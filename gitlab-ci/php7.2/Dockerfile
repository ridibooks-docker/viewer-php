FROM ubuntu:bionic
LABEL maintainer="KyungJun Park <kyungjun.park@ridi.com>"

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update --fix-missing && apt-get install --no-install-recommends -y \
    libmcrypt-dev \
    curl \
    apt-utils \
    software-properties-common \
    gettext-base \
    python3 \
    python3-pip \
    python3-setuptools \
    python3-wheel \
    git \
    libmcrypt-dev \
    python3-pip \
    unzip \
    zlib1g-dev \
    php7.2 \
    php7.2-cli \
    php7.2-xml \
    php7.2-curl \
    php7.2-mbstring \
    php7.2-gmp \
    gnupg

# Install composer
RUN php -r "readfile('http://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer

## Setting timezion
ENV TZ Asia/Seoul

RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && \
    echo $TZ > /etc/timezone
RUN apt-get install -y tzdata
RUN rm /etc/localtime
RUN dpkg-reconfigure -f noninteractive tzdata

# Install nodejs
RUN curl -sL https://deb.nodesource.com/setup_11.x | bash - && \
	apt-get install -y nodejs

RUN pip3 install awscli --upgrade
RUN npm install --global redoc-cli