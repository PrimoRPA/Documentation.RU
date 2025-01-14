## Множественные производственные календари

В Оркестраторе существует 2 типа производственных календарей:
* Производственный календарь по умолчанию. Предполагает соотношение «один календарный год = один производственный календарь». 
* Множественные производственные календари. Предполагает соотношение «один календарный год = множество производственных календарей».

Режим множественных производственных календарей по умолчанию отключен. Включить его можно в конфигурационном файле WebApi в секции **ProductionCalendar**. Для этого установите параметру **Multiple** значение **true**:

```json
"ProductionCalendar": {
    "Multiple": true
  }
```
Управление множественными производственными календарями осуществляется в UI Оркестратора, в разделе [ЗАМЕНИТЬ ССЫЛКУ Настройки > Задания > Производственный календарь](https://docs.primo-rpa.ru/primo-rpa/orchestrator/settings/calendar). Доступ в раздел имеет только администратор Оркестратора.