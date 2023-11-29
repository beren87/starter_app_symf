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
Suivre la [documentation](https://symfony.com/doc/current/frontend/encore/css-preprocessors.html) pour activer Sass/SCSS dans un projet.

Dans le fichier webpack.config.js, décommenter la ligne suivante : ,
.enableSassLoader() ,
Puis exécuter : ,
```bash
npm install sass-loader@^13.0.0 sass --save-dev
```
## Renommer dans "assets/styles/app.js"
import './styles/app.scss';

## Renommer dans "assets/styles/"
app.scss

## Postprocesseur - PostCSS et Autoprefixing
Suivre la [documentation](https://symfony.com/doc/current/frontend/encore/postcss.html) pour activer PostCSS dans un projet.

Dans le fichier webpack.config.js, ajouter la ligne suivante sous .enableSassLoader() :,
.enablePostCssLoader()
Puis exécuter :,
```bash
npm install postcss-loader@^7.0.0 --save-dev
```

## Autoprefixer
```bash
npm install autoprefixer --save-dev
```
Créer un fichier à la racine du projet:,
postcss.config.js,
Puis insérer le code suivant:,
module.exports = {
    plugins: [
        require('autoprefixer')
    ]
},




