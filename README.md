## Etapes à effectuer pour l'installation d'un projet drupal

composer create-project drupal/recommended-project "DRUPAL PROJECT NAME" 
cd "DRUPAL PROJECT NAME"
php -d memory_limit=256M web/core/scripts/drupal quick-start demo_umami
composer install --no-dev

## Base de données

1. Aller à localhost/phpadmin
2. Ajouter un compte utilisateur
3. In the User name field, enter the username that you want to use.
4. In the Host field, select Local, which is a more secure setting, unless you'll be accessing the database with this user from another server.
5. Enter or generate a password for the user.
6. In the Database for User section, select Create database with same name and grant all privileges.
7. Make sure you select utf8mb4_unicode_ci or utf8mb4_general_ci for COLLATION.
   Note: The difference between the two collations is how much faster they are in character comparison and sorting. utf8mb4_general_ci is slightly faster however utf8mb4_unicode_ci is more accurate for a wider range of characters. If you are unsure use utf8mb4_unicode_ci.
   Note: If you do not have the option to select COLLATION during this routine, you can change it later. Select your database from the Databases menu, then click Operations. There you will find a section for Collation where you can select the desired setting.
8. Click Go to create the user.

## Utiliser l'installeur drupal

1. Aller sur l'URL localhost/"nomDuProjet"/core/install.php
2. Suivre les étapes (le site en anglais permet de ne pas télécharger directement les traductions en français).
3. Modifier le php.ini en enlevant le ";" aux lignes :
zend_extension=opcache
opcache.enable=1
extension=gd

## Surcharger un thème de base

1. Créer un dossier à l'intérieur du dossier web : themes/custom/nomDuTheme.
2. Copier et coller à cet endroit tous les fichiers du theme starterkit_theme présent dans web>core>themes>starterkit_theme.
3. Renommer starterkit_theme.info.yml en "nomDuTheme".info.yml
4. Renommer starterkit_theme.libraries.yml en "nomDuTheme".libraries.yml
5. Renommer starterkit_theme.theme en "nomDuTheme".theme
6. Mettre dans le fichier "nomDuTheme".info.yml
name: "nomDuTheme"
description: Custom theme edited by Théo Petit
type: theme
core_version_requirement: ^9 || ^10
base theme: stark
package: Custom

libraries: 
  - pizza_theme/global-styling
regions:
  header: Header
  primary_menu: Primary menu
  secondary_menu: Secondary menu
  content: Content
  footer: Footer

7. Mettre dans le fichier "nomDuTheme".libraries.yml
  global-styling:
  version: 1.0
  css:
    theme:
      assets/css/styles.css: {}
  js:
    assets/js/app.js: {}

## Ajout du less au projet

1. Se mettre dans le theme custom puis taper les commandes :
npm init
npm i lessc
npm i less-watch-compiler

2. Ajouter la ligne suivante dans le script du fichier package.json
"less": "lessc-watch sources/less/style.less assets/css/styles.css"

3. Dans le dossier custom/"nomDuTheme", nous devons avoir les dossiers suivants :
- assets > css  (pour le css compilé)
- assets > js   (pour le js compilé)
- img (pour les images)
- sources > js
- sources > less (avoir au moins à l'intérieur un fichier style.less qui fasse des imports des autres fichiers less)
- templates (pour tout ce qui est surcharge html)



