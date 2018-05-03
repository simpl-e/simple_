## Authentificate
### Laravel Login

TODO

## JWT (axios)
### Login

``` js
axios.post(api + "login", data, {
    auth: {
        username: user,
        passowrd: pass
    }
}
```

## JWT (axios)
### Reutilización del token de cookie

``` js
var token = getCookie('Authorization');
axios.post(url, data, {
    headers: {
        'Authorization': 'Bearer ' + token,
    }
}
```

## JWT (axios)
### Archivo "boot/exceptions.js"

``` js
axios.interceptors.response.use(function (resp) {
    return resp;
}, function (error) {
    if (401 === error.response.status) {

        //LOGIN CON VUE MODAL
        require(["vue!modal.html"], function (M) {
            var modal = new M();
            var vm = new Vue(modal);

            var div = $("<div>").appendTo("body");
            vm.$mount(div[0]);

            vm.page = "login.html";
        });
        return;

    } else {
        var msg = "<b>" + err + "</b>: "
            + jqxhr.responseText;
        $.notify(msg, {type: 'danger'});
    }
});
```

## JWT (guzzle)
### Basic Authorization

**Guzzle** transforma header **auth** en: **`btoa($user:$pass);`**

``` php
new GuzzleHttp\Client([
    'cookies' => true, // SI NECESITA MANTENER LOGIN
    'auth': [$user, $password]
]);
```
