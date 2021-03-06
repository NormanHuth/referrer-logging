```bash
composer require muetze42/referrer-logging
```

#### For file method

```php
// config/filesystems.php
    'disks' => [
    //...
        'referrer-cache' => [
            'driver' => 'local',
            'root' => storage_path('app/referrer-cache'),
        ],
    //...
    ],
```
---
The artisan command to delete the file memory:
```bash
referrer-logging:cleanup
```

#### Publish the config:
```bash
php artisan vendor:publish --provider="NormanHuth\ReferrerLogging\ReferrerLoggingServiceProvider" --tag=config
```

---

#### Publish the migrations:
```bash
php artisan vendor:publish --provider="NormanHuth\ReferrerLogging\ReferrerLoggingServiceProvider" --tag=migrations
```

#### Add middleware to app/Http/Kernel.php for all routes
```php
    protected $middleware = [
        //..
        \NormanHuth\ReferrerLogging\Http\Middleware\ReferrerLog::class,
        //...
];
```
