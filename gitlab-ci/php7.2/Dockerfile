FROM php:7.2
LABEL maintainer="KyungJun Park <kyungjun.park@ridi.com>"

RUN apt-get update && apt-get install -yqq \
    git \
    libmcrypt-dev \
    python3 \
    python3-pip \
    unzip \
    zlib1g-dev \
    gnupg

# Install composer
RUN php -r "readfile('http://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer

# Install nodejs
RUN curl -sL https://deb.nodesource.com/setup_11.x | bash - && \
	apt-get install -y nodejs

RUN docker-php-ext-install bcmath pdo_mysql zip
RUN pecl install apcu xdebug && docker-php-ext-enable apcu xdebug
RUN pip3 install awscli --upgrade
RUN npm install --global redoc-cli