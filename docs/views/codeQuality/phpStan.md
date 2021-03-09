# PHPStan

PHPStan focuses on finding errors in your code without actually running it. 

## Installation

The installation and configuration of the package are detailed below

### Composer
```	
composer require --dev nunomaduro/larastan
```
In composer.json the following script should be added
```
"phpstan": "vendor/bin/phpstan analyse -c phpstan.neon --memory-limit=2G --no-progress"
```
Then run composer update.

### PhpStorm

In PhpStorm’s preferences php quality tools menu

PhpStorm > Languages & Frameworks > PHP > Quality Tools

Point to phpstan executable located at 

vendor > bin > phpstan

Then click on the validate button.

The configuration of phpstan is stored in phpstan.neon located at the root of the project folder.

<a class="link" href="https://drive.google.com/file/d/1FTWPnyTh1tjNQpM3jmT3bMyVrm1ZSUn6/view?usp=sharing" target="_blank">PhpStan config</a>

In the inspection options the config file should be selected.


### References
<a class="link" href="https://github.com/nunomaduro/larastan" target="_blank">Larastan github</a>   
<a class="link" href="https://www.jetbrains.com/help/phpstorm/using-phpstan.html" target="_blank">Phpstorm docs</a> 
