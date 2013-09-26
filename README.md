magari-workshops
================

PHP VM with pre-installed cookbooks and vendors (dev).

/*Änderung für nixe 2*/


After cloning do the following:

    cd magari-workshops
    vagrant up
    vagrant ssh
    cd /vagrant
    composer install
    app/console doctrine:database:create

The Symfony application is now accessable via [http://localhost:8080/](http://localhost:8080/) and phpMyAdmin via [http://localhost:8080/phpmyadmin/](http://localhost:8080/phpmyadmin/) (MySQL username: root, no password).

Composer and PHPUnit are installed. Unit tests can be executed via:

    cd /vagrant
    vendor/bin/phpunit -c app
