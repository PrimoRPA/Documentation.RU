# Удалить файл/папку

![](../../../resources/activities/basic/files/image-100-1-1-1-1-1-1-1-2-184.png)

![](../../../resources/activities/basic/files/image-50.png)

Компонент, удаляющий файл.

| Свойство | Тип    | Описание                                     |
| -------- | ------ | -------------------------------------------- |
| Путь\*   | String | Путь к удаляемому файлу (c:\folder\file.txt) |

{% tabs %}
{% tab title="C#" %}
```csharp
System.IO.File.Delete(@"C:\text.txt");
System.IO.Directory.Delete(@"C:\Dir");
```
{% endtab %}

{% tab title="Python" %}
```python
System.IO.File.Delete("C:\\text.txt")
System.IO.Directory.Delete("C:\\Dir")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.System.IO.File.Delete("C:\\text.txt");
_lib.System.IO.Directory.Delete("C:\\Dir");
```
{% endtab %}
{% endtabs %}
