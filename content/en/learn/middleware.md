# Route Middleware

Flight supports route and group route middleware. Middleware is a function that is executed before (or after) the route callback. This is a great way to add API authentication checks in your code, or to validate that the user has permission to access the route.

## Basic Middleware

Here's a basic example:

```php
// If you only supply an anonymous function, it will be executed before the route callback. 
// there are no "after" middleware functions except for classes (see below)
Flight::route('/path', function() { echo ' Here I am!'; })->addMiddleware(function() {
	echo 'Middleware first!';
});

Flight::start();

// This will output "Middleware first! Here I am!"
```

There are some very important notes about middleware that you should be aware of before you use them:
- Middleware functions are executed in the order they are added to the route. The execution is similar to how [Slim Framework handles this](https://www.slimframework.com/docs/v4/concepts/middleware.html#how-does-middleware-work).
   - Befores are executed in the order added, and Afters are executed in reverse order.
- If your middleware function returns false, all execution is stopped and a 403 Forbidden error is thrown. You'll probably want to handle this more gracefully with a `Flight::redirect()` or something similar.
- If you need parameters from your route, they will be passed in a single array to your middleware function. (`function($params) { ... }` or `public function before($params) {}`). The reason for this is that you can structure your parameters into groups and in some of those groups, your parameters may actually show up in a different order which would break the middleware function by referring to the wrong parameter. This way, you can access them by name instead of position.

## Middleware Classes

Middleware can be registered as a class as well. If you need the "after" functionality, you **must** use a class.

```php
class MyMiddleware {
	public function before($params) {
		echo 'Middleware first!';
	}

	public function after($params) {
		echo 'Middleware last!';
	}
}

$MyMiddleware = new MyMiddleware();
Flight::route('/path', function() { echo ' Here I am! '; })->addMiddleware($MyMiddleware); // also ->addMiddleware([ $MyMiddleware, $MyMiddleware2 ]);

Flight::start();

// This will display "Middleware first! Here I am! Middleware last!"
```

## Grouping Middleware

You can add a route group, and then every route in that group will have the same middleware as well. This is useful if you need to group a bunch of routes by say an Auth middleware to check the API key in the header.

```php

// added at the end of the group method
Flight::group('/api', function() {

	// This "empty" looking route will actually match /api
	Flight::route('', function() { echo 'api'; }, false, 'api');
    Flight::route('/users', function() { echo 'users'; }, false, 'users');
	Flight::route('/users/@id', function($id) { echo 'user:'.$id; }, false, 'user_view');
}, [ new ApiAuthMiddleware() ]);
```

If you want to apply a global middleware to all your routes, you can add an "empty" group:

```php

// added at the end of the group method
Flight::group('', function() {
	Flight::route('/users', function() { echo 'users'; }, false, 'users');
	Flight::route('/users/@id', function($id) { echo 'user:'.$id; }, false, 'user_view');
}, [ new ApiAuthMiddleware() ]);
```
