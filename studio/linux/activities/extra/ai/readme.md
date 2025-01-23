# AI

Библиотека **Primo.AI.Linux** позволяет автоматизировать работу с генеративными языковыми моделями. На данный момент поддерживается работа с Sber GigaChat и Yandex YandexGPT.

Библиотека содержит следующие элементы:

1. GigaChat:
   * [**Получить токен**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai/gigachat/el_gettoken) — получает токен GigaChat.
   * [**Вопрос в чат**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai/gigachat/el_chatmessage) — отправляет указанный вопрос в GigaChat.
2. YandexGPT:
   * [**Создать чат**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai/yandexgpt/el_chat) — создает чат с YandexGPT.
   * [**Вопрос в чат**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai/yandexgpt/el_chatmessage) — отправляет вопрос в чат с YandexGPT. Используйте этот элемент, если вам необходимо поддерживать диалог чат-бота и отправлять запросы в синхронном режиме.
   * [**Задать вопрос**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai/yandexgpt/el_instruct) — задает вопрос YandexGPT. Используйте этот элемент, если ваш вопрос не требует срочного ответа и, следовательно, можно отправить запрос в асинхронном режиме. В асинхронном режиме генерация текста займет больше времени, но ответ будет качественнее и дешевле.

Набор элементов не входит в базовую комплектацию, а устанавливается дополнительно в виде библиотеки Primo.AI.Linux. Ее можно скачать:
   * с официального сайта [NuGet](https://www.nuget.org/packages/Primo.AI.Linux);
   * напрямую из Студии с помощью [менеджера зависимостей](https://docs.primo-rpa.ru/primo-rpa/primo-studio/projects/manage-dependencies#menedzher-zavisimostei), где нужно выбрать раздел Nuget.org.
