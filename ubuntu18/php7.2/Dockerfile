FROM ubuntu:bionic

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update --fix-missing && apt-get install --no-install-recommends -y \
    software-properties-common \
    gettext-base \
    python3-pip \
    python3-setuptools \
    python3-wheel \
    jq \
    php7.2 \
    php7.2-cli \
    php7.2-curl \
    php7.2-mbstring \
    php7.2-mysql \
    php7.2-apcu \
    php7.2-zip \
    php7.2-xml \
    php7.2-xdebug \
    php7.2-gmp \
    apache2 \
    libapache2-mod-php7.2 \
    git \
    ssh

# Install composer
RUN php -r "readfile('http://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer

## Setting timezion
ENV TZ Asia/Seoul

RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && \
    echo $TZ > /etc/timezone
RUN apt-get install -y tzdata
RUN rm /etc/localtime
RUN dpkg-reconfigure -f noninteractive tzdata

## Clean up
RUN apt-get remove -y software-properties-common \
    && apt-get clean \
    && apt-get autoremove -y \
    && rm -rf /var/lib/apt/lists/*