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
# ADD PLUGINS
cordova plugin add cordova-plugin-whitelist
cordova plugin add cordova-plugin-inappbrowser
# TEST
cordova run android --device
```

## config.xml
```xml
<access origin="[URL]" />
<allow-navigation href="[URL]/*"/>
```

## Crear App que solo redirecciona a una web
```html
<!-- https://stackoverflow.com/a/38325627/2075591 -->
<meta http-equiv="Content-Security-Policy" content="default-src 'self'; frame-src 'self' https://iframe url">

<iframe id="iframe" src="[URL]"></iframe>

<script>
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
</script>
```

---
