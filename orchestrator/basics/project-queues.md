# Очереди проектов

При нехватке Роботов или лицензий RPA-проекты становятся в очередь проектов. Наблюдать очередь RPA-проектов можно на [главной странице](https://docs.primo-rpa.ru/primo-rpa/orchestrator/monitoring/dashboard).

Назначение очереди проектов:
1. Не потерять запуск проекта, отсрочив его запуск. В период этой отсрочки, возможно, в системе появятся свободные Роботы, подходящие для выполнения проекта. [Подходящий Робот – это Робот, который может выполнить проект](https://docs.primo-rpa.ru/primo-rpa/orchestrator/settings/projects-queue).
2. Если одновременно[1] несколько проектов поставлено на выполнение, очередь позволяет выбрать проект с максимальным приоритетом.
Рекомендуется не допускать возникновения очереди проектов. Если она неизбежна – заведомо возможны ситуации нехватки Роботов/лицензий – настроить её на оптимальную работу можно при помощи ряда параметров, непосредственно или косвенно влияющих на работу очереди:

| №  | Настройки      | Описание        | Примечание               |
| -- | -------------- | --------------- | ------------------------------------------ |
| 1 | Приоритет проекта    | Задается в форме создания/редактирования проекта. Связана с конкретным проектом | Существует 3 фиксированных приоритета. Определяет, как долго проект будет находиться в очереди задержки, и в каком порядке проекты будут выходить из очереди проектов при одновременном попадании в нее |
| 2 | Время нахождения проекта в очереди задержки (сек.) | Задается в конфигурационном файле Оркестратора для каждого из 3-х приоритетов. Общесистемная настройка | Требуется перезагрузка Оркестратора. Чем меньше проект находится в очереди ожидания, тем чаще для него будет искаться подходящий Робот |
| 3 | Время нахождения проекта в очереди приоритетов (мсек.) | Задается в конфигурационном файле Оркестратора. Общесистемная настройка | Небольшая по времени задержка перед основной очередью проектов, которая необходима для того, чтобы упорядочить по приоритету проекты, запущенные (также пришедшие в очередь из очередей задержек) практически одновременно. Требуется перезагрузка Оркестратора. Чем больше время, тем выше вероятность правильного порядка выхода из очереди проектов в порядке их приоритета |
| 4 | [Стратегия очереди проектов](https://docs.primo-rpa.ru/primo-rpa/orchestrator/settings/projects-queue) | Задается на форме настройки Оркестратора. Общесистемная настройка | Менее ограниченная стратегия позволит для проектов использовать больше Роботов для поиска подходящих, уменьшает вероятность очереди |
| 5 | [Привязка роботов к RPA-проектам](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/assign-task) | Задается на форме привязки Роботов к RPA-проектам. Связана с конкретным проектом, но может влиять на систему в целом в условиях дефицита Роботов или лицензий | Ограничивает множество Роботов для поиска подходящих, увеличивает вероятность очереди |
| 6 | Проект запускается в единственном экземпляре | Задается в форме создания/редактирования проекта. Связана с конкретным проектом, но может влиять на систему в целом в условиях дефицита роботов или лицензий | Если установлен этот флаг, запуск проекта будет пропускаться, пока не завершится текущий запуск, вероятность очереди уменьшается |
| 7 | Разрешить наложение | Задается [в форме создания задания](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/tasks). Связана с конкретным заданием, но может влиять на систему в целом в условиях дефицита Роботов или лицензий | Если не установлен этот флаг, запуск проекта задания будет пропускаться, пока не завершится текущий запуск задания, вероятность очереди уменьшается. Иначе задание будет стараться запуститься на другом роботе, и при его отсутствии проект задания встанет в очередь |
| 8 | Не повторять в очереди ожидания | Задается в форме создания/редактирования проекта. Связана с конкретным проектом, но может влиять на систему в целом в условиях дефицита Роботов или лицензий | Если установлен этот флаг, проект не будет копиться в очереди ожидания, соответственно при выходе проекта из очереди каждый раз не потребуются роботы, вероятность очереди уменьшается |

---
1. Понятие одновременности тут условное. Если проект с меньшим приоритетом встанет в очередь раньше, чем проект с большим приоритетом, но в более ранний временной интервал обслуживания очереди, проект с меньшим приоритетом выйдет из очереди раньше.