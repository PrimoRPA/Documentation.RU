# Использование кириллицы

В некоторых случаях при использовании кириллицы в названиях файлов ZIP-архива проекта могут возникать проблемы.
В этом случае кодировку нужно задать принудительно, используя параметр **ProjectZipEncoding** в конфигурационном файле Агента на машине робота:

![](../../../orchestrator-new/resources/fine-tuning/encoding-cyrillic.PNG)

При `ProjectZipEncoding = null` кодировка определится автоматически на основе окружения.

Список значений для данного параметра можно найти в [статье](https://learn.microsoft.com/en-us/dotnet/api/system.text.encoding.getencodings?view=net-8.0).
