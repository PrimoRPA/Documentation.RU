# Поиск в диапазоне

Элемент ищет заданные значения в диапазоне ячеек ODF-таблицы. Путь до файла указывается в контейнере «Таблица ODF».

![Элемент «Поиск в диапазоне»](../../../../resources/activities/extra/odf-oxml/table/odf-lookup-range.png)


## Свойства

Символ `*` указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Диапазон** *[String]* — диапазон считывания ячеек. Если не указан, будет прочитан выделенный диапазон. Если указан символ `"*"`, будет прочитан весь лист.
1. **Значение\*** *[String]* — искомое значение.
1. **Страница** *[String]* — наименование страницы.
1. **Индекс страницы** *[Int32]* — порядковый номер страницы.
1. **Переменная** *[String]* — переменная для хранения результатов поиска.
 