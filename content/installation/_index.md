---
title: "نصب سریع"
date: 2018-12-29T11:02:05+06:00
icon: "ti-panel"
description: "نصب سریع همراه با قالب پیش فرض"
type : "docs"
---




## Installation

You can install the package via composer:

```bash
composer require dpsoft/mehr
```

## Usage

You must also chose a theme. The default theme is novinmodir. Install by:
```bash
composer require dpsoft/mehr-theme-novinmodir
```
Then set `APP_THEME=mehr4-theme-minimal` in `.env` file.

## Breaking changes

### Models

All models namespace except `User` changed from `App` to `Dpsoft\Mehr\Models`:
```php
//deprecated
App\Category::first();

//valid
Dpsoft\Mehr\Models\Category::first();
```
### Widgets

Add namespace `mehr` to widget names: `@widget('mehr::FeatureCourses')`

### Views

#### Core Views
Some of mehr views like `components.seo` must be used with `mehr` namespace:
```blade
//deprecated
@include('component.seo')

//Valid
@include('mehr::component.seo')
```

#### Auth Views

Mehr themes must provide Auth views and publish theme in: `resources/views/auth`.

List of views is:
```
.
├── auth
│   ├── login.blade.php
│   ├── passwords
│   │   ├── confirm.blade.php
│   │   ├── email.blade.php
│   │   └── reset.blade.php
│   ├── register.blade.php
│   └── verify.blade.php
```

This views are laravel/ui packages view. More information at [package documentation.](https://laravel.com/docs/6.x/authentication#included-views)

### Testing

``` bash
composer test
```

## Upgrade to new package system

To rename models namespace in database and other stuffs run command `mehr:upgrade:package`:
```shell script
php artisan mehr:upgrade:package
```

## Facade
The `Mehr` facade could be used with some helper function.

### updateOrNewSetting

To create or update setting in lms you could use `updateOrNewSetting` function:
```php
\Mehr::updateOrNewSetting('site_facebook','@siteAccount','Facebook account...');
```

### persianDate

To show jalalian date from carbon instance, you could use `persianDate` function:
```php
\Mehr::persianDate($post->created_at,'Y/m/d H:i');
```

### Security

If you discover any security related issues, please email sadeghpm@gmail.com instead of using the issue tracker.

## Credits

- [Dpsoft](https://github.com/dpsoft)