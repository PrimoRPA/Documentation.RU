# Выполнить скрипт VB

![](../../resources/basic/prog/image-(100)-(1)-(1)-(1)-(1)-(1)-(1)-(1)-(1)-(57).png)

![](../../resources/basic/prog/missing.png)

Элемент выполняет файл сценария на языке VBScript.

### Свойства

Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство               | Тип           | Описание                                                                                                                                                     |
| ---------------------- | ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| _**Скрипт:**_          |               |                                                                                                                                                              |
| Файл\*                 | String        | Полный путь к файлу скрипта VB                                                                                                                               |
| Аргументы              | List\<string> | Входные аргументы сценария. Для указания аргументов можно использовать **Редактор коллекции** по кнопке ![](../../resources/basic/prog/java-editor-button.png) |
| Тайм-аут               | Int32         | Время ожидания выполнения сценария в миллисекундах. По умолчанию 0 - не используется                                                                         |
| Закрывать по тайм-ауту | Boolean       | Определяет, будет ли процесс закрыт по истечении указанного времени ожидания. По умолчанию параметр выключен                                                 |
| Ожидать вывода         | Boolean       | Определяет, нужно ли дожидаться результата работы процесса. По умолчанию включено                        |
| Поддержка Unicode      | Boolean       | Определяет возможность использования символов Unicode во входных и выходных данных. По умолчанию выключено                                                   |
| Скрыть окна            | Boolean       | Определяет, будут ли отображаться окна сообщений. По умолчанию параметр выключен, окна отображаются                                                          |
| _**Вывод:**_           |               |                                                                                                                                                              |
| Результат              | String        | Переменная, которая будет хранить результат выполнения скрипта                                                                                               |

### Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):
  
{% tabs %}
{% tab title="C#" %}
```csharp
//wf: [LTools.Common.Model.WorkflowData] ссылка на вызывающий алгоритм
//script - Файл: [String] Путь к файлу скрипта
//args - Аргументы: [List<string>] Аргументы скрипта
//close - Закрывать по тайм-ауту: Определяет, будет ли процесс закрыт по тайм-ауту
//wait - Ожидать вывода: Определяет, нужно ли дождаться результат работы процесса
//uc - Поддержка Unicode: Определяет возможность использования символов Unicode
//win - Скрыть окна: Определяет, будут ли отображаться окна сообщений
//to - Тайм-аут: [Int32] Тайм-аут скрипта
//string res = LTools.Workflow.PrimoApp.InvokeVB(wf, script, [args], [close], [wait], [uc], [win], [to]);
		
string res = LTools.Workflow.PrimoApp.InvokeVB(wf, ".\\message.vbs");
```
{% endtab %}

{% tab title="Python" %}
```python
#wf: [LTools.Common.Model.WorkflowData] ссылка на вызывающий алгоритм
#script - Файл: [String] Путь к файлу скрипта
#args - Аргументы: [List<string>] Аргументы скрипта
#close - Закрывать по тайм-ауту: Определяет, будет ли процесс закрыт по тайм-ауту
#wait - Ожидать вывода: Определяет, нужно ли дождаться результат работы процесса
#uc - Поддержка Unicode: Определяет возможность использования символов Unicode
#win - Скрыть окна: Определяет, будут ли отображаться окна сообщений
#to - Тайм-аут: [Int32] Тайм-аут скрипта
#res = LTools.Workflow.PrimoApp.InvokeVB(wf, script, [args], [close], [wait], [uc], [win], [to]) #String

res = LTools.Workflow.PrimoApp.InvokeVB(wf, ".\\message.vbs") #String
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
//wf: [LTools.Common.Model.WorkflowData] ссылка на вызывающий алгоритм
//script - Файл: [String] Путь к файлу скрипта
//args - Аргументы: [List<string>] Аргументы скрипта
//close - Закрывать по тайм-ауту: Определяет, будет ли процесс закрыт по тайм-ауту
//wait - Ожидать вывода: Определяет, нужно ли дождаться результат работы процесса
//uc - Поддержка Unicode: Определяет возможность использования символов Unicode
//win - Скрыть окна: Определяет, будут ли отображаться окна сообщений
//to - Тайм-аут: [Int32] Тайм-аут скрипта
//var res = _lib.LTools.Workflow.PrimoApp.InvokeVB(wf, script, [args], [close], [wait], [uc], [win], [to]); //String

var res = _lib.LTools.Workflow.PrimoApp.InvokeVB(wf, ".\\message.vbs"); //String
```
{% endtab %}
{% endtabs %}