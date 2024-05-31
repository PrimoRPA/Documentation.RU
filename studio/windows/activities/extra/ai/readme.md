# AI

Библиотека **Primo.AI** позволяет автоматизировать работу с генеративными языковыми моделями. На данный момент поддерживается работа с Sber GigaChat и Yandex YandexGPT.

Библиотека содержит следующие элементы:

1. GigaChat:
   * [**Получить токен**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai/gigachat/el_gettoken) — получает токен GigaChat.
   * [**Вопрос в чат**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai/gigachat/el_chatmessage) — отправляет указанный вопрос в GigaChat.
2. YandexGPT:
   * [**Создать чат**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai/yandexgpt/el_chat) — создает чат с YandexGPT.
   * [**Вопрос в чат**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai/yandexgpt/el_chatmessage) — отправляет вопрос в чат с YandexGPT. Используйте этот элемент, если вам необходимо поддерживать диалог чат-бота и отправлять запросы в синхронном режиме.
   * [**Задать вопрос**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai/yandexgpt/el_instruct) — задает вопрос YandexGPT. Используйте этот элемент, если ваш вопрос не требует срочного ответа и, следовательно, можно отправить запрос в асинхронном режиме. В асинхронном режиме генерация текста займет больше времени, но ответ будет качественнее и дешевле.


## Установка Primo.AI

Ниже описан пошаговый способ установки **Primo.AI** в качестве зависимости проекта:

1. Откройте Primo RPA Studio и нажмите в главном меню кнопку **Управление зависимостями** <img src="../../../.gitbook/assets/managePackages32.png" alt="" data-size="line">

   ![](../../../resources/activities/extra/ai/управление-зависимостями.png)

2. В окне **Управление зависимостями** перейдите на вкладку **Nuget.org**. Введите в поисковом поле название пакета — **Primo.AI**.

   ![](../../../resources/activities/extra/ai/depend-nuget-primo-ai.png)

3. Установите пакет:
   * Нажмите кнопку **Установить**.

   ![](../../../resources/activities/extra/ai/1-install-primo-ai.png)

   * Нажмите кнопку **Сохранить**.

   ![](../../../resources/activities/extra/ai/2-save-primoai.png)

   * Нажмите кнопку **Установить**.

    ![](../../../resources/activities/extra/ai/3-install-primoai.png)

    * Дождитесь окончания установки и нажмите **ОК**.

    ![](../../../resources/activities/extra/ai/4-install-primo-ai.png)
 
4. Готово — пакет **Primo.AI** установлен в качестве зависимости. Немного подождите, пока зависимость загрузится. Во время установки проект будет перезапущен с предложением сохранить изменения.

5. Перейдите на панель элементов и найдите появившиеся группы `GigaChat` и `YandexGPT`.

   ![](../../../resources/activities/extra/ai/элементы-из-пакета-ai.png)

6. Перетащите элемент из нужной группы в процесс, чтобы начать с ним работу.


