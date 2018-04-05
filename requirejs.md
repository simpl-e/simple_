## Implementación de Require.js
### Ejemplo de configuración de carga (main.js)

``` js
require.config({
    waitSeconds: 0, // QUITAR TIMEOUT DEL REQUIRE
    paths: {
        // PLUGINS REQUIRE.JS
        css: 'https://[CDN]/css',
        vue: 'https://[CDN]/vue',
        // LIBRERÍAS
        jquery: "https://[CDN]/jquery",
        Vue2: "https://[CDN]/vue",
        bootstrap: "https://[CDN]/bootstrap"
    },
    config: {
        // PERMITE CORS EN REQUIRES "text!"
        text: {
            useXhr: function () {
                return true;
            }
        }
    },
    // DEFINICIÓN DE DEPENDENCIAS
    shim: {
        bootstrap: ["jquery"]
    },
    // EXCLUSIONES (EXCEPCIONAL)
    exclude: ['require-css/normalize']
});

// DEFINICIÓN DE UN MÓDULO
define('Vue', ["Vue2"], function (vue) {
    window.Vue = vue;
    return vue;
});

// DESCARGA DE ARCHIVOS ANTES DE EJECUTAR
require([
    "../src/boot/router", // CÓDIGO .JS
    "css!styles/styles.css", // ESTILOS .CSS
    "jquery", "Vue" // LIBRERÍAS
], function (router) {
    router();
});

// LIBRERÍAS QUE PUEDEN CARGAR ASÍNCRONAMENTE
require([
    "bootstrap"
]);
```

## Compilador 'r.js' en 'gulp'
### Compilador de bundle de los CDN para App's

``` js
// CONFIGURACIÓN TIPO DE 'r.js'
var config = {
    mainConfigFile: 'main.js',
    modules: [{
        name: 'main',
        create: true
    }]
};

// EJECUCIÓN GULP PARA COMPILAR
gulp.task('bundle', function () {
    rjs.optimize(config);
});
```

## Definir .js como módulo Object
### Funciona como archivo de datos

``` js
// 'shirt.js':
define({
    color: "black",
    size: "unisize"
});
```

## Definir .js como módulo Función
### Permite ejecutar código al cargar el módulo

``` js
// 'shirt.js':
define(function () {
    // EJECUCIÓN DE CÓDIGO AQUÍ

    return {
        color: "black",
        size: "unisize"
    }
});
```

## Definir .js como módulo Clase
### Permite reutilizar el archivo para usos diferentes

``` js
// 'shirt.js':
define(function () {
    return function () {
        // EJECUCIÓN DE CÓDIGO AQUÍ

        return {
            color: "black",
            size: "unisize"
        }
    }
});
```

## Carga de módulos 'define()' con Require.js
### Ejemplo de configuración (main.js)

``` js
require(["shirt"], function(Shirt){
    var shirt = new Shirt(); // EJEMPLO DE CLASE
});
```

## Carga de 'require.js' en 'index.html'
### Toda la definición de librerías debe ir en main.js

``` html
<html>
    <head>
        <!-- REQUIRE.JS CON CDN's -->
        <script data-main="main" src="require.js"></script>
        <!-- REQUIRE.JS CON BUNDLE -->
        <script src="main-built.js"></script>
    </head>
</html>
 ```

