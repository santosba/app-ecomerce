FROM php:8.1-fpm
RUN  apt-get update && apt-get install -y zlib1g-dev g++ git libicu-dev zip libzip-dev unzip libpq-dev \
    && docker-php-ext-install intl opcache pdo pdo_pgsql pgsql\
    && pecl install apcu \
    && docker-php-ext-enable apcu \
    && docker-php-ext-configure zip \
    && docker-php-ext-install zip

WORKDIR /var/www/project

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

 RUN curl -sS https://get.symfony.com/cli/installer | bash \
    && mv /root/.symfony5/bin/symfony /usr/local/bin/symfony

# Install Node.js
RUN curl -fsSL https://deb.nodesource.com/setup_18.x | bash - \
    && apt-get install -y nodejs

# Optional: Install Yarn
RUN npm install -g yarn

# Copy application files
COPY . .

# Start PHP-FPM
CMD ["php-fpm"]
