# Git en cmd

## Git workflow
### Hacer 'push'

```sh
# CAMBIAR A LA BRANCH QUE QUIERES MODIFICAR
git checkout [BRANCH]

# DEFINIR RUTA DESDE DONDE HAY QUE MODIFICAR
git add .

# INTRODUCIR LOS CAMBIOS EN GIT CON UN MENSAJE
git commit -m "[MESSAGE]"

# DESCARGAR Y SINCRONIZAR CON EL REPOSITORIO
git pull

# SUBIR LOS CAMBIOS AL REPOSITORIO (GITHUB)
git push
```

## Git workflow
### Hacer 'merge'

```sh
# CAMBIAR A LA BRANCH PRINCIPAL QUE QUIERES UNIFICAR
git checkout [MAIN-BRANCH]

# AGREGAR BRANCH A LA PRINCIPAL
git merge [MY-BRANCH]

# ..CONTINUAR CON WORKFLOW DE 'PUSH'
```

# Git en Visual Studio Code

## Visual Studio Code
### Hacer 'push'

- Click al 3er icono del menu lateral izquierdo de git
- Click en icono 'Checkout a la izquierda del menu inferior
- Seleccionar branch del desplegable (**checkout**)
- Click a 'Sincronizar', siguiente al icono 'Checkout'
- Escribir mensaje de cambios sobre los archivos modificados
- Click en icono 'Commit' sobre el mensaje (**add + commit**)
- De nuevo click en 'Sincronizar' (**pull + push**)

## Visual Studio Code
### Hacer 'merge'

- Click en icono 'Checkout a la izquierda del menu inferior
- Seleccionar branch del desplegable (**checkout**)
- F1 + 'git merge'
