# Что такое Flight?

Flight - это быстрый, простой, расширяемый фреймворк для PHP. Он довольно универсален и может использоваться для создания любого вида веб-приложений. Он создан с учетом простоты и написан таким образом, что легко понимать и использовать.

Flight - отличный начальный фреймворк для тех, кто нов в PHP и хочет научиться создавать веб-приложения. Он также отлично подходит для опытных разработчиков, которые хотят быстро и легко создавать веб-приложения. Он разработан для легкого создания RESTful API, простого веб-приложения или сложного веб-приложения.

```php
<?php

// если установлен с помощью composer
require 'vendor/autoload.php';
// или если установлен вручную из zip-файла
// require 'flight/Flight.php';

Flight::route('/', function() {
  echo 'привет, мир!';
});

Flight::start();
```

Просто, не так ли? [Узнайте больше о Flight!](learn)

## Быстрый старт
Есть пример приложения, который может помочь вам начать работу с фреймворком Flight. Перейдите по ссылке [flightphp/skeleton](https://github.com/flightphp/skeleton) для инструкций о том, как начать! Вы также можете посетить страницу с [примерами](examples) для вдохновения на то, какие возможности предоставляет Flight.

# Сообщество

Мы находимся на Matrix! Общайтесь с нами в чате [#flight-php-framework:matrix.org](https://matrix.to/#/#flight-php-framework:matrix.org).

# Вклад

Есть два способа, которыми вы можете внести вклад в Flight:

1. Вы можете внести вклад в основной фреймворк, посетив [репозиторий ядра](https://github.com/flightphp/core).
1. Вы можете внести вклад в документацию. Этот веб-сайт документации размещен на [Github](https://github.com/flightphp/docs). Если вы заметили ошибку или хотите улучшить что-то, не стесняйтесь исправлять и отправлять запрос на включение изменений! Мы стараемся следить за всеми обновлениями, но обновления и языковые переводы приветствуются.

# Требования

Flight требует PHP 7.4 или выше.

**Примечание:** PHP 7.4 поддерживается, потому что на момент написания (2024 год) PHP 7.4 является версией по умолчанию для некоторых дистрибутивов LTS Linux. Переход на PHP >8 вызвал бы много проблем для этих пользователей. Фреймворк также поддерживает PHP >8.

# Лицензия

Flight выпущен под лицензией [MIT](https://github.com/flightphp/core/blob/master/LICENSE).