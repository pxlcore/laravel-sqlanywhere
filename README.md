#Laravel SQLAnyWhere

Adds an Sybase driver to Laravel 5.5, usable with Fluent and Eloquent.

## Attention
The latest version only works with Laravel 5.5 and higher. For lower
version use [version 1.4.1](https://github.com/emericklaw/laravel-sqlanywhere/tree/v1.4.1).

##Todo
    - Migrate integration is not 100%
    - Find bugs


##Installation

Add `emericklaw/laravel-sqlanywhere` as a requirement to `composer.json`:

```javascript
{
    "require": {
        ...
        "emericklaw/sql-anywhere-client": "dev-master",
        "emericklaw/laravel-sqlanywhere": "dev-master"
    },
    "repositories": [
        {
            "type": "package",
            "package": {
                "name": "emericklaw/sql-anywhere-client",
                "version": "dev-master",
                "dist": {
                    "url": "https://github.com/emericklaw/sql-anywhere-client/zipball/master",
                    "type": "zip"
                },
                "autoload": {
                    "psr-0": { "emericklaw": "src/" }
                }
            }
        },
        {
            "type": "package",
            "package": {
                "name": "emericklaw/laravel-sqlanywhere",
                "version": "dev-master",
                "dist": {
                    "url": "https://github.com/emericklaw/laravel-sqlanywhere/zipball/master",
                    "type": "zip"
                },
                "autoload": {
                    "psr-0": { "emericklaw\\SQLAnywhere": "src/" }
                }
            }
        }
    ],
}
```

Update your packages with `composer update` or install with `composer install`.

Once Composer has installed or updated your packages you need to register
LaravelODBC and the package it uses (extradb) with Laravel itself.
Open up `config/app.php` and find the providers key towards the bottom.


 Add the following to the list of providers:
```php
emericklaw\SQLAnywhere\SQLAnywhereServiceProvider::class,
```

You won't need to add anything to the aliases section.


##Configuration

The login parameters could be set inside the `.env` file.
```php
DB_SQLA_HOST     = hostname
DB_SQLA_PORT     = 2638
DB_SQLA_SERVER   = dbdemo
DB_SQLA_DATABASE = dbname
DB_SQLA_USERNAME = dbuser
DB_SQLA_PASSWORD = dbpwd
```

Just add a new array to the `connections` array in `config/database.php`.

```php
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
]
```

Don't forget to update your default database connection.
