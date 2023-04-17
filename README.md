# laravel-debugbar-memory
[![License](https://poser.pugx.org/sustartx/laravel-debugbar-memory/license)](https://packagist.org/packages/sustartx/laravel-debugbar-memory)

Add detailed memory usage measurement for code blocks in [Laravel Debugbar](https://github.com/barryvdh/laravel-debugbar)

## Note

This package was cloned from [Amir Irfan's iffifan/laravel-debugbar-memory repo](https://github.com/iffifan/laravel-debugbar-memory). I made some improvements by cloning because I saw that he did not contribute to the project for a long time. Thank him for publishing this package.

## Installation

```shell
composer require sustartx/laravel-debugbar-memory --dev
```

#### or add composer.json

```
    "require-dev": {
        "sustartx/laravel-debugbar-memory": "*"
    },
    "extra": {
        "laravel": {
            "dont-discover": [
                "sustartx/laravel-debugbar-memory"
            ]
        }
    },
```

#### AppServiceProvider.php

```
// Debugbar
if (env('DEBUGBAR_ENABLE', false)){
    // $this->app->register(\Barryvdh\Debugbar\ServiceProvider::class);
    $this->app->register(\SuStartX\MemoryDebugbar\Providers\MemoryDebugbarServiceProvider::class);
    // $this->app->alias('Debugbar', \Barryvdh\Debugbar\Facades\Debugbar::class);
}
```

## Usage

After successful installation you should see `Memory` tab in your Debugbar

![Screenshot](https://i.ibb.co/hHHbnVZ/debugbar-memory.jpg)

### Measuring memory usage of a code block

Let's calculate memory usage of a while loop with helper methods

```php
    start_memory_measure('Some Loop');
    $a = 0;
    $b = 'X';
    while ($a < 10000000) {
        $b .= 'X';
        ++$a;
    }
    stop_memory_measure('Some Loop');
```
Memory calculation will be updated like this:

![Screenshot](https://i.ibb.co/gryfYkY/debugbar-memory-code.jpg)

## Disable

Just add 
```php
        'memory_details'  => false, //Display memory details
```
in ``config/debugbar.php``

