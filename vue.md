# Vue2
## Arquitectura y ubicación de archivos

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

# Vistas y componentes
## Plantilla de ejemplo de un componente Vue
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

# Carga dinámica de vista Vue
##  Se descarga el archivo antes de montar Vue
``` js
require(["vue!" + url], function (view) {
  new Vue(view).$mount('#app > *:first-child');
});
```

# Carga dinámica de Componente
## El componente se inicializa antes de su descarga
``` js
Vue.component('modal', function(resolve){
  require(['vue!components/modal.html'], resolve);
});
```

# Crear filtro global
## El filtro se podrá usar en cualquier componente
``` js
Vue.filter('lowerCase', function(txt){
    return t.charAt(0).toUpperCase() + t.slice(1);
});
```
