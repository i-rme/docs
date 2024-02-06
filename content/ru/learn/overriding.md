# Переопределение

Flight позволяет вам переопределить его стандартную функциональность под ваши собственные потребности, не меняя никакой код.

Например, когда Flight не может найти совпадение URL для маршрута, он вызывает метод `notFound`, который отправляет общий ответ `HTTP 404`. Вы можете изменить это поведение, используя метод `map`:

```php
Flight::map('notFound', function() {
  // Отобразить специальную страницу 404
  include 'errors/404.html';
});
```

Flight также позволяет заменить основные компоненты фреймворка.
Например, вы можете заменить класс маршрутизатора по умолчанию на свой собственный класс:

```php
// Зарегистрируйте свой собственный класс
Flight::register('router', MyRouter::class);

// Когда Flight загрузит экземпляр маршрутизатора, он загрузит ваш класс
$myrouter = Flight::router();
```

Однако методы фреймворка, такие как `map` и `register`, не могут быть переопределены. Вы получите ошибку, если попытаетесь это сделать.