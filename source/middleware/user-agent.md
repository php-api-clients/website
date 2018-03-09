---
layout: default
title: User Agent Middleware
---

# User Agent Middleware

The user agent middleware takes care of setting the user agent header on each outgoing request. For performance 
considerations the results of each different set of options passed into the middleware are cached. Otherwise a strategy 
might perform blocking I/O and block all the non-blocking I/O.

## Installation

To install via [Composer](http://getcomposer.org/), use the command below, it will automatically detect the latest version and bind it with `^`.

```
composer require api-clients/middleware-user-agent 
```

## Strategies

This middleware ships with two build in strategies for the user agent header.

### STRING

The string strategy lets you fully control the contents of the user agent header:

```php
use ApiClients\Foundation\Transport\Options as TransportOptions;
use ApiClients\Middleware\UserAgent\Options as UserAgentMiddlewareOptions;
use ApiClients\Middleware\UserAgent\UserAgentMiddleware;
use ApiClients\Middleware\UserAgent\UserAgentStrategies;

$transportOptions = [
    TransportOptions::MIDDLEWARE => [
        UserAgentMiddleware::class,
    ],
    TransportOptions::DEFAULT_REQUEST_OPTIONS => [
        UserAgentMiddleware::class => [
            UserAgentMiddlewareOptions::STRATEGY => UserAgentStrategies::STRING,
            UserAgentMiddlewareOptions::USER_AGENT => 'User agent header contents',
        ],
    ],
],
```

### PACKAGE_VERSION

The package version strategy takes a package name and retrieves it's installed version and when available homepage 
address and combines that into a header like: 
`vendor/package_name v1.2.3 (https://example.com/) powered by PHP API Clients https://php-api-clients.org/`

```php
use ApiClients\Foundation\Transport\Options as TransportOptions;
use ApiClients\Middleware\UserAgent\Options as UserAgentMiddlewareOptions;
use ApiClients\Middleware\UserAgent\UserAgentMiddleware;
use ApiClients\Middleware\UserAgent\UserAgentStrategies;

$transportOptions = [
    TransportOptions::MIDDLEWARE => [
        UserAgentMiddleware::class,
    ],
    TransportOptions::DEFAULT_REQUEST_OPTIONS => [
        UserAgentMiddleware::class => [
            UserAgentMiddlewareOptions::STRATEGY => UserAgentStrategies::PACKAGE_VERSION,
            UserAgentMiddlewareOptions::PACKAGE => 'PACKAGE_NAME',
        ],
    ],
],
```

## Options

- `PACKAGE` The package name for the `PACKAGE_VERSION` strategy.
- `STRATEGY` Which strategy to use, pass class name must implement `UserAgentStrategyInterface` or else it will be ignored.
- `USER_AGENT` The contents of the user agent header to be used with the `STRING` strategy.
