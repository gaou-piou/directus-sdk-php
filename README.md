<p align="center">
<img src="https://s3.amazonaws.com/f.cl.ly/items/3Q2830043H1Y1c1F1K2D/directus-logo-stacked.png" alt="Directus Logo"/>
</p>

# Directus SDK for PHP
For PHP driven applications, use this SDK to more easily communicate with your Directus managed database.

[![Build Status](https://img.shields.io/travis/directus/directus-sdk-php.svg?style=flat-square)](https://travis-ci.org/directus/directus-sdk-php)
[![Scrutinizer](https://img.shields.io/scrutinizer/g/directus/directus-sdk-php.svg?style=flat-square)](https://scrutinizer-ci.com/g/directus/directus-sdk-php)
[![Scrutinizer Coverage](https://img.shields.io/scrutinizer/coverage/g/directus/directus-sdk-php.svg?style=flat-square)](https://scrutinizer-ci.com/g/directus/directus-sdk-php/?branch=master)

## Work In Process.

## Install

Via Composer

``` bash
$ composer require directus/directus-sdk
```

## Usage

### Database connection
``` php
require 'vendor/autoload.php';

$config = [
    'driver' => 'pdo_mysql',
    'host' => 'localhost',
    'user' => 'root',
    'pass' => 'root',
    'name' => 'directus'
];
$connection = new \Directus\SDK\Connection($config);
$tableGateway = new \Directus\SDK\BaseTableGateway('articles', $connection);

$articles = $tableGateway->fetchItems();

foreach($articles as $article) {
    echo '<h2>'.$article->title.'</h2>';
}
```

### Directus Hosted

```php
require 'vendor/autoload.php';

$client = new \Directus\SDK\Client('user-token', [
    // the sub-domain in your instance url
    'instance_key' => 'user--instance'
]);

$results = $client->fetchItems('articles');

$articles = $results->rows;

foreach($articles as $article) {
    echo "<h2>".$article->title."</h2>";
}
```

### Your own server

```php
require 'vendor/autoload.php';

$client = new \Directus\SDK\Client('user-token', [
    // Directus API Path without its version
    'base_url' => 'http://directus.local/api/',
    'version' => 1 // Optional - default 1
]);

$results = $client->fetchItems('articles');

$articles = $results->rows;

foreach($articles as $article) {
    echo "<h2>".$article->title."</h2>";
}
```
