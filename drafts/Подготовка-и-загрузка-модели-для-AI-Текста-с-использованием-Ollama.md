# Общая информация
Данная статья описывает подготовку к загрузке новой базовой модели для использования в AI Тексте с движком Ollama.  
>Поддерживаются модели в формате GGUF, упакованные в архив.  

Инструкция объясняет, как извлечь из хранилища Ollama файл модели, а также шаблон и параметры, которые затем можно указать в пользовательском интерфейсе.

## Подготовка: Извлечение модели Ollama
Чтобы извлечь модели из хранилища Ollama, выполните следующие шаги данного руководства.

Требования к устройству:
- Должен быть интернет
- Должен быть установлен `Docker`
- Должна быть установлена утилита `zip`

### 1. **Запустите Ollama**
```bash
docker run --name ollama_tmp -v ~/ollama_models:~/.ollama/models -d ollama/ollama:latest 
```
*Обратите внимание на инструкцию -v: маппинг тома нужен для того, чтобы файл модели был доступен на машине хоста.*

### 3. **Найдите путь к хранилищу Ollama**
Ollama хранит модели в определённой директории:
`~/.ollama/models`
Это соответствует папке `~/ollama_models` на машине-хосте.
Произведите листинг содержимого со списком моделей:
```bash
docker exec -it ollama_tmp ls -la ~/.ollama/models
```
Вывод:
```
root@abaaab9b1ab8:~/.ollama/models# ls -la
total 16
drwxr-xr-x 4 root root 4096 Jun 20 09:45 .
drwxr-xr-x 3 root root 4096 Jun 20 09:44 ..
drwxr-xr-x 2 root root 4096 Jun 20 09:46 blobs
drwxr-xr-x 3 root root 4096 Jun 20 09:46 manifests
```
Это соответствует директории на машине хосте `~/ollama_models`.

### 4. **Скачайте нужную модель**
```bash
docker exec -it ollama_tmp ollama pull llama3.1
```

### 5. **Найдите нужную модель**
Выведите список моделей:
```bash
ls -la ~/ollama_models/manifests/registry.ollama.ai/library/
```
Вывод: 
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
Вывод: 
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

В приведенном json нас интересуют следующие слои модели:
- шаблон модели: `application/vnd.ollama.image.template`. Хэш слоя в приведённом примере: `sha256:948af2743fc78a328dcb3b0f5a31b3d75f415840fdb699e8b1235978392ecf85`.

Слой может отсутствовать. 
- параметры модели: `application/vnd.ollama.image.params`. Хэш слоя в приведённом примере: `sha256:56bb8bd477a519ffa694fc449c2413c6f0e1d3b1c88fa7e3c9d88d3ae49d4dcb`.
- модель в формате GGUF: `application/vnd.ollama.image.model`. Хэш слоя в приведённом примере: `sha256:667b0c1932bc6ffc593ed1d03f895bf2dc8dc6df21db3042284a6f4416b06a29`.
### 3. **Извлеките шаблон модели**

Откройте искомый blob (укажите свой хэш):
```bash
cat ~/ollama_models/blobs/sha256:948af2743fc78a328dcb3b0f5a31b3d75f415840fdb699e8b1235978392ecf85
```
Скопируйте его содержимое в поле `Шаблон модели` при загрузке модели через интерфейс.

### 6. **Извлеките параметры модели**
Откройте искомый blob:
```bash
cat ~/ollama_models/blobs/sha256:56bb8bd477a519ffa694fc449c2413c6f0e1d3b1c88fa7e3c9d88d3ae49d4dcb
```
Такие параметры, как `Размер контекстного окна` и `Температура`, AI Server позволяет указать через пользовательский интерфейс при конфигурировании модели в разделе `Машины` и при `Тестировании` соответственно.
Скопируйте параметры, такие как stop-токены, в поле `Шаблон модели` при загрузке модели через интерфейс.

### 7. **Извлеките файл GGUF**
Скопируйте искомый blob:
```bash
cp ~/ollama_models/blobs/sha256:667b0c1932bc6ffc593ed1d03f895bf2dc8dc6df21db3042284a6f4416b06a29 ~/llama3.1.gguf
```

### 8. **Проверьте файл**
Убедитесь, что это действительно GGUF:
   ```bash
   file ~/Downloads/model.gguf
   ```
Должно быть что-то вроде:
   ```
   model.gguf: GGUF neural network model data (little-endian)
   ```
или
   ```
   /home/ubuntu/llama3.1.gguf: data
   ```

### 9. **Подготовьте архив с моделью**
Запакуйте модель утилитой zip:
```bash
zip -0 new-model.zip /home/ubuntu/llama3.1.gguf
```

### 10. **Загрузите модель в AI Server**
- Откройте `Настройки` > `Шаблоны моделей`
- Нажмите "Добавить шаблон модели"
- Выберите файл `new-model.zip`
- Укажите `Название`
- Укажите `Тип проекта`: `AI Текст`
- Укажите `Движок`: `Ollama`
- Укажите `Шаблон`: см. п.3
- Укажите `Параметры`: см. п.4
- Нажмите "Сохранить" и дождитесь завершения загрузки

### 11. **Произведите очистку**
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