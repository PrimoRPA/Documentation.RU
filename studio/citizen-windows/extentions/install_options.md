---
asIndexPage: true
---

import { Cards, Callout } from 'nextra/components';

# Установка расширений

Расширения возможно установить:

- [Вручную из Студии](/primo-studio/settings/plugin-install#ruchnaya-ustanovka-iz-studii) 
- [Вручную из командной строки](/primo-studio/settings/plugin-install#ustanovka-iz-komandnoi-stroki) 
- [Автоматически](/primo-studio/settings/autoinstall-browser-extension) 

## Ручная установка из Студии

Инструкции см. в разделах:

<Cards>
  <Cards.Card title="Chrome" href="./plugin-install/chrome" />  
  <Cards.Card title="FireFox" href="./plugin-install/firefox" />  
  <Cards.Card title="Edge" href="./plugin-install/edge" />  
  <Cards.Card title="Yandex" href="./plugin-install/yandex" />  
 
</Cards>

## Установка из командной строки

Ниже приводятся способы установки расширений из командной строки.

```
LTools.WebBrowser.Native.exe install=<browser> lang=<language> mode=<mode> manifest=v3
```

Поддерживаемые аргументы:

- **browser** — тип браузера: CHROME, FIREFOX, EDGE, YANDEX.
- **language** — язык установки: EN, RU.
- **mode** — режим установки расширения. Доступные значения:
  - packed — упакованное;
  - storelocal — из магазина для текущего пользователя;
  - unpacked — распакованное.
- **manifest** — используется для установки браузерного расширения на основе нового [манифеста версии 3](https://developer.chrome.com/docs/extensions/develop/migrate/what-is-mv3?hl=ru). Единственное допустимое значение параметра — `v3`. Расширение на базе Manifest V3 разработано, чтобы избежать проблем с совместимостью в поздних версиях браузеров Chrome, Yandex, Edge, основанных на движке Chromium. Если параметр `manifest` не указан, то по умолчанию будет установлено расширение для манифеста V2.

<Callout type="info" emoji="ℹ️">
  Версии расширения Primo RPA Extension для Manifest V2 нумеруются с 1.xx
  (например, 1.66), для Manifest V3 — с 3.xx (например, 3.66).
</Callout>

<Callout type="warning" emoji="⚠️">
  Если вы хотите изменить версию манифеста для установленного расширения, то
  сначала удалите расширение на базе старого манифеста и только затем
  устанавливайте новое. Учтите, что для браузера Firefox невозможно установить
  расширение на базе V3.
</Callout>

#### Особенности работы расширения с Manifest V2

Расширение на базе второй версии манифеста (1.xx) на данный момент может работать нестабильно из-за политик Google в отношении старых расширений, не предназначенных для ManifestV3. Чтобы продолжить работу с расширением для Manifest V2, в рабочие контуры рекомендуется добавить политику `ExtensionManifestV2Availability` со значением `2`, которая разрешает пользоваться расширениями на основе Manifest V2.

Например, для браузера Chrome это можно сделать или групповыми политиками или вручную, запустив в CMD или Powershell скрипт от имени администратора на сервере агента (компьютере клиента):

```
reg add HKLM\SOFTWARE\Policies\Google\Chrome /v ExtensionManifestV2Availability /t REG_DWORD /d 2 /f
```

После этого, [по заявлениям Google](https://chromeenterprise.google/policies/?hl=ru#ExtensionManifestV2Availability), можно будет работать с расширениями второй версии манифеста до июня 2025 года.

#### Особенности работы расширения с Manifest V3

Расширение Primo RPA Extension на основе Manifest V3 является новым решением, поэтому рекомендуется проверять работоспособность проекта с браузерными элементами в Студии перед тем, как добавлять его в Оркестратор или Robor Runner.

#### Пример установки браузерного расширения

Установка браузерного расширения для Manifest V3 без интернета:

```
LTools.WebBrowser.Native.exe install=CHROME lang=RU mode=packed manifest=v3
```

Установка браузерного расширения для Manifest V3 при наличии интернета:

```
LTools.WebBrowser.Native.exe install=CHROME lang=RU mode=storelocal manifest=v3
```

Если вы хотите установить расширение для Manifest V2, просто не указывайте параметр **manifest**.


## Автоматическая установка браузерных расширений

Подробнее см. [здесь](/primo-studio/settings/autoinstall-browser-extension).

<Callout type="info" emoji="ℹ️">
  При автоматическом способе устанавливается только расширение на базе манифеста
  V2 (версия расширения 1.xx).
</Callout>
