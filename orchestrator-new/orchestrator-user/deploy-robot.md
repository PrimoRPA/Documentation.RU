# Развертывание робота

Развертывание робота на машине робота осуществляется на вкладке **Роботы/Все роботы** по нажатии на кнопку **Добавить робота** или **Добавить роботов**:  

![](../../../orchestrator-new/resources/orchestrator-user/deploy-robot1.PNG)

Красным восклицательным знаком отмечены роботы, которые при текущей стратегии очереди проектов не будут использованы при автоматическом запуске проектов через задания, так как не привязаны ни к какому проекту.

Два идентификатора ниже названия робота – это *RobotKey* (назначается системой при развертывании робота на машине робота) и *OperationKey* (назначается системой при старте проекта). RobotKey в дальнейшем может быть использован для идентификации папки робота на машине робота и Windows-task, который непосредственно запускает робота на машине робота. OperationKey позволяет перейти в журнал Оркестратора\* с фильтрацией по OperationKey.

>\* - *У робота есть собственный журнал*

При развертывании робота\* можно выбрать версию ядра (влияет на скорость загрузки больших RPA-проектов).

>\* - *Для роботов версии 1.1.30.6 и выше*

Ранее развернутых роботов можно переразвернуть: либо используя кнопку **Переразвернуть роботов**, либо сначала стереть робота на машине робота (кнопка **Стереть робота (на машине)**, см. рисунок 1) и развернуть заново (кнопки **Развернуть** или **Развернуть с параметрами**, см. рисунок 2):

Рисунок 1

![](../../../orchestrator-new/resources/orchestrator-user/deploy-robot2.PNG)

Рисунок 2

![](../../../orchestrator-new/resources/orchestrator-user/deploy-robot3.PNG)

При развертывании робота на машине робота используется дистрибутив робота. При запуске развертывания робота в поле **Статус развертывания** сразу отображается трекинг развертывания:

![](../../../orchestrator-new/resources/orchestrator-user/deploy-robot4.PNG)

Если трекинг не появился (индикатор в вертикальными цветными полосками), значит Оркестратор развернут неправильно, и/или неправильно настроена машина робота. В этом случае надо обратиться к системному администратору, выполнявшему развертывание Оркестратора и настройку машины робота.

Развертывание робота завершается переходом **Статуса развертывания** в *Готово*. Это означает, что робот удачно развернулся и готов к использованию.

![](../../../orchestrator-new/resources/orchestrator-user/deploy-robot5.PNG)

Описание стадий развертывания (трекинга развертывания) Робота приведено в ДОБАВИТЬ ССЫЛКУ [Приложение 1 – Стадии развертывания Робота] ().    
В UI Оркестратора описание стадии можно увидеть, если навести на полоску трекинга мышкой. 

Если на какой-то стадии произошел сбой, она отображается красным, при наведении мышкой в этом случае отображается сообщение об ошибке.



