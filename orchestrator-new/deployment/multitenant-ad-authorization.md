# Мультитенантная AD-авторизация

Мультитенантная AD-авторизация допускает использование одной доменной учетной записи в нескольких тенантах. 

Настройка включается в конфигурационном файле WebApi в секции **ActiveDirectory**. Для этого установите параметру **MultyTenantsGroup** значение `true`:

```
"ActiveDirectory": {
    "KerberosKeytabPath: "/opt/Primo/krb5.keytab",
    "Type": 5,
    "MultyForest":  ,
    "MultyTenantsGroup": true
 },
```

В этом случае для разрешения неоднозначности выбора тенанта по роли Оркестратора пользователь должен будет явно указывать тенант при AD-авторизации. 