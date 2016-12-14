FROM  ubuntu:14.04

ADD ./sources.list /etc/apt/sources.list

RUN locale-gen en_US.UTF-8

ENV LANGUAGE=en_US.UTF-8
ENV LC_ALL=en_US.UTF-8
ENV LC_CTYPE=UTF-8
ENV LANG=en_US.UTF-8
ENV TERM xterm

# Install "software-properties-common" (for the "add-apt-repository")
RUN apt-get update && apt-get install -y \
    software-properties-common


# Install PHP-CLI 7, some PHP extentions and some useful Tools with APT
RUN apt-get update && apt-get install -y --force-yes \
        php5-dev \
        libcurl4-openssl-dev \
        libedit-dev \
        libssl-dev \
        libxml2-dev \
        xz-utils \
        sqlite3 \
        libsqlite3-dev \
        git \
        curl \
        vim \
        nano

# Clean up, to free some space
RUN apt-get clean


# Add bin folder of composer to PATH.
RUN echo "export PATH=${PATH}:/var/www/tp/vendor/bin" >> ~/.bashrc

# Install Composer
RUN curl -s http://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer

# Load xdebug Zend extension with phpunit command
RUN echo "alias phpunit='php -dzend_extension=xdebug.so /var/www/tp/vendor/bin/phpunit'" >> ~/.bashrc


# Source the bash
RUN . ~/.bashrc

# Clean up
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

WORKDIR /var/www/tp

# Install optional software
ARG INSTALL_PRESTISSIMO=false
RUN if [ "$INSTALL_PRESTISSIMO" = true ] ; then \
        composer global require "hirak/prestissimo:^0.3"; \
    fi
