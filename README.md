## Etapes à effectuer pour l'installation d'un projet drupal

composer create-project drupal/recommended-project "DRUPAL PROJECT NAME" 
cd "DRUPAL PROJECT NAME" && php -d memory_limit=256M web/core/scripts/drupal quick-start demo_umami
composer install --no-dev

## Base de données

1. Sign in to phpMyAdmin as the root user.
2. Click Users, and then click Add user.
   Note: You can use the root user credential as well.
3. In the User name field, enter the username that you want to use.
4. In the Host field, select Local, which is a more secure setting, unless you'll be accessing the database with this user from another server.
5. Enter or generate a password for the user.
6. In the Database for User section, select Create database with same name and grant all privileges.
7. Make sure you select utf8mb4_unicode_ci or utf8mb4_general_ci for COLLATION.
   Note: The difference between the two collations is how much faster they are in character comparison and sorting. utf8mb4_general_ci is slightly faster however utf8mb4_unicode_ci is more accurate for a wider range of characters. If you are unsure use utf8mb4_unicode_ci.
   Note: If you do not have the option to select COLLATION during this routine, you can change it later. Select your database from the Databases menu, then click Operations. There you will find a section for Collation where you can select the desired setting.
8. Click Go to create the user.

## Utiliser l'installeur drupal

1. Aller sur l'URL localhost/core/install.php
2. Suivre les étapes (le site en anglais permet de ne pas télécharger directement les traductions en français).

## Surcharger un thème de base

Créer un dossier à l'intérieur du dossier web : themes/custom/nomDuTheme.
Copier et coller à cet endroit 
