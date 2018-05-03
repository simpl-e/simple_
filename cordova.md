# Phonegap Cordova

## Instalación

https://cordova.apache.org/
```sh
# DOWNLOAD
npm install -g cordova
# CREATE PROJECT
cordova create [PATH]
# ADD PLATFORM
cordova platform add android
# TEST
cordova run android --device
```

## Crear App que solo redirecciona a una web
```js
// INICIAR WEB EN UN IFRAME
$("#iframe").on('load', function () {
    var webApp = $("iframe")[0].contentWindow;

    // INYECTAR CORDOVA EN EL IFRAME    
    webApp.cordova = window.cordova;

    // ABRIR LINKS EXTERNOS '_blank' EN EL NAVEGADOR FUERA DE LA APP
    webApp.$('a[target=_blank]').click(function (e) {
        e.preventDefault();
        webApp.cordova.InAppBrowser.open($(this).attr('href'), '_system');
    });
});
```

---
