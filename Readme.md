# Fetch
![alt text](image.png)
## JavaScript может отправлять сетевые запросы на сервер и подгружать новую информацию по мере необходимости.
## Например, мы можем использовать сетевой запрос, чтобы:
## Отправить заказ,
## Загрузить информацию о пользователе,
## Запросить последние обновления с сервера, …и т.п.
## Для сетевых запросов из JavaScript есть широко известный термин «AJAX» (аббревиатура от Asynchronous JavaScript And XML). XML мы использовать не обязаны, просто термин старый, поэтому в нём есть это слово. Возможно, вы его уже где-то слышали.
## Есть несколько способов делать сетевые запросы и получать информацию с сервера.
## Метод fetch() — современный и очень мощный, поэтому начнём с него. Он не поддерживается старыми (можно использовать полифил), но поддерживается всеми современными браузерами.
## Базовый синтаксис:
![alt text](<Snap (13).png>)
## url – URL для отправки запроса.
## options – дополнительные параметры: метод, заголовки и так далее. Без options это простой GET-запрос, скачивающий содержимое по адресу url.
## Браузер сразу же начинает запрос и возвращает промис, который внешний код использует для получения результата.
## Процесс получения ответа обычно происходит в два этапа.
## Во-первых, promise выполняется с объектом встроенного класса Response в качестве результата, как только сервер пришлёт заголовки ответа.
## На этом этапе мы можем проверить статус HTTP-запроса и определить, выполнился ли он успешно, а также посмотреть заголовки, но пока без тела ответа.
## Промис завершается с ошибкой, если fetch не смог выполнить HTTP-запрос, например при ошибке сети или если нет такого сайта. HTTP-статусы 404 и 500 не являются ошибкой.
## Мы можем увидеть HTTP-статус в свойствах ответа: status – код статуса HTTP-запроса, например 200. ok – логическое значение: будет true, если код HTTP-статуса в диапазоне 200-299.
## Например:
![alt text](<Snap (14).png>)
## Во-вторых, для получения тела ответа нам нужно использовать дополнительный вызов метода. Response предоставляет несколько методов, основанных на промисах, для доступа к телу ответа в различных форматах:
## response.text() – читает ответ и возвращает как обычный текст,
## response.json() – декодирует ответ в формате JSON,
## response.formData() – возвращает ответ как объект FormData (разберём его в следующей главе),
## response.blob() – возвращает объект как Blob (бинарные данные с типом),
## response.arrayBuffer() – возвращает ответ как ArrayBuffer (низкоуровневое представление бинарных данных), помимо этого, response.body – это объект ReadableStream, с помощью которого можно считывать тело запроса по частям. Мы рассмотрим и такой пример несколько позже.
## Например, получим JSON-объект с последними коммитами из репозитория на GitHub:
![alt text](<Snap (15).png>)
   