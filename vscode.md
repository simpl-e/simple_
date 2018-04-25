## vscode
### Configuración

Configuración web y php para vscode:

* Copiar las configuraciones del archivo **settings.json** del respositorio **simpl-e/vscode** con: **F1** + **Open User Settings**
* Para hacer efectiva cualquier modificación, se recommienda cerrar y abrir vscode 

## JS - formato
### Beautify

Plugin **Beautify**

## JS - código
### eslint

ejecutar:
```
npm install -g eslint
npm install -g eslint-config-standard
npm install -g eslint-plugin-html
npm install -g eslint-plugin-node
npm install -g eslint-plugin-promise
npm install -g eslint-plugin-standard
```

Guardar archivo '.eslintrc.js' global en:
* ~/.eslintrc *(unix)*
* C:\Users\username\.eslintrc *(windows)*

## PHP - formato
### PHP Intellisense

* Plugin auto-completado en php: **PHP IntelliSense**
* Plugin links a librerías en 'use': **PHP Intellisense - Crane**

## PHP - código
### PHP Code Sniffer

plugin para aviso y corrección de errores php: **php cs fixer**  
(ha resultado no dar problemas en windows)
```sh
composer global require squizlabs/php_codesniffer
```

Añadir los 'php-cs-fixer.*' de 'settings.json' +
```json
"php-cs-fixer.executablePathWindows": "C:/Users/[USUARIO]/AppData/Roaming/Composer/vendor/bin/phpcs.bat"
```

## Git
### Visualización información git en código

* Buscar e instalar plugin "**GitLens**"
* Para habilitar/deshabilitar que el plugin añada títulos con agrupaciones de código modificar "gitlens.codeLens.enabled"

## Markdown
### Estandarización de archivos 'README.md'

Plugin **markdownlint**

## Bonus
### Iconos más llamativos en el arbol de proyectos

Plugin **vscode-icons**

---

## Bonus
### Mostrar árbol de archivos

* Instalar plugin "**Custom CSS and JS**"
* En 'F1' + 'User Settings' añadir:

```json
"vscode_custom_css.imports": [
    "https://gist.githubusercontent.com/samdenty99/b96f4df576d05cb123248f8ebfa899b6/raw/d46a5de9959823d2d806d5f01d6fd20fdce676c3/styles.css"
],
```
Ignorar aviso:  
"Your Code installation appears to be corrupt. Please reinstall."

#### En caso de usar interfaz blanca:

```json
"vscode_custom_css.imports": [
    "https://gist.githubusercontent.com/ogardiazabal/39f8d70b9dd5858a067c4b70bffb9b2e/raw/b36bae86652bbee10be6bc16b8f2abeaf386c3d2/styles.css"
],
```
