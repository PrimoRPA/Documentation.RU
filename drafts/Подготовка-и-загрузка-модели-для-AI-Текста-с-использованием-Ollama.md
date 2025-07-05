# Общая информация
Данная статья описывает процесс подготовки к загрузке новой базовой модели для использования в AI Тексте с движком Ollama.

<Callout type="info"> Поддерживаются модели в формате GGUF, упакованные в архив. </Callout>

Вы узнаете, как извлечь файл модели из хранилища Ollama, а также получить шаблон и параметры, которые впоследствии можно указать в пользовательском интерфейсе.


## Подготовка: Извлечение модели Ollama
Чтобы извлечь модели из хранилища Ollama, выполните шаги, описанные в данном руководстве.

Перед началом убедитесь, что:
- Устройство подключено к интернету
- Установлен `Docker`
- Установлена утилита `zip`

### 1. Запустите движок Ollama

Для этого выполните команду:
```bash
docker run --name ollama_tmp -v ~/ollama_models:~/.ollama/models -d ollama/ollama:latest 
```
*Параметр `-v` используется для маппинга тома: он обеспечивает доступ к файлам модели на вашей машине-хосте.*

### 2. Найдите путь к хранилищу Ollama

Ollama хранит модели в определённой директории: `~/.ollama/models`. Эта директория соответствует локальной папке соответствует локальной папке `~/ollama_models` на машине-хосте.

Выполните команду, чтобы просмотреть содержимое директории с моделями внутри контейнера:

```bash
docker exec -it ollama_tmp ls -la ~/.ollama/models
```
Пример вывода:
```
root@abaaab9b1ab8:~/.ollama/models# ls -la
total 16
drwxr-xr-x 4 root root 4096 Jun 20 09:45 .
drwxr-xr-x 3 root root 4096 Jun 20 09:44 ..
drwxr-xr-x 2 root root 4096 Jun 20 09:46 blobs
drwxr-xr-x 3 root root 4096 Jun 20 09:46 manifests
```

### 3. Скачайте нужную модель
```bash
docker exec -it ollama_tmp ollama pull llama3.1
```

### 4. Найдите нужную модель
Выведите список моделей:
```bash
ls -la ~/ollama_models/manifests/registry.ollama.ai/library/
```
Пример вывода: 
```
total 12
drwxr-xr-x 3 root root 4096 Jun 20 09:46 .
drwxr-xr-x 3 root root 4096 Jun 20 09:46 ..
drwxr-xr-x 2 root root 4096 Jun 20 09:46 llama3.1
```
Получите хэш blob'а нужной модели: 
```bash
cat  ~/ollama_models/manifests/registry.ollama.ai/library/llama3.1/latest
```
Хэш из этого файла указывает на конкретный blob, в котором хранится модель.

Пример вывода: 
```json
{
    "config": {
        "digest": "sha256:455f34728c9b5dd3376378bfb809ee166c145b0b4c1f1a6feca069055066ef9a",
        "mediaType": "application/vnd.docker.container.image.v1+json",
        "size": 487
    },
    "layers": [
        {
            "digest": "sha256:667b0c1932bc6ffc593ed1d03f895bf2dc8dc6df21db3042284a6f4416b06a29",
            "mediaType": "application/vnd.ollama.image.model",
            "size": 4920738944
        },
        {
            "digest": "sha256:948af2743fc78a328dcb3b0f5a31b3d75f415840fdb699e8b1235978392ecf85",
            "mediaType": "application/vnd.ollama.image.template",
            "size": 1481
        },
        {
            "digest": "sha256:0ba8f0e314b4264dfd19df045cde9d4c394a52474bf92ed6a3de22a4ca31a177",
            "mediaType": "application/vnd.ollama.image.license",
            "size": 12320
        },
        {
            "digest": "sha256:56bb8bd477a519ffa694fc449c2413c6f0e1d3b1c88fa7e3c9d88d3ae49d4dcb",
            "mediaType": "application/vnd.ollama.image.params",
            "size": 96
        }
    ],
    "mediaType": "application/vnd.docker.distribution.manifest.v2+json",
    "schemaVersion": 2
}
```

### 5. Изучите содержимое
После выполнения команды `cat`, вы получите JSON-структуру.

Нас интересуют следующие слои:
- шаблон модели: `application/vnd.ollama.image.template`.   
  Хэш слоя из примера: `sha256:948af2743fc78a328dcb3b0f5a31b3d75f415840fdb699e8b1235978392ecf85`. 
 _Этот слой может отсутствовать_. 

- параметры модели: `application/vnd.ollama.image.params`.   
  Хэш слоя из примера:  `sha256:56bb8bd477a519ffa694fc449c2413c6f0e1d3b1c88fa7e3c9d88d3ae49d4dcb`.

- модель в формате GGUF: `application/vnd.ollama.image.model`.   
  Хэш слоя из примера:  `sha256:667b0c1932bc6ffc593ed1d03f895bf2dc8dc6df21db3042284a6f4416b06a29`.

### 6. Извлеките шаблон модели

Теперь, зная хэш слоя с параметрами модели, откройте соответствующий blob-файл:
```bash
cat ~/ollama_models/blobs/sha256:948af2743fc78a328dcb3b0f5a31b3d75f415840fdb699e8b1235978392ecf85
```
Скопируйте его содержимое в поле `Шаблон модели` при загрузке модели через интерфейс.

### 7. Извлеките параметры модели
Снова откройте искомый blob:
```bash
cat ~/ollama_models/blobs/sha256:56bb8bd477a519ffa694fc449c2413c6f0e1d3b1c88fa7e3c9d88d3ae49d4dcb
```

Такие параметры, как `Размер контекстного окна` и `Температура`, AI Server позволяет указать через пользовательский интерфейс при конфигурировании модели в разделе `Машины` и при `Тестировании` соответственно.

Скопируйте параметры, такие как stop-токены, в поле Шаблон модели при загрузке модели через интерфейс.


### 8. Извлеките файл GGUF
Скопируйте искомый blob:
```bash
cp ~/ollama_models/blobs/sha256:667b0c1932bc6ffc593ed1d03f895bf2dc8dc6df21db3042284a6f4416b06a29 ~/llama3.1.gguf
```

### 9. Проверьте файл
После извлечения модели проверьте её формат. Убедитесь, что это действительно GGUF:
   ```bash
   file ~/Downloads/model.gguf
   ```
В случае корректного файла, команда должна вернуть следующий (или аналогичный) результат:
   ```
   model.gguf: GGUF neural network model data (little-endian)
   ```
В отдельных случаях вывод может быть менее информативным:
   ```
   /home/ubuntu/llama3.1.gguf: data
   ```

### 10. Подготовьте архив с моделью
Для загрузки модели в интерфейс AI Server, она должна быть упакована в .zip-архив. Для этого выполните команду:
```bash
zip -0 new-model.zip /home/ubuntu/llama3.1.gguf
```

### 11. Загрузите модель в AI Server
<ol type="a">
 <li>Откройте `Настройки` > `Шаблоны моделей`</li>
 <li>Нажмите "Добавить шаблон модели"</li>
 <li>Выберите файл `new-model.zip`</li>
 <li>Укажите `Название`</li>
 <li>Укажите `Тип проекта`: `AI Текст`</li>
 <li>Укажите `Движок`: `Ollama`</li>
 <li>Укажите `Шаблон`: см. п.3</li>
 <li>Укажите `Параметры`: см. п.4</li>
 <li>Нажмите "Сохранить" и дождитесь завершения загрузки</li>
</ol>


### 12. Произведите очистку

- Остановите и удалите контейнер: 
```bash
docker stop ollama_tmp && docker rm ollama_tmp
```
- Удалите том контейнера:
```bash
rm -r ~/ollama_models
```
- Удалите файл модели:
```bash
rm /home/ubuntu/llama3.1.gguf
```