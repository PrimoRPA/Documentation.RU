# Управление пользователями

Пользователями могут управлять:
* Администратор Оркестратора — управляет пользователями всех тенантов\*.
* Администратор тенанта — имеет право управлять только пользователями своего тенанта.

> \**Под тенантом подразумевается относительно независимый экземпляр Оркестратора. Например, если организация состоит из обособленных подразделений/филиалов, то этому подразделению/филиалу можно [назначить тенант](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/tenants).*

## Администратор Оркестратора

Администратор Оркестратора может использовать для авторизации как встроенную учетную запись, так и созданную вручную.

К встроенным относятся: 
1. **superadmin** — видит все учетные записи в системе. Может создавать пользователей для дефолтного тенанта и для любого другого: в том числе учетные записи для роботов, Студии и Агента. Может создавать аккаунты администраторов Оркестратора и администраторов тенанта. Может входить в любой тенант.
2. **admin** — те же права, что и у superadmin, кроме **входа в любой тенант**.

Кроме того, в системе существует возможность вручную создать пользователя с правами администратора Оркестратора, аналогичными встроенной записи **admin**. Для этого:
1. Войдите под учетной записью администратора Оркестратора (superadmin или admin).
2. Создайте пользователя согласно [инструкции](https://docs.primo-rpa.ru/primo-rpa/orchestrator/settings/users/orch-users). В параметре **Роли** выберите встроенную системную роль **Administrator**. 


## Администратор тенанта

Администратор тенанта может управлять пользователями только своего тенанта. В том числе создавать учетные записи роботов, Студии и Агента в рамках своего тенанта.

Для администратора тенанта нет встроенной учетной записи — пользователя нужно создать вручную и назначить ему соответствующие права. Для этого:
1. Войдите под учетной записью администратора Оркестратора.
2. Создайте пользователя согласно [инструкции](https://docs.primo-rpa.ru/primo-rpa/orchestrator/settings/users/orch-users). В параметре **Роли** выберите встроенную системную роль **TenantAdministrator.**


