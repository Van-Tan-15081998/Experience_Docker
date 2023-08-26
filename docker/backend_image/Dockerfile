# Sử dụng hình ảnh php:8.2-apache làm hình ảnh cơ sở
FROM php:8.2-apache

ENV APACHE_DOCUMENT_ROOT /var/www/html/public

RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf
RUN sed -ri -e 's!/var/www/!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/apache2.conf /etc/apache2/conf-available/*.conf

# Cài đặt các extension và phần mềm bổ sung cần thiết
RUN apt-get update && apt-get install -y \
    vim \
    git \
    unzip \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Cài đặt tiện ích Composer
RUN curl -s https://getcomposer.org/installer | php && \
    echo "export PATH=${PATH}:/var/www/vendor/bin" >> ~/.bashrc && \
    mv composer.phar /usr/local/bin/composer

RUN apt-get update && apt-get install -y \
    gcc \
    libfreetype6-dev \
    libjpeg-dev \
    libmcrypt-dev \
    libpng-dev \
    make \
    && docker-php-ext-configure gd \
    && docker-php-ext-install -j$(nproc) gd

RUN curl -sL https://deb.nodesource.com/setup_20.x | bash - \
    && apt-get update && apt-get install -y \
    nodejs

RUN a2enmod rewrite

RUN docker-php-ext-install pdo pdo_mysql

# Mở cổng 8000 để ứng dụng Laravel chạy trên
#EXPOSE 8000

# Lệnh mặc định khi container khởi chạy
#CMD ["php", "artisan", "serve", "--host=0.0.0.0", "--port=8000"]