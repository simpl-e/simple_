# Servidor

## Definiciones del API Lumen
### routes/api.php

```php
<?php

$router->group(['middleware' => 'jwt-auth']
    , function () use ($router) {

$router->get('{class}'
    , function ($request, $class) {
  $controller=app()->make("App\\Http\\Controllers\\"
  . ucwords($class) . "Controller");
  return $controller->get($request);
});

$router->get('{class}/{id}'
    , function ($request, $class, $id) {
  $controller=app()->make("App\\Http\\Controllers\\"
    . ucwords($class) . "Controller");
  return $controller->first($request, $id);
});

$router->post('{class}'
    , function ($request, $class) {
  $controller=app()->make("App\\Http\\Controllers\\"
    . ucwords($class) . "Controller");
  return $controller->post($request);
});

$router->put('{class}/{id}'
    , function ($request, $class, $id) {
  $controller=app()->make("App\\Http\\Controllers\\"
    . ucwords($class) . "Controller");
  return $controller->put($request, $id);
});

$router->patch('{class}/{id}'
    , function ($request, $class, $id) {
  $controller=app()->make("App\\Http\\Controllers\\"
    . ucwords($class) . "Controller");
  return $controller->patch($request, $id);
});

$router->delete('{class}/{id}'
    , function ( $request, $class, $id) {
  $controller=app()->make("App\\Http\\Controllers\\"
  . ucwords($class) . "Controller");
  return $controller->delete($request, $id);
});

// EXTRA
$router->post('{class}/{method}'
    , function ($request, $class, $method) {
  $controller=app()->make("App\\Http\\Controllers\\"
    . ucwords($class) . "Controller");
    return $controller->$method($request);
});

});
```

---

# Cliente

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
