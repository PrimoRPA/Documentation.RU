# Вставка строк

Элемент добавляет строки в в ODF-таблицу. Путь до файла указывается в контейнере «Таблица ODF».

Если в файле требуется сохранить изменения, то дополнительно используйте элемент «Сохранить документ».

![Элемент «Вставка строк»](<../../../../.gitbook/assets1/windows_items/odf-insert-row.png>)


## Свойства

Символ `*` указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Кол-во\*** *[Int32]* — количество вставляемых строк. По умолчанию `1`.
1. **Индекс** *[Int32]* — порядковый номер строки, после которой будут вставлены новые строки. Если индекс не указан, то вставка производится в конце листа.
1. **Страница** *[String]* — наименование страницы с таблицей. Пример: `"Лист1"`.
1. **Индекс страницы** *[Int32]* — порядковый номер страницы с таблицей. Пример: `0`.
