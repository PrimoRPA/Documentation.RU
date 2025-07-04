---
Description: Process link
---

# Ссылка на процесс

![](../../../resources/activities/basic/logic/logic-link-base.png)

**Назначение**: выполняет указанный подпроцесс. Путь до его файла задается либо в строке на панели элемента, либо в свойстве «Путь к процессу».

На панели элемента также находятся кнопки:

1. **Открыть** ![](../../../resources/activities/basic/logic/open-link-process2.png) - автоматически открывает в проекте вкладку с указанным подпроцессом.
2. **Аргументы** ![](../../../resources/activities/basic/logic/args-link-process2.png) - вызывает окно с аргументами подпроцесса. Пример:

   ![](../../../resources/activities/basic/logic/logic-link-arguments-panel.png)

   Для каждого аргумента возможно создать переменную (или аргумент) и указать ее в столбце **Назначение**.\
   В окне поддерживается сочетание клавиш:
   * `Ctrl` + `K` - для создания переменной. Переменная создается для выбранного аргумента в соответствии с его типом данных. Добавленная переменная отобразится в столбце **Назначение**, а также на панели переменных активного процесса.
   * `Ctrl` + `Alt` + `K` - для создания аргумента. Тип данных назначается в соответствии с выбранным аргументом подпроцесса.

## Свойства

Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

***Процесс:***     
1. **Путь к процессу\*** *[String]* - Путь к файлу подпроцесса. Пример: `"./Main.ltw"`
1. **Маппинг\*** *[[LTools.Common.Model. VariablesMapping](../els\_data/datatypes/variablesmapping.md)]* - Маппинг аргументов подпроцесса
1. **Кешировать** *[Boolean]* - Определите, нужно ли кешировать подпроцесс
***Песочница:***    
1. **Запуск в песочнице** *[Boolean]* - Нужно ли запускать процесс в Песочнице Windows
1. **Закрывать** *[Boolean]* - Нужно ли закрывать Песочницу по завершении. По умолчанию закрывается
1. **Таймаут старта\*** *[Int32]* - Таймаут запуска Песочницы в миллисекундах. По умолчанию `60000`
1. **Таймаут завершения\*** *[Int32]* - Таймаут завершения работы робота в миллисекундах (0 - бесконечно). По умолчанию `0`
1. **Параллельно** *[Boolean]* - Нужно ли запускать Песочницу параллельно с основным процессом


### Песочница

![](../../../resources/activities/basic/logic/image-9.png)

[«Песочница» (SandBox)](https://learn.microsoft.com/ru-ru/windows/security/application-security/application-isolation/windows-sandbox/windows-sandbox-overview) - инструмент Windows 10, 11 для безопасного запуска приложений в изолированной виртуальной среде. Программы, установленные и запущенные внутри Песочницы, изолированы от остальной системы и работают независимо от главного компьютера. Песочница является временной. При ее закрытии все находящееся в ней программное обеспечение, все файлы и данные о состоянии удаляются. При каждом открытии приложения вы получаете новый экземпляр Песочницы.

**Установка песочницы:**

1. Убедитесь, что на вашем компьютере используется Windows 10 Pro или Windows 10 Корпоративная с версией сборки 18305 или Windows 11.
2. Виртуализация на компьютере:
   * Если вы используете физический компьютер, убедитесь, что возможности виртуализации включены в BIOS.
   * Если вы используете виртуальную машину, запустите эту команду PowerShell, чтобы включить вложенную виртуализацию:
     ```
     Set-VMProcessor -VMName <VMName> -ExposeVirtualizationExtensions $true
     ```
3. В строке поиска на панели задач введите **Включение или отключение компонентов Windows**, чтобы получить доступ к инструменту дополнительных компонентов Windows. Выберите **Песочницу Windows,** а затем нажмите **ОК.** Перезапустите компьютер при появлении соответствующего запроса.
   * Если вариант **Песочница Windows** недоступен, то компьютер не соответствует требованиям для запуска Песочницы. Если вы считаете, что это не так, просмотрите список [предварительных требований](https://learn.microsoft.com/ru-ru/windows/security/application-security/application-isolation/windows-sandbox/windows-sandbox-overview#prerequisites), а также шаги 1 и 2.

**Работа с Песочницей**

Для запуска процесса в Песочнице необходимо:

* Установить флаг **Запуск в песочнице** в свойствах элемента:

![](../../../resources/activities/basic/logic/logic-link-sanbox-property-panel.png)

:bangbang:***Основной и вспомогательный робот могут обмениваться только простыми данными (String, [Double](https://learn.microsoft.com/ru-ru/dotnet/api/system.double?view=net-5.0&viewFallbackFrom=windowsdesktop-3.0), [DateTime](https://learn.microsoft.com/ru-ru/dotnet/api/system.datetime?view=net-5.0), Boolean и т.д.) либо коллекциями простых данных (List\<String>, List\<DateTime> и т.д.)***

* Чтобы Песочница закрывалась по завершении работы процесса, используйте флаг **Закрывать**.
* Свойство **Таймаут старта** - это количество миллисекунд, которое нужно ожидать до старта дополнительного робота.
* Свойство **Таймаут завершения** - это количество миллисекунд, которое нужно ожидать до завершения работы дополнительного робота (в не-параллельном режиме). Значение `0` - ожидать бесконечно.
* Робота можно запускать параллельно с основным роботом (флаг **Параллельно**), но в этом случае аргументы, возвращенные дополнительным роботом, получены не будут.


## Обучающий пример

Перейдите по [ссылке](https://github.com/PrimoRPA/Learning/tree/master/StudioActivities/Ru/%D0%A3%D0%BF%D1%80%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5), чтобы скачать процессы, демонстрирующие работу элемента: `Ссылка на процесс.ltw` и `Ссылка на процесс 1.ltw` (подпроцесс). Чтобы ознакомиться с работой процессов, загрузите их в нужный проект и откройте в Студии.

## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
//Создаем аргументы
List<LTools.Workflow.Model.SequenceLinkArg> args = new List<LTools.Workflow.Model.SequenceLinkArg>();
args.Add(new LTools.Workflow.Model.SequenceLinkArg() { Name = "arg1", Value = "val1" });
//Вызываем процесс
args = LTools.Workflow.Elements.WFSequenceLink.CallWorkflow(wf, @"C:\Project\Process.ltw", args);
//Получаем аргументы
string ret = args.Where(it => it.Name == "arg1").FirstOrDefault().Value as string;
```
{% endtab %}

{% tab title="Python" %}
```python
#Создаем аргументы
args = List[LTools.Workflow.Model.SequenceLinkArg]()
args.Add(LTools.Workflow.Model.SequenceLinkArg("arg1", "val1"))
#Вызываем процесс
args = LTools.Workflow.Elements.WFSequenceLink.CallWorkflow(wf, "C:\\Project\\Process.ltw", args)
#Получаем аргументы
ret = ret[0].Value
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let host = new _lib.Microsoft.ClearScript.HostFunctions();
//Создаем аргументы
let args = host.newObj(_lib.System.Collections.Generic.List(_lib.LTools.Workflow.Model.SequenceLinkArg));
args.Add(new _lib.LTools.Workflow.Model.SequenceLinkArg("arg1", "val1"));
//Вызываем процесс
args = _lib.LTools.Workflow.Elements.WFSequenceLink.CallWorkflow(wf, "C:\\Project\\Process.ltw", args, false);
//Получаем аргументы
let ret = args[0];
```
{% endtab %}
{% endtabs %}
