# Обработка Ошибок

## Ошибки и Исключения

Все ошибки и исключения перехватываются Flight и передаются методу `error`.
Поведение по умолчанию - отправлять общий ответ `HTTP 500 Внутренняя Ошибка Сервера`
с некоторой информацией об ошибке.

Вы можете переопределить это поведение для ваших собственных потребностей:

```php
Flight::map('error', function (Throwable $error) {
  // Обработать ошибку
  echo $error->getTraceAsString();
});
```

По умолчанию ошибки не записываются в журнал веб-сервера. Вы можете включить это,
изменив конфигурацию:

```php
Flight::set('flight.log_errors', true);
```

## Не Найдено

Когда URL не может быть найден, Flight вызывает метод `notFound`. Поведение по
умолчанию - отправить ответ `HTTP 404 Не Найдено` с простым сообщением.

Вы можете переопределить это поведение для ваших собственных потребностей:

```php
Flight::map('notFound', function () {
  // Обработать не найдено
});
```