# composer を動かすためだけのイメージ。
# 依存解決の結果が利用側とズレないよう、PHP は利用側の実行環境に合わせて固定している。
FROM php:8.4.25-cli

RUN apt-get update \
    && apt-get install -y --no-install-recommends git unzip libonig-dev libzip-dev \
    && docker-php-ext-install mbstring zip \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

COPY --from=composer:2 /usr/bin/composer /usr/local/bin/composer

ENV COMPOSER_ALLOW_SUPERUSER=1
WORKDIR /app
