# Очереди обмена данными

Очереди обмена данными — это структуры данных в БД Оркестратора. С их помощью можно организовать коммуникацию роботов и Студии при выполнении RPA-проектов.

Очереди могут:
1. Использовать принцип «Первым пришёл – первым обслужен» (FIFO).
2. Вместо FIFO использовать логику «Прочитать элемент может только один робот».

### Работа по FIFO

Для того, чтобы соблюдался принцип FIFO, необходимо правильно сформировать RPA-сценарий. Для извлечения элемента по FIFO используйте компонент [Получить из очереди](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_orch/els_queues/readfromqueue). В этом случае робот будет получать для обработки первый элемент, вошедший в очередь.

### Работа без FIFO

Работа по этому принципу предполагает, что робот может обратиться к любому незанятому элементу, а не только к первому. 

Пример:

1. Обратиться к элементу напрямую по его идентификатору (ID). Для этого используйте в сценарии компонент [Получить из очереди по ID](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_orch/els_queues/peekqueueid). Извлеченный элемент можно сразу занять для обработки роботом (с помощью свойства **Занимать**).
2. Извлечь из очереди список элементов, используя настроенный фильтр. В том числе с чекаутом: извлечь и сразу занять. Это гарантирует, что другие роботы не смогут прочитать занятые элементы. Данный механизм можно считать аналогом FIFO, только для множественного чтения и с более оптимальным использованием блокировок в БД. Для получения элементов в этом случае используется компонент [Получить из очереди по фильтру](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_orch/els_queues/peekqueuefilter). 

## Создание очереди

1. Перейдите в раздел Оркестратора **Роботы > Очереди обмена данными** (1 и 2 на рисунке).
2. Нажмите кнопку **«Добавить очередь»** (3):

   ![](../../resources/basics/queues/orch-add-queue-upd.png)

3. Укажите параметры очереди и сохраните изменения.

### Параметры очереди обмена данными

Символ `*` указывает на обязательность заполнения параметра.

| №  | Параметр                                                          | Описание                                                                                    |
| -- | ----------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| 1  | Наименование\*                                                    | Название очереди обмена данными для отображения в Оркестраторе. Должно состоять только из латинских букв, цифр, символов `_` и `-` и точки |
| 2  | Описание                                                          | Краткое произвольное описание очереди, которое будет отображаться в общей таблице очередей  |
| 3  | Тип уникальности натурального ключа                               | Натуральный ключ — это содержательный идентификатор элемента очереди, который задается пользователем произвольно (при создании элемента) и может отсутствовать.<p> Данный параметр определяет тип проверки на уникальность, которую система будет использовать по отношению к натуральному ключу. По умолчанию тип проверки не задан. </p> Доступные значения: <p> 1. **Проверка на уникальность внутри очереди** — натуральный ключ должен быть уникальным в рамках одной очереди.<p> </p> 2. **Проверка на уникальность глобально** — натуральный ключ должен быть уникальным в разрезе всех очередей. </p> |
| 4  | Время жизни элемента очереди (сек.)                               | Определяет время, по истечении которого система принудительно удалит элемент из очереди. По умолчанию время не задано |
| 5 | Физическое удаление      | Параметр может отсутствовать — его видимость зависит от [настройки](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/fine-tuning/physic-removing-items) в конфигурационном файле. Переключатель «Физическое удаление» определяет, как элемент будет удален из очереди — логически или физически. Логическое удаление задано по умолчанию. В этом случае удаленные элементы остаются в БД, а также видны в UI Оркестратора — они подсвечиваются красным. При физическом удалении элементы удаляются из БД и недоступны для просмотра в интерфейсе |
| 6  | На какие ошибки элемент должен ставиться в очередь повторно       | По умолчанию, если обработка элемента завершилась ошибкой, то система не возвращает его в очередь для повторной обработки. Данный параметр позволяет изменить поведение системы.<p> Доступные значения:</p> <p> 1. **Завершилось с ошибкой общего вида** (Error) — элемент поставится в очередь по FIFO повторно, если обработка завершилась со статусом `Error`. </p> <p> 2. **Завершилось с бизнес-ошибкой** (BusinessError) — элемент поставится в очередь по FIFO повторно, если обработка завершилась со статусом `BusinessError`.</p> <p> Допускается выбор сразу двух значений </p>|
| 7  | Максимальное количество попыток поставить элемент в очередь повторно | Если вы настроили повторное помещение элемента в очередь, то данный параметр позволяет указать предельное количество таких повторов. После превышения максимального количества попыток элемент в очередь повторно не поставится |
| 8  | Зашифрована              | Определяет, будут ли элементы очереди храниться в БД в зашифрованном виде. По умолчанию элементы не шифруются. Если сначала установить флаг, а при редактировании очереди его снять, то новые элементы останутся незашифрованными |
| 9  | Публичная                | Определяет, каким роботам будет доступна очередь: всем либо только перечисленным  |
| 10 | Specific JSON Schema     | JSON-схема, которой должен соответствовать элемент очереди. Тонкая настройка, не рекомендуется использовать без необходимости  |
| 11 | Output JSON Schema       | JSON-схема, которой должен соответствовать элемент очереди. Тонкая настройка, не рекомендуется использовать без необходимости  |
| 12 | Analytics JSON Schema    | JSON-схема, которой должен соответствовать элемент очереди. Тонкая настройка, не рекомендуется использовать без необходимости  |
| 13 | Реакция на невозможность извлечения элемента по FIFO | Определяет, какое значение система должна вернуть роботу в случае невозможности извлечь элемент по FIFO. Доступные значения: <p> 1. **Вернуть null** – будет использован внешний признак завершения попыток извлечь элемент (см. рисунок ниже, схема «б»). Например, достижение максимального количества итераций или получение внешнего сигнала. Рекомендуется использовать это значение, если очередь динамическая (одновременно работают писатели и читатели). </p> <p> 2. **Вернуть ошибку** – рекомендуется использовать при обработке заранее подготовленной очереди, чтобы отличать ошибку от случая, когда очередь пустая (см. рисунок ниже, схема «а»). Под ошибкой подразумевается количество попыток извлечь элемент перед получением финального null (пустая очередь). Пустая очередь в данном случае является признаком завершения </p> |
| 14 | Кол-во попыток при извлечении элемента по FIFO  | Применяется, если в качестве реакции на невозможность извлечения элемента по FIFO выбрано **Вернуть ошибку**. По умолчанию количество равно 3. <p> Использование этого алгоритма под нагрузкой может привести к увеличению времени извлечения элемента очереди и негативно влиять на клиентские тайм-ауты на стороне робота </p> |

Ниже приведены общие схемы алгоритмов для обработки очереди:

![](../../resources/basics/queues/схемы-алгоритмов-для-обработки-очереди.png)


## Элементы очереди
О том, как наполнить очередь элементами, см. раздел [Элементы очереди](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/data-queues/items).


