# SAP Front End

Для работы компонентов SAP Front End (за исключением BAPI), необходимо включить поддержку SAP UI Scripting.

**Активация SAP UI Scripting**

В SAP UI перейти в транзакцию RZ11

![](../../../resources/activities/basic/sap/image-81.png)

В поле Param. Name ввести sapgui/user\_scripting

![](../../../resources/activities/basic/sap/image-192.png)

Нажать Change Value

![](../../../resources/activities/basic/sap/image-123.png)

В поле New Value ввести TRUE и нажать кнопку с дискетой

![](../../../resources/activities/basic/sap/image-186.png)

**Перезагрузить SAP UI**

Далее в SAP UI нажать кнопку Customize Local Layout и выбрать Options

![](../../../resources/activities/basic/sap/image-56.png)

Перейти в раздел Accessibility & Scripting и выбрать Scripting

![](../../../resources/activities/basic/sap/image-167.png)

Поставить галку в пункте Enable scripting и убрать галки в пунктах Notify...

![](../../../resources/activities/basic/sap/image-34.png)
