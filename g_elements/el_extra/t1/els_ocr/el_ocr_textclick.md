# Клик текста мышью

![](<../../../../.gitbook/assets/click_ocrtext.png>)

Элемент ищет указанную строку и щелкает по ней мышью. При этом делает скриншот экрана.

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность его заполнения.

| Свойство             | Тип                   | Описание                                      |
| -------------------- | --------------------- | --------------------------------------------- |
| ***OCR:*** | |  |
| Переменная\* | Primo.T1.OCR.OCRInst | Переменная со ссылкой на ядро OCR. При использовании элемента внутри контейнера [Microsoft OCR](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/t1/els_ocr/el_ocr_microsoft) или [Tesseract OCR](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/t1/els_ocr/el_ocr_tesseract) свойство можно не заполнять |
| Искомый текст\* | String | Текст, который нужно кликнуть |
| Смещение X | Int32 | Процент смещения курсора по оси X относительно центра (горизонталь) |
| Смещение Y | Int32 | Процент смещения курсора по оси Y относительно центра (вертикаль) |
| ***Прочее:***  |  |  |
| Кнопка мыши\* | - | Кнопка мыши, которой необходимо произвести клик. По умолчанию это одиночный клик левой кнопкой - BUTTON_LEFT. <p>Доступные значения: 1) BUTTON_LEFT_DOUBLECLICK - двойной щелчок левой кнопкой; 2) BUTTON_RIGHT - правая кнопка; 3) BUTTON_MIDDLE - колесико </p> |
| Таймаут\*  | Int32 | Предельное время ожидания завершения процесса в миллисекундах. По умолчанию 10000 мс (10 секунд) |