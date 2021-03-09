# PHP CS Fixer

PHP-CS-Fixer stands for PHP Coding Standards Fixer.

Php CS Fixer fixes the code to follow standards as PSR-1, PSR-2, etc., or other community driven. 

## Installation

The installation and configuration of the package are detailed below

### Composer
```	
composer require --dev friendsofphp/php-cs-fixer
```
In composer.json the following script should be added 
```
"php-cs-fixer": "php-cs-fixer --config=./.php_cs"
```
Then run composer update.

### PhpStorm

In PhpStorm’s preferences php quality tools menu 

PhpStorm > Languages & Frameworks > PHP > Quality Tools

Point to php-cs-fixer located at 

vendor > friendsofphp > php-cs-fixer > php-cs-fixer

Then click on the validate button. In case a permission error is encountered , a permission fix of the vendor folder with the chmod console command is needed.

Laravel code styling standard follows mainly PSR-2. 

However the community tailored a preset for Laravel which can be downloaded from [laravel preset](https://drive.google.com/file/d/1oBJC9BFEEE-mQPMJ2O90bBnn8T0XQLTD/view?usp=sharing).

The preset file should be renamed to .php_cs and placed at the root of the Laravel project.

In the php cs fixer inspection options choose custom as ruleset and point to the file .php_cs
