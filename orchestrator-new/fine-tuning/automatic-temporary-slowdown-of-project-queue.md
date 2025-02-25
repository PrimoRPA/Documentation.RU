# Автоматическое временное замедление очереди проектов 

При запуске робота с проектом, вышедшим из очереди проектов, может возникнуть риск отказа в обслуживании по причине перегруженности машины роботов. 
Чтобы предотвратить риск отказа в обслуживании, можно использовать автоматическое замедление очереди проектов. 
В этом случае проект продолжит ждать в очереди проектов, пока нагрузка на машине робота не спадет до приемлемой.

Параметры, влияющие на автоматическое временное замедление очереди проектов, находятся в секциях **Worker** и **ProjectQueue**. Их описание приведено в таблицах ниже.

### Параметры сбора метрик производительности с машин роботов 

Данные параметры настраиваются в секции Worker.

| №  | Параметр                         | Назначение                       | Примечание        |
| -- | -------------------------------- | -------------------------------- | ----------------- |
| 1. | **CollectBackgroundPerformance** | Собирать метрики производительности машин в фоне, одновременно с проверкой их доступности. Если включена, может использоваться автоматическое временное замедление очереди проектов при пиках нагрузки на машинах роботов.<p> Только для CollectWorkerStatusService = 1 </p> |  |
| 2. | **PerformanceDeltaPrcnt**        | Шаг разбиения шкалы 0-100 на интервалы. Пример: 0, 25, 50, 75, 100 |  |
| 3. | **PerformanceDelta100Prcnt**     | Величина (абсолютное значение процента), на которую метрики должны отличаться от 100%, чтобы был зафиксирован факт перегрузки машины |  |



### Параметры автоматического временного замедления очереди проектов при пиках нагрузки на машинах роботов 

Данные параметры настраиваются в секции ProjectQueue.

| №  | Параметр                          | Назначение                       | Примечание        |
| -- | --------------------------------- | -------------------------------- | ----------------- |
| 1. | **WorkerPerformanceHighDuration** | Продолжительность (сек) нахождения метрик машины робота в диапазоне высокой нагрузки, при которой проект должен снова уйти в очередь проектов. <p>Если равно 0 – замедление очереди не используется </p> | Если равно 0, метрики производительности с машин роботов все равно собираются, если этот сбор включен |
| 2. | **WorkerPerformanceHighCPUOnly**  | Для принятия решения о том, что машина робота перегружена, использовать только CPU% |  |
| 3. | **WorkerPerformanceHighResolver** | Тип определения высокой нагрузки: <p> * 0 – фиксированное значение, например, 95%. Не связано с Worker.PerformanceDeltaPrcnt.</p> <p> * 1 – 100% – Worker.PerformanceDeltaPrcnt </p> | Если шкала разбивается на большие интервалы или не кратные 100, то попадание нагрузки в последний интервал может быть грубой оценкой или неоправданно завышенной. Тогда можно эту оценку указать явно в AbsoluteWorkerPerformanceHigh и использовать тип 1  |
| 4. | **AbsoluteWorkerPerformanceHigh** | Абсолютное значение нагрузки, которое считается высоким. <p>Только для WorkerPerformanceHighResolver = 0 </p> |  |

