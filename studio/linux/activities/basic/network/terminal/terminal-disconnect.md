# Отсоединиться от сервера

![](../../../../resources/activities/basic/network/terminal/image-100-1-1-1-1-1-1-1-2-278.png)

![](../../../../resources/activities/basic/network/terminal/image-388.png)

Компонент, выполняющий отсоединение от терминального сервера

| Свойство   | Тип                    | Описание                                             |
| ---------- | ---------------------- | ---------------------------------------------------- |
| Переменная | Renci.SshNet.SshClient | Переменная, содержащая ссылку на подключенный сервер |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Network.TServerApp app = LTools.Network.TServerApp.Init(wf, "address", 22, "login", "pass", 10000);
app.Disconnect();
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Network.TServerApp.Init(wf, "address", 22, "login", "pass", 10000)
app.Disconnect()
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Network.TServerApp.Init(wf, "address", 22, "login", "pass", 10000);
app.Disconnect();
```
{% endtab %}
{% endtabs %}
