# Приложение 1 - Стадии развертывания робота

Таблица 1. - Стадии развертывания робота на машине робота.

| <p>№</p><p>п/п</p>    | Код | Наименование                                                                                                                                                  | Примечание |
| --------------------- | --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- |
| 1.                    | 1   | Процесс запущен                                                                                                                                               |            |
| 2.                    | 10  | Скачивание дистрибутива робота с Оркестратора                                                                                                                 |            |
| 3.                    | 11  | Сохранение дистрибутива робота на машине робота                                                                                                               |            |
| 4.                    | 20  | Уничтожение процесса робота, если такой есть запущенный                                                                                                       |            |
| 5.                    | 30  | Распаковка дистрибутива робота                                                                                                                                |            |
| 6.                    | 40  | Импорт SSL-сертификата из дистрибутива робота в хранилище сертификатов ОС                                                                                     |            |
| 7.                    | 50  | Трансформация конфигурации робота под параметры развертывания                                                                                                      |            |
| 8.                    | 60  | Резервирование url+port для https-службы робота с port, переданным Оркестратором                                                                              |            |
| 9.                    | 61  | Если url зарезервирован для port, резервирование происходит с первым свободным после переданного port. Фактический port возвращается в событии в Оркестратора |            |
| 10.                   | 70  | Привязка SSL-сертификата к службе робота                                                                                                                      |            |

&#x20;

Соответствующие события Оркестратора (см. [ЗАМЕНИТЬ ССЫЛКУ Приложение 3](https://docs.primo-rpa.ru/primo-rpa/orchestrator/appendix/appendix3)) получаются как Код + 7000.

Стадии проходят последовательно, в порядке возрастания кода. При отображении стадий в UI иногда последовательность может нарушаться – более поздние стадии отображаются раньше. Некоторые стадии могут отсутствовать.