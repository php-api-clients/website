---
layout: default
title: Oauth 1 Middleware
---

# Oauth 1 Middleware

The oauth 1 middleware signs all outgoing requests with a oauth 1 `Authorization` header.

## Installation

To install via [Composer](http://getcomposer.org/), use the command below, it will automatically detect the latest version and bind it with `^`.

```
composer require api-clients/middleware-oauth1 
```

## Usage

```php
use ApiClients\Middleware\Oauth1\Oauth1Middleware;
use ApiClients\Middleware\Oauth1\Options as Oauth1Options;
use ApiClients\Tools\Psr7\Oauth1\Definition;

$transportOptions = [
    TransportOptions::MIDDLEWARE => [
        Oauth1Middleware::class,
    ],
    TransportOptions::DEFAULT_REQUEST_OPTIONS => [
        Oauth1Middleware::class => [
            Oauth1Options::CONSUMER_KEY    => new Definition\ConsumerKey('CONSUMER_KEY'),
            Oauth1Options::CONSUMER_SECRET => new Definition\ConsumerSecret('CONSUMER_SECRET'),
            Oauth1Options::ACCESS_TOKEN    => new Definition\AccessToken('ACCESS_TOKEN'),
            Oauth1Options::TOKEN_SECRET    => new Definition\TokenSecret('TOKEN_SECRET'),
        ],
    ],
],
```
