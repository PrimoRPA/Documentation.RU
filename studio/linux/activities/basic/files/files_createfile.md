# Создать файл

![](../../resources/basic/files/image-(100)-(1)-(1)-(1)-(1)-(1)-(1)-(1)-(2)-(90).png)

![](../../resources/basic/files/image-(15).png)

Компонент, создающий новый файл.

| Свойство | Тип    | Описание                                       |
| -------- | ------ | ---------------------------------------------- |
| Путь\*   | String | Путь к создаваемому файлу (c:\folder\file.txt) |

{% tabs %}
{% tab title="C#" %}
```csharp
System.IO.File.Create(@"C:\text.txt");
```
{% endtab %}

{% tab title="Python" %}
```python
System.IO.File.Create("C:\\text.txt")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.System.IO.File.Create("C:\\text.txt");
```
{% endtab %}
{% endtabs %}
