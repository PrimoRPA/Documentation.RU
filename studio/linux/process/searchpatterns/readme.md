# ВЕРСИЯ ПОД WINDOWS

# Шаблоны поиска

**Шаблон поиска** — это свойство ряда элементов Студии, которое используется для взаимодействия с пользовательским интерфейсом программ. Шаблон позволяет идентифицировать компонент приложения и получить к нему программный доступ.

Свойство **Шаблон поиска** есть, например, у элемента [**Клик мышью**](https://docs.primo-rpa.ru/primo-rpa/g\_elements/osnovnye-elementy/els\_uiinteraction/el\_click) — с его помощью можно определить кнопку приложения, по которой нужно кликнуть.

## Общая информация

Шаблон представляет собой JSON-файл, который содержит заданный набор свойств для идентификации компонента. Его можно сформировать вручную или автоматически. Автоматическое формирование является предпочтительным сценарием, для этого используется кнопка **Выбрать компонент** ![](../../resources/process/searchpatterns/image-553.png) — она вызывает захват элемента управления в зависимости от категории приложения. Кнопку можно найти на панели элемента или в его свойствах, например:

![](../../resources/process/searchpatterns/клик-мышью.-волшебная-палочка.png)

Primo RPA поддерживает поиск в категориях:

* **Браузер**
* **Рабочий стол**
* **SAP**

Подробнее о них см. в разделе [**Категории приложений**](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/searchpatterns/apps-categories).

Редактировать шаблон можно двумя способами:

* **В формате правки JSON-файла.** Для открытия файла нажмите в свойстве **Шаблон поиска** значок многоточия. Пример: ![](../../resources/process/searchpatterns/шаблон-поиска.-многоточие-2.png).
* **Через окно редактора шаблона**. Для открытия графического окна нажмите кнопку ![](../../resources/process/searchpatterns/image-516-1-2-1-1-1-4.png). Окно редактора видоизменяется в зависимости от категории приложения. Примеры интерфейса приведены в подразделе **Интерфейс редактора шаблона**.

## Интерфейс редактора шаблона

Интерфейс редактора зависит от категории приложения, в котором необходимо найти компонент. В ситуации, когда категория неизвестна, окно редактора будет выглядеть так:

![](../../resources/process/searchpatterns/шаблон-поиска.-неизвестно.png)

После выбора категории приложения в окне редактора появятся соответствующие параметры поиска и возможные команды.

Интерфейс редактора шаблона для категорий **Браузер** и **Рабочий стол** имеет следующие общие элементы:

![](../../resources/process/searchpatterns/шаблон-поиска.-интерфейс,-общее.png)

1. **Режим** — иконка выбора между категориями приложений (Браузер, Рабочий стол, SAP). Также доступен режим **Контейнер**, о котором подробнее сказано ниже, в подразделе [**Выбор категории приложений**](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/searchpatterns#vybor-kategorii-prilozhenii).
2. **Подтип** — список значений зависит от выбранного режима. Например, в режиме **Рабочий стол** потребуется выбрать тип автоматизации, в режиме **Браузер** - тип браузера.
3. **Заголовок** — параметр для поиска. Например, имя главного окна десктоп-приложения в режиме **Рабочий стол**.
4. **Выбрать компонент** ![](../../resources/process/searchpatterns/image-553.png) — позволяет автоматически выбрать элемент управления и добавить его в шаблон.
5. **Отобразить компонент** ![](../../resources/process/searchpatterns/15-1-1-1-1-1-1.png) — выделяет элемент управления, который был задан в шаблоне. Используется для проверки правильности шаблона поиска.
6. **Инспектор UI** — инструмент для детального исследования интерфейсов приложений. Выводит окно с подробной информацией обо всех открытых приложениях и их компонентах. Позволяет перенести выбранный элемент в шаблон. Подробнее об инструменте см. [**здесь**](https://docs.primo-rpa.ru/primo-rpa/primo-studio/instrumenty/uiexplorer).
7. ![](../../resources/process/searchpatterns/12-2-3-1-1-2-1-4.png) — кнопка для ручного добавления элемента управления в шаблон.
8. ![](../../resources/process/searchpatterns/13-1-1-2-1-1-2-1.png) — кнопка для удаления элемента из шаблона. Возможно удалить клавишей `Del`.

Кроме этого, окно редактора имеет две таблицы: первая - для добавления строк с компонентами, а вторая — для детализации каждой строки:

![](../../resources/process/searchpatterns/шаблон.-таблицы.png)

## Процесс поиска

Рассмотрим, как происходит поиск компонента на примере работы с приложением **Калькулятор** (категория **Рабочий стол**).

С точки зрения Windows, приложение состоит из ряда компонентов (кнопки, текстовые поля, таблицы), объединенных в дерево. Любая кнопка, которую видит пользователь в интерфейсе программы, будет входить в данное дерево. В свою очередь, каждый компонент обладает набором свойств: они идентифицируют элемент приложения, предоставляют информацию о его специфике и назначении, разбивают все компоненты рабочего стола по тегам и классам.

Для идентификации компонента Primo RPA также использует поиск по его свойствам.

Откроем приложение **Калькулятор** в Windows. Создадим в Студии новый проект и выполним следующие действия:

1. Добавим контейнер [**Присоединиться к приложению**](https://docs.primo-rpa.ru/primo-rpa/g\_elements/osnovnye-elementy/els\_desktop/el\_desktop\_attach). В свойстве **Заголовок** воспользуемся кнопкой ![](../../resources/process/searchpatterns/image-553.png) для быстрого указания названия приложения (Калькулятор).
2. Поместим в контейнер элемент [**Клик мышью**](https://docs.primo-rpa.ru/primo-rpa/g\_elements/osnovnye-elementy/els\_uiinteraction/el\_click).
3. На панели элемента **Клик мышью** нажмем кнопку **Выбрать компонент** ![](../../resources/process/searchpatterns/image-553.png) — для автоматического добавления компонента в шаблон.

![](../../resources/process/searchpatterns/шаблон-поиска.-калькулятор.png)

**Внимание! Окно с приложением Калькулятор должно быть активным!**

После нажатия кнопки ![](../../resources/process/searchpatterns/image-553.png) мы переместимся в окно с **Калькулятором**, чтобы выбрать нужный компонент. При наведении указателя на элемент приложения, он подсветится, а в левом верхнем углу появится его увеличенное изображение:

![](../../resources/process/searchpatterns/шаблон-поиска.-выбор-кнопки-в-калькуляторе.png)

Выберем **кнопку 5** — появится окно с выбором свойств для идентификации компонента:

> *В свойстве Index нумерация элементов начинается с 1.*

![](../../resources/process/searchpatterns/селекторы-калькулятора.png)

Необходимо выбрать такую комбинацию свойств, которая была бы уникальна и неизменна для данного компонента. Для нашего случая выберем параметры **AutomationID**, **Name** (имя элемента автоматизации) и нажмем **ОК** — селектор создан. Он сохранится в JSON-файле шаблона поиска. Если просмотреть готовый шаблон через окно редактора, он будет выглядеть таким образом:

![](../../resources/process/searchpatterns/шаблон-поиска.-контейнер.png)

В дальнейшем, при обработке шаблона, робот возьмет заданные свойства и проанализирует дерево компонентов в поисках позиции, которая имеет указанные значения в параметрах **AutomationID** и **Name**. При совпадении значений компонент будет найден.

## Выбор категории приложений

Категорию приложения (Рабочий стол, Браузер, SAP, Контейнер) можно выбрать в шаблоне вручную либо использовать автоматическое определение. Студия самостоятельно определяет категорию в том случае, если пользователь добавляет компонент в шаблон автоматически — кнопкой ![](../../resources/process/searchpatterns/image-553.png).

Так, в примере с Калькулятором окно редактора шаблона отображается в режиме **Контейнер**. Система выбрала данный режим потому, что элемент **Клик мышью** находится в контейнере [**Присоединиться к приложению**\*](https://docs.primo-rpa.ru/primo-rpa/g\_elements/osnovnye-elementy/els\_desktop/el\_desktop\_attach). Студия также определила, что Калькулятор, к которому установлено подключение в контейнере, относится к приложениям рабочего стола, поэтому в окне редактора отображаются настройки для приложений рабочего стола.

Если бы мы использовали шаблон поиска для компонента веб-приложения, а элемент **Клик мышью** находился бы в контейнере [**Присоединиться к браузеру**](https://docs.primo-rpa.ru/primo-rpa/g\_elements/osnovnye-elementy/els\_browser/el\_browser\_attach), то параметры поиска в окне редактора соответствовали параметрам для категории приложений **Браузер**:

![](../../resources/process/searchpatterns/контейнер.-браузер.png)

Подробнее работа с шаблоном поиска в различных категориях описана в разделе [**Категории приложений**](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/searchpatterns/apps-categories).

> \*_Размещение элементов Студии в контейнере экономит ресурсы компьютера и улучшает работу с нагруженными проектами._

## Инспектор UI

Работа с инструментом **Инспектор UI** подробнее описана [**здесь**](https://docs.primo-rpa.ru/primo-rpa/primo-studio/instrumenty/uiexplorer).