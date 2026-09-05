# GMO Aozora Net Bank Open Api PHP SDK

## About

GMOあおぞらネット銀行について

https://gmo-aozora.com/

GMOあおぞらネット銀行 API開発者ポータルについて

https://api.gmo-aozora.com/ganb/developer/

## Version 
1.0.0

## Requirements
PHP 7.4 and later

## このフォークについて

本家 [gmoaozora/gmo-aozora-api-php](https://github.com/gmoaozora/gmo-aozora-api-php) の fork です。
本家が guzzle 6 系・firebase/php-jwt 5 系に固定しており、いずれも未修正のセキュリティ勧告を抱えたまま
PHP 8 環境で利用できないため、依存を引き上げています。

- guzzle を 7 系へ (`\GuzzleHttp\json_encode()` / `\GuzzleHttp\Psr7\build_query()` の置き換え)
- firebase/php-jwt を 6 系以降へ
- PHP 8.4 で deprecated になった暗黙 nullable 引数に `?` を付与
- `require-dev` を削除 (テストは swagger 生成の空スタブで、PHPUnit 6 で削除された
  `\PHPUnit_Framework_TestCase` を継承しており動作しないため)

API の使い方は本家と同じです。

### 開発

`composer.lock` の更新には同梱の docker 環境を使います。

```console
$ docker compose run --rm composer composer update
```

## Installation

### Composer

To install the bindings via [Composer](http://getcomposer.org/), add the following to `composer.json`:

```
{
  "repositories": [
    {
      "type": "git",
      "url": "https://github.com/gmoaozora/gmo-aozora-api-php.git"
    }
  ],
  "require": {
    "gmoaozora/gmo-aozora-api-php": "*@dev"
  }
}
```

Then run `composer install`

### import the package
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');
```
## Getting Started

### Enviroment
Add the configuration below into your config file

* stg

    conf.json
    ```json
    {
        "AUTH_BASE_URL": "https://stg-api.gmo-aozora.com/ganb/api/auth/v1",
        "JWT_ISSUER": "https://stg-api.gmo-aozora.com/",
        "AUTH_PATH": "/authorization",
        "TOKEN_PATH": "/token",
        "SALT": "PleaseDefineYourself"
    }
    ```
    [Configuration.php - Personal ](./personal/lib/Configuration.php) 
    ```php
        protected $host = 'https://stg-api.gmo-aozora.com/ganb/api/personal/v1';
    ```
    [Configuration.php - Corporate ](./corporate/lib/Configuration.php) 
    ```php
        protected $host = 'https://stg-api.gmo-aozora.com/ganb/api/corporation/v1';
    ```
    [Configuration.php - Webhook ](./webhook/lib/Configuration.php) 
    ```php
        protected $host = 'https://stg-api.gmo-aozora.com/ganb/api/webhook/v1';
    ```

* prod

    conf.json
    ```json 
    {
        "AUTH_BASE_URL": "https://api.gmo-aozora.com/ganb/api/auth/v1",
        "JWT_ISSUER": "https://api.gmo-aozora.com/",
        "AUTH_PATH": "/authorization",
        "TOKEN_PATH": "/token",
        "SALT": "PleaseDefineYourself"
    }
    ```
    [Configuration.php - Personal ](./personal/lib/Configuration.php) 
    ```php
        protected $host = 'https://api.gmo-aozora.com/ganb/api/personal/v1';
    ```
    [Configuration.php - Corporate ](./corporate/lib/Configuration.php) 
    ```php
        protected $host = 'https://api.gmo-aozora.com/ganb/api/corporation/v1';
    ```
    [Configuration.php - Webhook ](./webhook/lib/Configuration.php) 
    ```php
        protected $host = 'https://api.gmo-aozora.com/ganb/api/webhook/v1';
    ```


## API Documents
* [**Auth**](./auth/docs/)
* [**Personal**](./personal/docs/)
* [**Corporate**](./corporate/docs/)
* [**Webhook**](./webhook/docs/)


## Autor

GMO Aozora Net Bank, Ltd. (open-api@gmo-aozora.com)

## Licence

[MIT](https://github.com/gmoaozora/gmo-aozora-api-php/blob/master/LICENSE)