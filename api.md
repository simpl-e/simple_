## Definiciones del API
### routes/api.php

```php
<?php

// INICIALIZAR CONTROLADOR
resource($router, 'user', 'UserController');

// MÉTODOS POST EXTRA DEL CONTROLADOR
$router->post('{class}/{method}',
    function ($request, $class, $method) {

    $name = ucwords($class) . "Controller";
    $path = "App\\Http\\Controllers\\$name";
    $controller = app()->make($path);
    return $controller->$method($request);
});

// MÉTODOS API REST FULL
//gist.github.com/sohelamin/a85329700f1ecae1b490
//scotch.io/tutorials/simple-laravel-crud-with-resource-controllers
function resource($router, $uri, $contr) {
    //global $router;
    $router->get($uri, "$contr@get");
    $router->get("$uri/{id?}", "$contr@first");
    $router->post($uri, "$contr@post");
    $router->put("$uri/{id?}", "$contr@put");
    $router->patch("$uri/{id?}", "$contr@patch");
    $router->delete("$uri/{id?}", "$contr@delete");
}
```

## Uso del API (Guzzle)
### Métodos del controlador que llama

```php
// function get(Request $request) {
$client->get("user");

// function first(Request $request) {
$client->get("user/1");

// function post(Request $request) {
$client->post("user");

// function put(Request $request) {
$client->put("user");

// function patch(Request $request) {
$client->patch("user");

// function delete(Request $request) {
$client->delete("user");
```
