# Try-Catch

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (1) (46).png>)

![](<../../../.gitbook/assets/image (53).png>)

Элемент **Try-Catch** используется для обработки исключений, которые могут возникать при выполнении сценария. Try-Catch содержит стандартные блоки: Try, Catch и Finally.

#### 1. Блок Try
Try  — контейнер для одного или нескольких элементов, которые выполняются в первую очередь и потенциально могут вызвать исключение. 

Если в Try произошло исключение, то:
* данные об исключении запишутся в переменную, которую вы указали в свойстве **Исключение**;
* остальные элементы в блоке Try, идущие после исключения, выполняться не будут;
* робот перейдет к выполнению блока Catch для перехвата и обработки исключения в соответствии с вашим сценарием автоматизации.

#### 2. Блок Catch
Catch — контейнер для одного или нескольких элементов, которые выполняются только в случае возникновения исключения в блоке Try. Если в блоке Try не было исключения, то блок Catch выполняться не будет.

Если в Catch тоже возникло исключение, то оно не будет считаться обработанным — это означает, что выполнение процесса после элемента Try-Catch прекратится.

#### 3. Блок Finally

Finally — контейнер для одного или нескольких элементов, которые выполняются в последнюю очередь. Finally идет после блоков Try и Catch и выполняется в обязательном порядке.

Это означает, что Finally будет выполнен:
* если в блоке Try не возникло никаких исключений;
* если в Try возникло исключение, которое было перехвачено в блоке Catch;
* если в Catch тоже возникло исключение.

Если в Finally в свою очередь возникнет исключение, то выполнение процесса после Try-Catch прекратится.


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство            | Тип                                                                               | Описание                                    |
| ------------------- | --------------------------------------------------------------------------------- | ------------------------------------------- |
| Скриншот исключения | Boolean                                                                           | Создает скриншот при возникновении исключения в блоке **Try**. По умолчанию чекбокс выключен — скриншот не создается |
| Исключение          | [LTools.Common.Model.ExecutionExceptionInfo](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_logic/datatypes/executionexceptioninfo) | Переменная для сохранения данных об исключении |


## Пример использования

На странице [Learning](https://github.com/PrimoRPA/Learning) доступен RPA-проект, демонстрирующий работу с элементом:

1. [Скачайте](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip) архив со всеми обучающими материалами.
2. Распакуйте архив и откройте в Студии проект **StudioActivities**.
3. Выберите процесс `StudioActivities/Ru/Управление/Try-Catch Исключение.ltw` для просмотра.

## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code) находится в разработке.