# laravel-echo-server

## Iniciar servidor websocket
### Server NodeJs para Laravel Echo Broadcast con socket.io

**`laravel-echo-server start`** junto a 'laravel-echo-server.json'

## Cliente websocket
### navegador / nodejs

Sin 'Authorization' correcta solo conectará a canales **públicos**  
La 'Authorization' se resuelve en la ruta definida en:  
**"laravel-echo-server.json"**  

```js
// HEADER 'Authorization' = 'Basic' || 'Bearer'
var echo = new Echo({
    broadcaster: 'socket.io',
    host: domain + ':6001',
    client: require('socket.io-client'),
    auth: {
        headers: {
            'Authorization': token
        }
    }
});

// EJEMPLOS DE CONEXIÓN A CANALES KPRIMA
echo.channel('messages')
    .listen('MessageEvent', function (data) {
        // DATOS ENTRANTES AL CANAL PÚBLICO
    });

echo.private('kprima.' + kprimaId)
    .listen('KprimaEvent', function (data) {
        // DATOS ENTRANTES AL CANAL PRIVADO
    });

echo.join("kprimas")
    .listen('KprimasEvent', function (data) {
        // DATOS ENTRANTES AL CANAL PRESENCIAL
    })
    .here(function (users) {
        // LISTA DE USUARIOS INICIAL
    })
    .joining(function (user) {
        // EVENTO DE ENTRADA DE CLIENTE
    })
    .leaving(function (user) {
        // EVENTO DE SALIDA DE CLIENTE
    });
```

## SSL
### Configuración en "/etc/https/conf.d/ssl.conf"

```conf
<VirtualHost *:443>
    SSLProxyEngine on
    # solve 'pass request body failed'
    SSLProxyCheckPeerCN off
    SSLProxyCheckPeerName off
    #
    ProxyPass /socket.io/ws/ wss://localhost:6001/socket.io/
    ProxyPassReverse /socket.io/ws/ wss://localhost:6001/socket.io/
    ProxyPass /socket.io/ https://localhost:6001/socket.io/
    ProxyPassReverse /socket.io/ https://localhost:6001/socket.io/
</VirtualHost>
```

Inicializar
```sh
supervisord -c /etc/supervisord.conf
```

Par debuguear el proceso:
```sh
tail /var/log/echoserver.log -f
```

---

# Supervisor (Process Control System)

## Mantener servicios siempre funcionando
### Instalación

```sh
sudo apt/yum install -y supervisor
systemctl start supervisord
```

## Websocket server
### Configurar Daemon

Configuración en `/etc/supervisord.conf`:
```sh
[...]

[program:laravel-echo-server]
directory=[directorio de 'laravel-echo-server.json']
command=/usr/bin/laravel-echo-server start
autostart=true
autorestart=true
user=centos
redirect_stderr=true
```

## Cliente NodeJS
### Configurar Daemon

Configuración en `/etc/supervisord.conf`:
```sh
[...]

[program:laravel-echo-client]
directory=[directorio del 'cliente websocket']
command=node websocket.js
autostart=true
autorestart=true
user=centos
redirect_stderr=true
```

[(ver más en 'Cliente websocket')](##Cliente websocket)

# Laravel

## Setup manual
### 

```sh
sudo apt/yum install nodejs
```

AllowOverride All

```sh
cp /var/www/html/api/kprima/settings.backup.js /var/www/html/api/kprima/settings.js
```

## Http API
### Obtener datos de los canales (Guzzle)

```php
$client->get("[..]:6001/apps/".[APP_ID]."/channels", [
    'headers' => [
        'Authorization' => 'Bearer '.[CLIENTS.KEY]
    ],
    'json' => [
        'appId' => [CLIENTS.APPID]
    ]
]);
```

(solo se puede obtener lista de usuarios en canales 'presence')

# Debugging

## DEBUG
### Para hacer debug en el lado del servidor

https://github.com/tlaverdure/laravel-echo-server/issues/225
```sh
DEBUG=* /usr/bin/laravel-echo-server start
```

## REDIS
### Validar conexiones 'laravel-echo-server' y sockets 'presence'

```sh
redis-cli -a [PASSWORD]
> monitor
```

---

# Archivos de configuration

## Servidor websocket
### Archivo de configuración "laravel-echo-server.json"

```php
{
    "authHost": "https://127.0.0.1",
    "authEndpoint": "[API]/public/broadcasting/auth",
    "clients": [
        {
            "appId": "[...]",
            "key": "[...]"
        }
    ],
    "database": "redis",
    "databaseConfig": {
        "redis": {
            "port": "6379",
            "host": null
        }
    },
    "devMode": true,
    "host": null,
    "port": "6001",
    "protocol": "https",
    "socketio": {"wsEngine": "ws"},
    "sslCertPath": "[...].crt",
    "sslKeyPath": "[...].key",
    "sslCertChainPath": "[...]/DigiCertCA.crt",
    "sslPassphrase": "",
    "apiOriginAllow": {
        "allowCors": true,
        "allowOrigin": "*",
        "allowMethods": "GET, POST",
        "allowHeaders": "Origin, Content-Type, X-Auth-Token, X-Requested-With, Accept, Authorization, X-CSRF-TOKEN, X-Socket-Id"
    }
}
```
