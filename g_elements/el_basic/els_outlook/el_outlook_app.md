# Приложение Outlook

![](<../../../.gitbook/assets/image (190).png>)

Элемент предоставляет возможность подключиться к приложению Outlook. Является контейнером по отношению к другим элементам из группы *Outlook*.

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

***Outlook:*** 

1. **Имя профиля** *[String]* - имя почтового [профиля](https://support.microsoft.com/ru-ru/office/%D0%BE%D0%B1%D0%B7%D0%BE%D1%80-%D0%BA%D0%BE%D0%BD%D1%84%D0%B8%D0%B3%D1%83%D1%80%D0%B0%D1%86%D0%B8%D0%B9-%D1%8D%D0%BB%D0%B5%D0%BA%D1%82%D1%80%D0%BE%D0%BD%D0%BD%D0%BE%D0%B9-%D0%BF%D0%BE%D1%87%D1%82%D1%8B-microsoft-outlook-9073a8ac-c3d6-421d-b5b9-fcedff7642fc). По умолчанию - `"Outlook"`. Это стандартное название первого профиля, который создается программой Outlook автоматически при первом запуске и затем используется по умолчанию.\
   Если вы хотите проверить количество почтовых профилей и их названия:
   * В поле поиска Windows введите «Панель управления» и выберите ее.
   * На панели управления найдите значок **Почта** и выберите его. Значок **Почта** не появится, если вы не запускали программу Outlook хотя бы раз.
   * Откроется диалоговое окно **Настройка почты - Outlook**.
   * Выберите команду **Показать**.

    ![](<../../../.gitbook/assets1/win-outlook-show.png>)
   
1. **Пароль** *[String]* - пароль профиля при его наличии. Чаще всего отсутствует.
1. **Защищенный пароль** *[[SecureString](https://learn.microsoft.com/ru-ru/dotnet/api/system.security.securestring?view=netcore-2.0)]* - зашифрованный пароль профиля, не хранится в открытом виде. Получить его можно, например, из программы **Диспетчер учетных данных** (Credential Manager).

***Вывод:***

* **Переменная** *[LTools.Office.OutlookInst]* - переменная для хранения ссылки на установленное подключение. Заполняется, если установленное соединение необходимо переиспользовать в дальнейшем.


### Решение проблем

#### Изменение профиля по умолчанию
В случае, когда у вас несколько почтовых профилей Outlook, и вы хотите изменить профиль по умолчанию в свойствах элемента - ***убедитесь, что Outlook не запущен***. Это связано с тем, что одновременно может выполняться только один процесс Outlook, который использует только один профиль и поддерживает только один сеанс MAPI. Когда пользователь запускает Outlook во второй раз, этот экземпляр Outlook запускается в том же процессе и использует тот же профиль.

Если Outlook уже запущен, изменение значений в свойствах элемента **Имя профиля** и **Пароль** не приведет к созданию нового сеанса Outlook или к изменению текущего профиля на другой.


### Демонстрационный проект
На странице Learning доступен RPA-проект, демонстрирующий работу основных элементов Outlook:
1. Скачайте архив со всеми обучающими материалами по ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip).
2. Распакуйте архив и откройте в Студии проект StudioActivities.
3. Выберите процесс `StudioActivities/Ru/Приложение Outlook/Основное.ltw` для просмотра.


## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.OutlookApp app = LTools.Office.OutlookApp.Init(wf, "Outlook", "password");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.OutlookApp.Init(wf, "Outlook", "password")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.OutlookApp.Init(wf, "Outlook", "password");
```
{% endtab %}
{% endtabs %}