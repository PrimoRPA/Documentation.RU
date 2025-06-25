# Удалить из Credentials

![](../../../resources/activities/basic/crypto/delete-credentials.png)

Компонент, производящий удаление учетных данных из системного хранилища учетных данных

| Свойство | Тип           | Описание                           |
| -------- | ------------- | ---------------------------------- |
| Ключ\*   | System.String | Ключ для поиска записанных данных  |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Cryptography.CryptoApp.CredentialsDelete(wf, "Key");
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Cryptography.CryptoApp.CredentialsDelete(wf, "Key")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Cryptography.CryptoApp.CredentialsDelete(wf, "Key");
```
{% endtab %}
{% endtabs %}
