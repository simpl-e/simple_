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

# ..CONTINUAR CON WORKFLOW NORMAL DE 'PUSH'
```

## Git workflow
### Eliminar / Revertir un merge

```sh
# OBTENER ID DEL COMMIT DEL MERGE
git log

# DEVOLVER 1 MERGE DESDE ESE COMMIT
git revert -m 1 [MERGE COMMIT]

# HACER UN NUEVO PUSH
git push
```

## Git workflow
### Revertir un pull en producción

https://stackoverflow.com/questions/5815448/how-to-undo-a-git-pull/5815626

```sh
# DEVUELVE TANTOS PULL COMO EL NÚMERO INDIQUE
git reset --hard HEAD@{1}
```

#### Si quieres volver a un commit específico del historial:

```sh
# BUSCA EL COMMIT DE LA LISTA QUE TE INTERESA
git log
# DEVUELVE EL CÓDIGO AL COMMIT
git checkout [COMMIT]
```

## .gitignore
### Eliminar archivos ignorados del repositorio

Debe hacerse en todos los branch para evitar bugs al moverse entre branches
```sh
git rm --cached <file>
```

## Cache
### Mantener passwords guardadas al hacer git pull

```sh
git config --global credential.helper cache
```

---

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

# Aplicaciones

## SourceTree (Escritorio)
### Cliente Git

- Útil para administrar y visualizar el estado de las 'branches'
- Útil para deshacer cambios en github con '`push --force`'

## vscode
### plugins

#### GitLens:
Anotaciones en el código sobre quien y cuando realizó cambios

#### Git History:
Visualiza gráficamente los cambios en el 'tree' y compararlos

## Eliminar un commit en SourceTree
### Los cambios eliminados no se podrán recuperar

- Click secundario + 'Reset current branch to this commit'
- Hacer Push con el checkbox 'Force Push' activado

# Debug

- '**`git status`**' es siempre un buen comienzo
