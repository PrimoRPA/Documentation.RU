# Журнал системных сессий

![](../../../resources/activities/basic/desktop/systemsessionslog.png)

Элемент, позволяющий читать лог(и) сессий операционной системы.

Позволяет компенсировать и дополнить регистрацию системных событий в случаях, когда их невозможно отследить/перехватить в режиме реального времени.

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

1. **С даты/времени** *[System.Nullable\<System.DateTime>]* - Минимальная начальная дата/время сессии
1. **По дату/время** *[System.Nullable\<System.DateTime>]* - Максимальная конечная дата/время сессии
1. **Максимальное число сессий** *[System.Nullable\<System.Int32>]* - Максимальное допустимое число сессий в итоговом множестве
1. **Переменная** *[System.Collections.Generic.List\<LTools.Desktop.Model.SystemSessionInfo>]* - Переменная для сохранения списка сессий

### Свойства типа данных `LTools.Desktop.Model.SystemSessionInfo`

Тип `LTools.Desktop.Model.SystemSessionInfo` имеет следующие свойства:

1. **UserOrPseudoUser** - Логин пользователя или имя процесса (псевдо-пользователя)
1. **InteractionDescription** - Описание способа взаимодействия с системой
1. **StartedAt** - Дата/время начала сессии
1. **EndedAt** - Дата/время окончания сессии
1. **Duration** - Длительность сессии
1. **SystemSessionState** - Состояние сессии
