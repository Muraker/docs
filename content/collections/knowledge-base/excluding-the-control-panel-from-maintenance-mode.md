---
title: 'Excluding the control panel from maintenance mode'
intro: '[Laravel''s maintenance mode](https://laravel.com/docs/configuration#maintenance-mode) is a great way to notify visitors that your site is down but will be shortly. But what if you still want to get into the control panel? Here''s how.'
template: page
stage: 4
id: 4f480db2-f80b-4b97-905c-b946f94c544d
---
## Overview

When your site is in Laravel's [maintenance mode](https://laravel.com/docs/configuration#maintenance-mode), a custom view will be displayed for all requests into your site. This makes it easy to "disable" your site while it is updating or when you are performing maintenance. The logic for this mode is handled in the default middleware.

To enable maintenance mode, run the `down` Artisan command:

```bash
php artisan down
```

And to disable maintenance mode, run the reverse `up` Artisan command:

```bash
php artisan up
```

## Excluding URLs

URLs that should remain "up" while in maintenance mode can be defined in your `app/Http/Middleware/CheckForMaintenanceMode.php` file. Assuming your control panel uses the default `/cp` URL, use the following config to exclude it:

```php
// app/Http/Middleware/CheckForMaintenanceMode.php

protected $except = [
    '/cp',
    '/cp/*'
];
```
