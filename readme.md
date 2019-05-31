![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)

# URL Shortener

Shorten URL's using your own domain

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

```
Laravel 5.8+ (Not tested in previous versions)
```

### Installing

1) Download it into your Laravel app using composer

```
composer require cedaesca/urlshortener
```

2) Run the migrations.
````
php artisan migrate
````

3) Publish the config file
````
php atisan vendor:publish
````

## Customizing the URL's code length

1) Go to the config file located on `config/cedaesca/URLShortener.php`

2) Change the `length` value for that of your preference.

## URLShortener Facade

You have to add the URLShortener facade to your controller:
````php
use cedaesca\URLShortener\Facades\URLShortener;
````

Then you'll have access to the `create` and `redirect` methods.

## Shorten URL's

Use the `create` static method to shorten a given URL. This method receives the request as argument and returns an instance of the model if was successfully created or false if not:

````php
URLShortener::create(Request $request);
````

## Redirecting users

Use the `redirect`static method to redirect users to the target url's. This method receives the URL code parameter as argument.

````php
Route::get('/r/{code}', 'UrlShortenerController@redirect')->name('rthis');
````
````php
return URLShortener::redirect($code);
````

## Default redirect

If the code given as argument is invalid, the `redirect` method will redirect the user to a default route. Change this from the config file.

1) Go to the config file located on `config/cedaesca/URLShortener.php`

2) Change the `defaultRedirect` value for that of your preference.
