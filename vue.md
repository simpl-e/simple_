## Proyecto Vue2
### Arquitectura basada en require.js

- **src**
  - **boot**: Archivos .js y .css de carga inicial
    - **exceptions.js**: manejador excepciones axios
    - **router.js**: enrutador automático
    - **utils.js**: funciones globales
  - **modules**: archivos Vue (.html)
    - **views**: Vistas funcionalmente independientes
      - **home**: Vista inicial + archivos extra
        - **home.html**
    - **components**: Componentes repetitivos
- **.htaccess**: Permitir solo .html y .js
- **gulpfile.js**: En caso de querer bundle (App)
- **index.html**: Carga de require.js y Vue
- **main.js**: librerías CDN para require.js
- **package.json**: solo dev (gulp, etc..)

## Vistas y componentes
### Plantilla de ejemplo de un componente Vue

``` html
<template>
  <div id="view_example">
    <!-- CONTENIDO HTML -->
    Hola {{name | capitalize}}
    <div v-for="tech in techs">{{tech}}</div>
  </div>
</template>

<script>
  // DEFINIMOS EL .js COMO MÓDULOS AMD
  define({
    template: template,
    data: function(){
      return {
        // DATOS
        name: oscar
      }
    },
    computed: {
      // DATOS QUE SE RECONSTRUYEN 'ON DEMAND'
      // NO PUEDEN CONTENER ARGUMENTOS
      techs: function(){
        return this.techs.sort();
      }
    },
    methods: {
      // MÉTODOS
      add: function(tech){
        this.techs.push(tech);
      }
    },
    filters: {
      // FILTROS
      capitalize: function (t) {
        return t.charAt(0).toUpperCase() + t.slice(1);
      }
    }
  });
</script>

<style>
  #view_example .class {
    /* CSS */
  }
</style>
```

## Carga dinámica de una vista Vue
###  Se descarga el archivo antes de montar Vue

``` js
require(["vue!" + url], function (view) {
  new Vue(view).$mount('#app > *:first-child');
});
```

## Carga dinámica de un Componente
### El componente se inicializa antes de su descarga

``` js
Vue.component('modal', function(resolve){
  require(['vue!components/modal.html'], resolve);
});
```

## Crear un filtro global
### El filtro se podrá usar en cualquier componente

``` js
Vue.filter('lowerCase', function(txt){
  return t.charAt(0).toUpperCase() + t.slice(1);
});
```

## Vue Modal
### Uso del modal.html dinámico de simple_

``` js
require(["vue!modal.html"], function (Modal) {
  // INICAR MÓDULO REQUIRE.JS COMO CLASE
  var modal = new Modal();
  // OBTENER DATA DEL COMPONENTE PARA ALTERAR
  component.data = component.data();
  // INYECTAR DATA EXTRA
  component.data.options = options;
  // INICIALIZAR COMPONENTE VUE
  var vm = new Vue(modal);
  // INSERTAR COMPONENTE EN EL HTML
  var $div = $("<div>").appendTo("body")[0];
  vm.$mount($div);
  // PERSONALIZAR ESTILOS CSS
  $(vm.$el).find(".div").css('padding', 0);
  // DEFINIR COMPONENTE VUE CONTENIDO
  vm.page = "modules/views/login/login.html";
});
```

## Vue independiente
### Uso Vue sin usar enrutador

```html
<head>
    <style>
        /* ESTILOS DEL VIEW */
    </style>
    <script data-main="../src/main" src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.3.5/require.js"></script>
</head>

<body>
    <div id='view_home'>
        <!-- evita que se vea código vue antes de compilar -->
        <template>
            <!-- HTML -->
        </template>
    </div>

    <script>        
        //LLAMAR AQUÍ EN VEZ DEL ENRUTADOR AL FINALIZAR LA CARGA
        window.router_override = function () {            
            window.vm = new Vue({
                el: "#view_home",
                // RESTO DEL VUE
            });
        };
    </script>
</body>
```
