---
layout: default
title: Initial Response Timer Middleware
---

# Initial Response Timer Middleware

The Initial Response Timer Middleware times how long it takes before the response initial
response headers are in. 

## Installation

To install via [Composer](http://getcomposer.org/), use the command below, it will automatically detect the latest version and bind it with `^`.

```
composer require api-clients/middleware-timer-response   
```

## Usage

When adding the middleware to the transport options middleware list it will time how 
long before response headers are received. The result is added to the response object 
as the `X-Middleware-Timer-Response` header.

```php
use ApiClients\Foundation\Transport\Options as TransportOptions;
use ApiClients\Middleware\Timer\Response\Middleware;

$transportOptions = [
    TransportOptions::MIDDLEWARE => [
        Middleware::class,
    ],
],
```
