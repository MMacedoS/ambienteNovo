FROM php:7.4-fpm

# Instalar dependências necessárias incluindo a extensão PDO MySQL
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
    && docker-php-ext-install pdo pdo_mysql

# Instalar o Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Adicionar uma configuração personalizada ao php.ini
RUN echo "variables_order=\"EGPCS\"" >> /usr/local/etc/php/conf.d/custom.ini

# Configurar o diretório de trabalho
WORKDIR /var/www/html

# Expor a porta do PHP-FPM
EXPOSE 9000
