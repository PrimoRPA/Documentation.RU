<div style="background-color:#f2f2f2; padding:10px; border-radius:5px;">
  📝 Keyсloak — это инструмент для управления аутентификацией и авторизацией, обеспечивающий централизованное управление доступом к приложениям и сервисам. Он поддерживает современные протоколы безопасности, такие как OpenID Connect и OAuth 2.0.
</div>

### Авторизация в Primo RPA

Primo RPA поддерживает два режима авторизации через Keycloak:

- **Упрощённый поток** — кнопка с подсказкой *«Упрощённый поток»*
- **Поток с PKCE (Proof Key for Code Exchange)** — кнопка с подсказкой *«Поток с PKCE»*

На форме авторизации пользователь выбирает нужный режим — соответствующая кнопка с подсказкой отобразится автоматически.  
После успешной авторизации Keycloak передаёт роли в систему — они используются для управления доступом пользователей.

> ⚠️ Роли Keycloak становятся доступны только после настройки интеграции в конфигурации **WebAPI**.

Подробнее о настройке и использовании авторизации через Keyсloak — в [официальной документации Keyсloak](https://www.keycloak.org/documentation) и в статье [Интеграция с Keyсloak](https://docs.primo-rpa.ru/ru/orchestrator-new/orchestrator-sys-admin/keycloak-integration).



---

Статья https://docs.primo-rpa.ru/ru/primo-ai/developer/tutorial/authorization

## Авторизация

Все методы находятся в разделе `/auth` и предназначены для управления пользовательскими сессиями.

| Метод | Endpoint | Назначение |
|-------|----------|------------|
| `POST` | `/auth/Account/logout` | Выход пользователя из системы. |
| `POST` | `/auth/Account/KeyCloak1/Login` | Авторизация через KeyCloak1 |
| `GET` | `/auth/Account/KeyCloak2/Login` | Авторизация через KeyCloak2. Используется `redirect_uri`. |
| `GET` | `/auth/Account/KeyCloak2/AuthUrl1` | Получение AuthUrl для авторизации через KeyCloak2. |

### Определение режима авторизации

`GET /auth/account/type`

В ответе приходит числовой код:

- 0 — обычная авторизация

- 1 — Active Directory (AD)

- 2 — OpenId

### Работа с ролями (v2)

Методы находятся в /api/Roles/v2 и позволяют создавать и обновлять роли:

| Метод | Endpoint | Назначение |
|-------|----------|------------|
|`POST`|`/api/Roles/v2`|Создание новой роли|
|`PUT`|`/api/Roles/v2/{id}`|Обновление роли по id|




