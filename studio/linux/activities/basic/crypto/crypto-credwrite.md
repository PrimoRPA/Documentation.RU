# Записать в Credentials

![](../../../resources/activities/basic/crypto/set-credentials.png)

Компонент, производящий запись учетных данных в системное хранилище учетных данных

| Свойство            | Тип     | Описание                                                  |
| ------------------- | ------- | --------------------------------------------------------- |
| Ключ\*              | System.String  | Ключ для поиска записанных данных                  |
| Имя пользователя\*  | System.String  | Имя пользователя                                   |
| Пароль\*            | System.String  | Пароль                                             |
| Защищенный пароль   | System.Security.SecureString  | Защищенный пароль                   |
| Защищать данные     | Boolean | Признак использования дополнительной защиты данных. Доступно только в Windows |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Cryptography.CryptoApp.CredentialsSet(wf, "Key", true, "login", "password");
```
{% endtab %}

{% tab title="Second Tab" %}
```python
LTools.Cryptography.CryptoApp.CredentialsSet(wf, "Key", True, "login", "password")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Cryptography.CryptoApp.CredentialsSet(wf, "Key", true, "login", "password");
```
{% endtab %}
{% endtabs %}
