# Журнал Оркестратора

Для просмотра событий Оркестратора используется раздел главного меню **Журнал**:

![](<../../.gitbook/assets/0 (5)>)

События Оркестратора делятся на классы: 
1. «Информационное».
2. «Инцидент безопасности».
3. «Ошибки».
4. «Корректировка». 
 
Соответствующие вкладки на форме журнала – это предустановленная фильтрация по классам событий.

Разным событиям соответствует разная информация. Например, общее правило отображения поля **Пользователь** такое: авторизованный пользователь выполняет некоторую операцию. Событие **Пользователь авторизовался** подразумевает, что пользователя еще как такового нет, есть только реквизиты (credential). Будущему пользователю только отдали его сессию. Кому именно (credential), отображается в столбце **EntityData**. Когда этот уже (настоящий) пользователь снова обратится в Оркестратор в сессии, например, выполнит какую-то операцию по кнопке, он будет уже зафиксирован в userId. Очень много событий Оркестратор генерирует внутренних, принципиально без «пользователя».

Фильтр **Дата события** предустановлен, используется последнее сохраненное значение. По умолчанию при сбросе поля устанавливается для текущего часа.

Цепочку событий операции можно выделить среди прочих событий, если отфильтровать по коду операции.

На вкладке **Отчеты** находятся кнопки, по нажатию на которые открываются аналитические отчеты в [Grafana](https://docs.primo-rpa.ru/primo-rpa/orchestrator/monitoring/grafana).

Свод всех событий Оркестратора приведен в [Приложении 3 – События Оркестратора](https://docs.primo-rpa.ru/primo-rpa/orchestrator/appendix/appendix3).