# Laravel PubSub Queue

[![Build Status](https://travis-ci.org/kainxspirits/laravel-pubsub-queue.svg?branch=master)](https://travis-ci.org/kainxspirits/laravel-pubsub-queue)
[![StyleCI](https://styleci.io/repos/131718560/shield)](https://styleci.io/repos/131718560)

This package is a Laravel queue driver that uses the [Google PubSub](https://github.com/GoogleCloudPlatform/google-cloud-php-pubsub) service.

## Installation

You can easily install this package with [Composer](https://getcomposer.org) by running this command :

```bash
composer require ankurgoels/laravel-pubsub-queue
```

If you disabled package discovery, you can still manually register this package by adding the following line to the providers of your `config/app.php` file :

```php
Kainxspirits\PubSubQueue\PubSubQueueServiceProvider::class,
```

## Configuration

Add a `pubsub` connection to your `config/queue.php` file. From there, you can use any configuration values from the original pubsub client. Just make sure to use snake_case for the keys name.

You can check [Google Cloud PubSub client](http://googleapis.github.io/google-cloud-php/#/docs/cloud-pubsub/master/pubsub/pubsubclient?method=__construct) for more details about the different options.

```php
'pubsub' => [
    'driver' => 'pubsub',
    'queue' => env('PUBSUB_QUEUE', 'default'),
    'project_id' => env('PUBSUB_PROJECT_ID', 'your-project-id'),
    'retries' => 3,
    'request_timeout' => 60,
    'keyFile' => json_decode(file_get_contents(storage_path('keys/pubsub.json')), true),
],
```

## Testing

You can run the tests with :

```bash
vendor/bin/phpunit
```

## License

This project is licensed under the terms of the MIT license. See [License File](LICENSE) for more information.
