# Вставка изображения

![](../../../../resources/activities/basic/myoffice/text/image-559.png)

Компонент, производящий вставку изображения в документ Текст.

| Свойство    | Тип     | Описание                                                                                      |
| ----------- | ------- | --------------------------------------------------------------------------------------------- |
| Закладка    | String  | Имя закладки, определяющей начало записи. Если не указано, запись производится в конец текста |
| Изображение | byte\[] | Вставляемое изображение                                                                       |
| Ширина      | float   | Ширина изображения                                                                            |
| Высота      | float   | Высота изображения                                                                            |

{% tabs %}
{% tab title="C#" %}
```csharp
app.InsertPicture(pic, "bookmark", 200, 100);
```
{% endtab %}

{% tab title="Python" %}
```python
app.InsertPicture(pic, "bookmark", 200, 100)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.InsertPicture(pic, "bookmark", 200, 100);
```
{% endtab %}
{% endtabs %}
