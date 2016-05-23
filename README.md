Laravel SQLAnyWhere
============

Adds an Sybase driver to Laravel 5, usable with Fluent and Eloquent.

#Todo
    - Migrate integration is not 100%
    - Find bugs


Installation
============

Add `pxlcore\laravel-sqlanywhere` and `cagartner/sql-anywhere-client` as a requirement to composer.json:

```javascript
{
    "require": {
        "cagartner/sql-anywhere-client": "dev-master",
        "pxlcore/laravel-sqlanywhere": "dev-master"
    }
}
```

Update your packages with `composer update` or install with `composer install`.

Once Composer has installed or updated your packages you need to register
LaravelODBC and the package it uses (extradb) with Laravel itself.
Open up `config/app.php` and find the providers key towards the bottom.


 Add the following to the list of providers:
```php
'Pxlcore\SQLAnywhere\SQLAnywhereServiceProvider',
```

You won't need to add anything to the aliases section.


Configuration
=============

The login parameters could be set inside the .env file.
```
    DB_SQLA_HOST     = hostname
    DB_SQLA_PORT     = 2638
    DB_SQLA_SERVER   = dbdemo
    DB_SQLA_DATABASE = dbname
    DB_SQLA_USERNAME = dbuser
    DB_SQLA_PASSWORD = dbpwd
```

There is no separate package configuration file for LaravelODBC.  You'll just add a new array to the `connections` array in `config/database.php`.

```
        'sqlanywhere' => [
            'host'        => env('DB_SQLA_HOST', 'localhost'),
            'port'        => env('DB_SQLA_PORT', '2638'),
            'dbserver'    => env('DB_SQLA_SERVER', 'dbdemo'),
            'database'    => env('DB_SQLA_DATABASE', 'dbname'),
            'username'    => env('DB_SQLA_USERNAME', 'dbuser'),
            'password'    => env('DB_SQLA_PASSWORD', 'dbpwd'),
            'charset'     => 'utf8',
            'prefix'      => '',
            'auto_commit' => true,
            'persintent'  => false,
```

**Don't forget to update your default database connection.**
