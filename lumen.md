## Instalación
### Laravel/Lumen

```sh
git clone https://github.com/simpl-e/simple_lumen_seed.git
```

Para migrarlo a cualquier versión de laravel o lumen copiar los archivos excepto /public/* y revisar bootstrap/app.php

## Instalación
### Composer (CentOs)

```sh
cd /tmp
curl -sS https://getcomposer.org/installer | php
mv composer.phar /usr/local/bin/composer
```

#### Paquetes laravel/lumen:

```sh
sudo chown -R apache:apache api
cd api
# sin sudo!
/usr/local/bin/composer install
```

## Arquitectura
### Estructura

From https://www.merixstudio.com/blog/laravel-5-tutorial/

- **app**: ubicación de los Model, ORM de la base de datos
    - **HTTP**: relacionado con el acceso a la aplicación desde la web
        - **Controllers**: controlladores, grueso de la app
        - **Middleware**: control de autentificación, etc..
    - **Providers**: carga y gestión de nuestra aplicación
- **bootstrap**: archivos de inicialización de Lumen
- **config**: archivos de configuración de cada plugin
- **public**: todo lo público desde la web
- **routes**: definición de 'resources' genéricos (get,post,put/patch/delete)
- **storage**: donde se guardan archivos 

## Login
### Implementación token JWT incorporado en el proyecto

https://github.com/tymondesigns/jwt-auth/wiki/Installation

## Uso
### Como llamar a la api:

Añade 'public/controller/method' a la url

#### Para testear la api:

[url]/api_test.html

## Auth Middlewares
### Manejo de roles

TODO

## Bonus
### Para añadir clases de uso común

https://stackoverflow.com/a/17091089/2075591  
"Create a 'Libraries' folder inside your app folder"
