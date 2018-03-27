---
layout: default
title: Request ID Middleware
---

# Request ID Middleware

The request ID middleware adds a unique request ID header to each requests so it can be tracked for debugging later on.

## Installation

To install via [Composer](http://getcomposer.org/), use the command below, it will automatically detect the latest version and bind it with `^`.

```
composer require api-clients/middleware-request-id  
```

## Usage

This middleware ships with two build in strategies for generating a random ID. Namely 
`RandomBytesStrategy` and `Uuid4Strategy`. Both can be use by setting their FQCN as the 
`STRATEGY` option:

```php
use ApiClients\Foundation\Transport\Options as TransportOptions;
use ApiClients\Middleware\RequestId\Options as RequestIdMiddlewareOptions;
use ApiClients\Middleware\RequestId\RequestIdMiddleware;
use ApiClients\Middleware\UserAgent\RequestIdStrategy\RandomBytesStrategy;

$transportOptions = [
    TransportOptions::MIDDLEWARE => [
        RequestIdMiddleware::class,
    ],
    TransportOptions::DEFAULT_REQUEST_OPTIONS => [
        RequestIdMiddleware::class => [
            RequestIdMiddlewareOptions::STRATEGY => RandomBytesStrategy::class,
        ],
    ],
],
```

## Options

- `STRATEGY` Which strategy to use, pass class name must implement `RequestIdStrategyInterface` or else it will be ignored.
- `USER_AGENT` The contents of the user agent header to be used with the `STRING` strategy.
