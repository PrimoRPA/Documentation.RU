# Установка браузерных расширений

Расширения возможно установить:
* вручную из Студии
* вручную из командной строки
* автоматически

## Ручная установка расширений из Студии

Инструкции см. в разделах:

{% content-ref url="chrome.md" %}
[chrome.md](chrome.md)
{% endcontent-ref %}

{% content-ref url="firefox.md" %}
[firefox.md](firefox.md)
{% endcontent-ref %}

{% content-ref url="edge.md" %}
[edge.md](edge.md)
{% endcontent-ref %}

{% content-ref url="yandex.md" %}
[yandex.md](yandex.md)
{% endcontent-ref %}

{% content-ref url="rdp.md" %}
[rdp.md](rdp.md)
{% endcontent-ref %} 

{% content-ref url="java.md" %}
[java.md](java.md)

## Установка из командной строки

Ниже приводятся способы установки расширений из командной строки.

```
LTools.WebBrowser.Native.exe install=<browser> lang=<language> mode=<mode>
```
Поддерживаемые аргументы:
* **browser** - тип браузера: CHROME, FIREFOX, EDGE, YANDEX;
* **language** - язык установки: EN, RU;
* **mode** - режим установки расширения. Значения: packed (упакованное), storelocal (из магазина для текущего  пользователя), unpacked (распакованное).

Пример установки без интернета:
```
LTools.WebBrowser.Native.exe install=CHROME lang=RU mode=packed
```

Пример установки при наличии интернета:
```
LTools.WebBrowser.Native.exe install=CHROME lang=RU mode=storelocal
```

## Автоматическая установка браузерных расширений

Подробнее см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings/autoinstall-browser-extension).