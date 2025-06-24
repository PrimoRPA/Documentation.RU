import { Callout } from 'nextra/components'

# Установка сервера AI

Подключитесь к серверу по SSH под пользователем с правами `root`.

## Установка Docker

_Установите Docker — он потребуется для запуска контейнеров. Подробная инструкция доступна по [ссылке](https://docs.primo-rpa.ru/ru/primo-ai/installing/linux/installing-docker)._

<Callout type="warning" emoji="⚠️">
 Сервер использует подсеть `server_ai`, которая создается автоматически при первом запуске финальной команды данной статьи.
</Callout>


## Загрузка образов

```
docker load -i /srv/samba/shared/install/distr/ai-server-api.tar
```
```
docker load -i /srv/samba/shared/install/distr/ai-server-auth.tar
```
```
docker load -i /srv/samba/shared/install/distr/ai-server-inference.tar
```
```
docker load -i /srv/samba/shared/install/distr/ai-server-logs.tar
```
```
docker load -i /srv/samba/shared/install/distr/ai-server-ui.tar
```

При необходимости для _среды_ разработки или тестирования загрузите сторонние зависимости:
```
docker load -i /srv/samba/shared/install/distr/postgres.tar
```
```
docker load -i /srv/samba/shared/install/distr/rabbitmq.tar
```

## Размещение файлов

1. _Создайте_ папку `/app/Primo.AI/Api` и дочерние каталоги:
   ```
   sudo mkdir -p /app/Primo.AI/Api/volumes/conf/Api/ /app/Primo.AI/Api/volumes/conf/Auth/ /app/Primo.AI/Api/volumes/conf/Logs/ /app/Primo.AI/Api/volumes/conf/MachineInfo/ /app/Primo.AI/Api/volumes/conf/Inference/ /app/Primo.AI/Api/volumes/nginx/ /app/Primo.AI/Api/volumes/Api_Models/ /app/Primo.AI/Api/volumes/Api_ContextFiles/ /app/Primo.AI/Api/volumes/Logs/
   ```
1. _Разместите_ окружение сервера в папке `/app/Primo.AI/Api`:
   ```
   sudo cp /srv/samba/shared/install/docker/server/docker-compose.yaml /app/Primo.AI/Api/
   ```
   ```
   sudo cp -r /srv/samba/shared/install/docker/server/volumes/* /app/Primo.AI/Api/volumes/
   ```
   ```
   sudo unzip /srv/samba/shared/install/docker/server/env.zip -d /app/Primo.AI/Api/
   ```
   
   _Если вы используете нестандартные параметры для базы данных, RabbitMQ или временной зоны, укажите их в `.env`-файле_:

   ```bash
   sudo nano /app/Primo.AI/Api/.env
   ```
1. _Разместите_ файлы моделей **Умного OCR**:
   ```
   sudo cp -r /srv/samba/shared/install/data/models/SmartOCR/* /app/Primo.AI/Api/volumes/Api_Models/
   ```
1. _Добавьте_ файлы моделей **AI Текст**:

   **Модели AI Текст**:
   | Имя модели                          | LLM-ядро         | Мультимодальность | Имя файла                            |
   |-------------------------------------|------------------|-------------------|--------------------------------------|
   | base-LLM-01 (Vllm, 8B)              | vLLM             | Нет               | e255188e-d9f6-41d3-b170-0c25bc0bd02f |
   | base-LLM-02 (Ollama, 8B)            | Ollama           | Нет               | ddc02d8d-0117-4c67-acb3-2dd0549d2985 |
   | base-LLM-03 (Vllm, 7B)              | vLLM             | Нет               | b1bf77a1-ca4e-4088-942c-8ec83086611b |
   | base-LLM-04 (Vllm, multimodal, 7B)  | vLLM             | Да                | ebe98258-1c21-4d19-af56-cf39f7e3883d |
   | base-LLM-05 (llama-cpp-python, 27B) | llama-cpp-python | Нет               | f55425a0-87c8-4d9e-a4cd-abc56f96ab1e |
   | base-LLM-06 (Vllm, multimodal, 7B)  | vLLM             | Да                | 78e57e23-363c-4b1e-b4e2-36fb31da5b48 |
   | base-LLM-07 (Vllm, 8B)              | vLLM             | Нет               | e161b94d-3272-4afa-9aad-d191b61c67d3 |

   _Файлы моделей объёмные — можно скопировать только отдельные (укажите вместо `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx` имя файла модели из таблицы выше)._
   ```
   sudo cp /srv/samba/shared/install/data/models/NLP/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /app/Primo.AI/Api/volumes/Api_Models/
   ```
   Либо, если места достаточно, скопируйте все модели:
   ```
   sudo cp /srv/samba/shared/install/data/models/NLP/* /app/Primo.AI/Api/volumes/Api_Models/
   ```
   _Если скопировать только часть моделей, при попытке использовать отсутствующие — система покажет ошибку._

1. _Разместите_ стандартный контекст NLP-запросов:
   ```
   sudo cp -r /srv/samba/shared/install/data/context/* /app/Primo.AI/Api/volumes/Api_ContextFiles/
   ```
   Должна получиться следующая иерархия папок для соответствия стандартному `docker-compose.yaml`:
   ```
   /app/Primo.AI/Api/
   ├── .env
   ├── docker-compose.yaml
   └── volumes
       ├── conf
       │   └── Api
       │       ├── appsettings.json
       │       └── appsettings.ProdLinux.json
       │   └── Logs
       │       ├── appsettings.json
       │       └── appsettings.ProdLinux.json
       │   └── Inference
       │       ├── appsettings.json
       │       └── appsettings.ProdLinux.json
       │   └── Auth
       │       ├── appsettings.json
       │       └── appsettings.ProdLinux.json
       │   └── nginx
       │       └── nginx.conf
       ├── Api_Models
       │   ├─── cf7d9f7f-ab96-4c15-873e-82c6aad7f9a4
       │   ├─── 3901af0a-8c50-4b76-b96f-481cae5e4a35
       │   ├─── ...
       │   └─── e161b94d-3272-4afa-9aad-d191b61c67d3
       ├── Api_ContextFiles
       │   ├─── 13fb0ff5-3f31-44e1-9c99-e24276380a3f
       │   ├─── e41cc59b-059f-4471-8d09-328aab8ed60f
       │   ├─── a9d109d6-0125-42f9-b44e-2052a0c4e164
       │   └─── d24b857c-6c21-4d5f-990f-52d6235c33dd
       └── Logs
   ```
## Редактируем конфигурационные файлы

### Конфигурационный файл Api

1. _Откройте_ в редакторе конфигурационный файл:
   ```
   sudo nano /app/Primo.AI/Api/volumes/conf/Api/appsettings.ProdLinux.json
   ```
1. _Укажите_ адрес портала AI Server в **Security > EnabledOrigins**:
   ```
   "Security": {
    ...
    "EnabledOrigins": [
      "https://192.168.0.4:44392",
      "https://ai-server-portal:44392"
    ],
    ...
   }
   ```

### Конфигурационный файл Api.Auth

1. _Откройте_ в редакторе конфигурационный файл:
   ```
   sudo nano /app/Primo.AI/Api/volumes/conf/Auth/appsettings.ProdLinux.json
   ```
1. _Укажите_ адрес портала AI Server в **Security > EnabledOrigins**:
   ```
   "Security": {
    ...
    "EnabledOrigins": [
      "https://192.168.0.4:44392",
      "https://ai-server-portal:44392"
    ],
    ...
   }
   ```

### Конфигурационный файл Api.Inference

1. _Откройте_ в редакторе конфигурационный файл:
   ```
   sudo nano /app/Primo.AI/Api/volumes/conf/Inference/appsettings.ProdLinux.json
   ```

1. _Укажите_ адрес портала AI Server в **Security > EnabledOrigins**:
   ```
   "Security": {
    ...
    "EnabledOrigins": [
      "https://192.168.0.4:44392",
      "https://ai-server-portal:44392"
    ],
    ...
   }
   ```

### Конфигурационный файл Api.Logs

1. _Откройте_ в редакторе конфигурационный файл:
   ```
   sudo nano /app/Primo.AI/Api/volumes/conf/Logs/appsettings.ProdLinux.json
   ```
1. _Укажите_ адрес портала AI Server в **Security > EnabledOrigins**:
   ```
   "Security": {
    ...
    "EnabledOrigins": [
      "https://192.168.0.4:44392",
      "https://ai-server-portal:44392"
    ],
    ...
   }
   ```

### Конфигурационный файл nginx

При необходимости укажите в конфигурационном файле количество рабочих процессов, максимальное число соединений и другие параметры.

_Откройте_ в редакторе конфигурационный файл:
   ```
   sudo nano /app/Primo.AI/Api/volumes/nginx/nginx.conf
   ```

## Разрешения

_Настройте права на запись для томов контейнеров_:
   ```
   sudo chmod -R 777 /app/Primo.AI/Api/volumes/
   ```


## Запуск контейнеров

_Запустите контейнеры с помощью `docker-compose`. Это развернёт сервисы в фоновом режиме:_
   ```
   docker compose -f /app/Primo.AI/Api/docker-compose.yaml up -d
   ```
