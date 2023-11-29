# Installation du projet Symfony
## Prérequis 
```bash
php -v
```
```bash
composer -v
```
```bash
node -v
```
```bash
npm -v
```
```bash
symfony check:requirements
```
## Initialisation de votre projet avec la version 6.3
```bash
symfony new votre_projet --version="6.3.*"--webapp
```

# Configuration de Webpack Encore avec Symfony

## Installation du bundle Symfony Webpack Encore
```bash
composer require symfony/webpack-encore-bundle
```
## Installation des dépendances dans le package.json
```bash
npm install
```
## Lancement automatique de Webpack
```bash
npm run dev
```
## Préprocesseur - Utilisation de Sass SCSS
Suivez la [documentation](https://symfony.com/doc/current/frontend/encore/css-preprocessors.html) pour activer Sass/SCSS dans votre projet.

Dans le fichier `webpack.config.js`, décommentez la ligne suivante : 
```javascript
.enableSassLoader() 
```
Puis exécutez : 
```bash
npm install sass-loader@^13.0.0 sass --save-dev
```
## Renommer dans "assets/styles/app.js"
import './styles/app.scss';

## Renommer dans "assets/styles/"
app.scss

## Postprocesseur - PostCSS et Autoprefixing
Suivez la [documentation](https://symfony.com/doc/current/frontend/encore/postcss.html) pour activer PostCSS dans votre projet.

Dans le fichier `webpack.config.js`, ajoutez la ligne suivante sous .enableSassLoader() :
```javascript
.enablePostCssLoader()
```
Puis exécutez :
```bash
npm install postcss-loader@^7.0.0 --save-dev
```

## Autoprefixer
```bash
npm install autoprefixer --save-dev
```
Créez un fichier à la racine du projet:
 `postcss.config.js`

Puis insérez le code suivant:
```javascript
module.exports = {
    plugins: [
        require('autoprefixer')
    ]
}
```
Dans le fichier `package.json`, ajoutez à la liste des `devDependencies`:
```javascript
"browserslist": ">0.0.1"
```
## Référencer des images
Suivez la [documentation](https://symfony.com/doc/current/frontend/encore/copy-files.html#referencing-image-files-from-a-template) pour copier et référencer des images dans votre projet.

Créez un dossier `images` dans `assets`.
Dans `webpack.config.js`, sous 
```javascript
.enableSassLoader()
.enablePostCssLoader()
```
copiez le code suivant:
```javascript
 .copyFiles({
        from: './assets/images',
        to: 'images/[path][name].[hash:8].[ext]',
    })
```
Puis exécutez : 
```bash
npm install file-loader@^6.0.0 --save-dev
```
# Installation de Bootstrap 5
Suivez la [documentation](https://symfony.com/doc/current/frontend/encore/bootstrap.html) pour installer Bootstrap 5.

```bash
npm i bootstrap@5.3.2
```
```bash
npm i --save bootstrap @popperjs/core
```
```bash
npm install jquery @popperjs/core --save-dev
```

Dans le fichier `app.js`:  
```javascript
const $ = require('jquery');
require('bootstrap');
document.addEventListener('DOMContentLoaded', function () {
    $('[data-toggle="popover"]').popover();
    $('[data-toggle="tooltip"]').tooltip();
});
```
puis en dessous :
```javascript
// or, specify which plugins you need :
import { Tooltip, Toast, Popover } from 'bootstrap';
```
Dans le fichier `app.scss`:  
```javascript
// Import all of Bootstrap's CSS by default
@import "~bootstrap/scss/bootstrap";
```