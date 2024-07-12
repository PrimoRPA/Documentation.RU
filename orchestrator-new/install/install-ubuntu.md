# Установка Primo RPA Orchestrator на Ubuntu Server 22.04
(при наличии интернета на сервере)

- **Шаг 1**:   
Обновите список пакетов и систему
```
sudo apt update
sudo apt upgrade
sudo reboot
```
Перейдите в режим root:  
`sudo -i` (введите пароль) - далее все действия будут выполняться под пользователем root

- **Шаг 2**:  
Скачайте и установите соответствующую вашей операционной системе версию **PostgreSQL**, используя [инструкцию](https://www.postgresql.org/download/). 

Разрешите подключение к PostgreSQL по сети:  
`vim /etc/postgresql/13/main/postgresql.conf`

Найдите строку:
`listen_addresses = 'localhost'`  
и внесите следующие изменения:   
`listen_addresses = '*'`  

Далее откройте файл pg_hba.conf:  
`vim /etc/postgresql/13/main/pg_hba.conf`
Найдите строки и внесите туда следующие изменения:


