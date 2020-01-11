# Eurostudio-test
## Описание приложения
Приложение представляет собой простое REST-api для работы с проектами с поддержкой авторизации посредством jwt-токенов.

## Требования к системе
Для запуска приложения необходимы
* MySQL 5.7
* PHP7
* Composer
* OpenSSL (для Windows взять [отсюда](https://slproweb.com/products/Win32OpenSSL.html))

## Установка приложения
1. скопировать содержимое репозитория в локальную папку
2. открыть папку проекта в командной строке
3. установить все зависимости backend
```
composer install
```
4. создать файл **.env.local**, скопировав в него содержимое **.env**
5. настроить подключение к базе данных в файле **.env.local**
6. создать базу данных
```
php bin/console doctrine:database:create
```
7. выполнить миграции
```
php bin/console doctrine:migrations:migrate
```
8. создать пользователя
```
php bin/console fos:user:create
```
9. сгенерировать SSH-ключи, следуя [инструкции](https://github.com/lexik/LexikJWTAuthenticationBundle/blob/master/Resources/doc/index.md#installation)
10. запустить сервер разработки
```
php bin/console server:run
```
11. выполнить CURL-запрос с телом вида *{"email":"string","password":"string"}* по пути */api/login* для получения jwt-токена
12. перейти в корень проекта по url-адресу */* и использовать полученный jwt-токен для выполнения запросов
