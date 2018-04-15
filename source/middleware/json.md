---
layout: default
title: JSON Middleware
---

## Installation

To install via [Composer](http://getcomposer.org/), use the command below, it will automatically detect the latest version and bind it with `^`.

```
composer require api-clients/middleware-json   
```

## AcceptJsonMiddleware

Adds the `Accept` header with `application/json` as value.

```php
use ApiClients\Middleware\Json\AcceptJsonMiddleware;

$transportOptions = [
    TransportOptions::MIDDLEWARE => [
        AcceptJsonMiddleware::class,
    ],
],
```

## JsonDecodeMiddleware

Decodes a response containing a `JSON` payload, the body has a `getParsedContents` method which results the 
parsed `JSON` body.

```php
use ApiClients\Middleware\Json\JsonDecodeMiddleware;

$transportOptions = [
    TransportOptions::MIDDLEWARE => [
        JsonDecodeMiddleware::class,
    ],
],
```

## JsonEncodeMiddleware

Encodes a request body to `JSON` when the body implements `ParsedContentsInterface`, also adds the 
corresponding `Content-Type` header.

```php
use ApiClients\Middleware\Json\JsonEncodeMiddleware;

$transportOptions = [
    TransportOptions::MIDDLEWARE => [
        JsonEncodeMiddleware::class,
    ],
],
```
