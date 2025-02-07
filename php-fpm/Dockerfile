FROM php:8.2-fpm

# Instalar dependências necessárias
RUN apt-get update && apt-get install -y \
    unzip \
    git \
    libonig-dev \
    libzip-dev \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    libssl-dev \
    mariadb-client \
    cron \
    libxml2-dev \ 
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install -j$(nproc) pdo pdo_mysql zip mbstring opcache dom \ 
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Instalar o Composer
RUN curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer \
    && chmod +x /usr/local/bin/composer

# Adicionar uma configuração personalizada ao php.ini
RUN echo "variables_order=\"EGPCS\"" >> /usr/local/etc/php/conf.d/custom.ini

# Configurar o diretório de trabalho
WORKDIR /var/www/html

# Verificar a versão do Composer após a instalação
RUN composer --version

# Expor a porta do PHP-FPM
EXPOSE 9000
