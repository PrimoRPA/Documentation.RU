# Мониторинг

Оркестратор регистрирует события, связанные с его внутренней работой, а также события от роботов, в три журнала: 
* журнал Оркестратора 
* журнал Робота (оркестраторного)
* журнал клиентского Робота
* журнал Проекта (часть журнала Робота). 

В UI оркестратора имеются формы для просмотра этих журналов, при помощи которых осуществляется мониторинг.

Для аналитики по журналам может применяться внешняя аналитическая система Grafana. Grafana не является частью Оркестратора, поставляется как дополнение к нему.