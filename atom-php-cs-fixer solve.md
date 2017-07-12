# Fix Atom IDE's PHP-CS-Fixer error

### 1. Install Composer 
[https://getcomposer.org/doc/00-intro.md#installation-linux-unix-osx](https://getcomposer.org/doc/00-intro.md#installation-linux-unix-osx)

`curl -sS https://getcomposer.org/installer | php`

`mv composer.phar /usr/local/bin/composer`

### 2. Install PHP-CS-Fixer 
[https://github.com/FriendsOfPHP/PHP-CS-Fixer](https://github.com/FriendsOfPHP/PHP-CS-Fixer)

`curl http://get.sensiolabs.org/php-cs-fixer.phar -o php-cs-fixer`

`sudo chmod a+x php-cs-fixer`

`sudo mv php-cs-fixer /usr/local/bin/php-cs-fixer`
