# Vue
```
<template>
  <div id="view_example">
    <!-- HTML VIEW -->
  </div>
</template>

<script>
  define({
    template: template,
    data: function(){
      return {
        //datos
      }
    },
    computed: {
      example_computed: function(){
        //datos que se reconstruyen 'on demand'
        //no pueden contener argumentos
      }
    },
    methods: {
      example_method: function(argument){
        //método
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
