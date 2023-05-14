# Wishlist API

Это простой API для управления списком желаний пользователей. Сервер написан на Node.js и использует файловую систему для хранения данных пользователей и их желаний.

## Описание API

API предоставляет следующие конечные точки:

- <span style="color:Olive">/register</span> - регистрация нового пользователя
- <span style="color:Olive">/login</span> - авторизация пользователя
- <span style="color:Olive">/addWish</span> - добавление желания пользователя
- <span style="color:Olive">/wishlist/{userLogin}</span> - просмотр списка желаний пользователя
- <span style="color:Olive">/wish/{itemId}</span> - просмотр деталей желания

## Как это работает

Когда поступает запрос типа <span style="color:Olive">POST</span> на <span style="color:Olive">/register</span>, сервер считывает входящие данные в формате JSON и проверяет, существует ли уже такой пользователь. Если нет, то сервер генерирует новый <span style="color:Olive">uuid</span> и сохраняет данные пользователя в JSON файл.

Когда поступает запрос типа <span style="color:Olive">POST</span> на <span style="color:Olive">/login</span>, сервер считывает входящие данные в формате JSON и проверяет, существует ли такой пользователь и является ли пароль правильным. Если да, то сервер генерирует JSON-токен и отправляет его обратно клиенту.

Когда поступает запрос типа <span style="color:Olive">POST</span> на <span style="color:Olive">/addWish</span>, сервер считывает входящие данные в формате JSON и проверяет авторизационный токен пользователя. Затем, если пользователь существует, сервер сохраняет поступившее желание (wish) в данные пользователя.

Когда поступает запрос типа <span style="color:Olive">GET</span> на <span style="color:Olive">/wishlist/{userLogin}</span>, сервер считывает логин ID из URL запроса и отправляет данные списка желаний пользователя обратно клиенту.

Когда поступает запрос типа <span style="color:Olive">GET</span> на <span style="color:Olive">/wish/{itemId}</span>, сервер считывает ID предмета из URL запроса и проверяет авторизационный токен пользователя. Затем, если предмет существует, сервер отправляет данные для указанного предмета обратно клиенту, иначе возвращает сообщение об ошибке 404.

## Как запустить
1. Установите Node.js на свой компьютер.
2. Склонируйте этот репозиторий на свой компьютер.
3. Откройте терминал или командную строку и перейдите в папку с проектом.
4. Запустите команду <span style="color:Olive">npm install</span> для установки зависимостей.
5. Запустите команду <span style="color:Olive">npm start</span> для запуска сервера.
6. Запросы выполняются на адрес http://localhost:3000.

## Зависимости
* <span style="color:Olive">uuid</span>
* <span style="color:Olive">jsonwebtoken</span>

## Будет доработано
* Валидация получаемых данных
