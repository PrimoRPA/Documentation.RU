# Установка браузерных расширений

Расширения возможно установить:
* [вручную из Студии](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings/plugin-install#ruchnaya-ustanovka-iz-studii)
* [вручную из командной строки](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings/plugin-install#ustanovka-iz-komandnoi-stroki)
* [автоматически](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings/autoinstall-browser-extension)

## Ручная установка расширений



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