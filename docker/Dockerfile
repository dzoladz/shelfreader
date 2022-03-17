FROM ubuntu:20.04

ENV DB_USERNAME=db_user
ENV DB_PASSWORD=db_password
ENV DB_USERNAME_2=db_user_2
ENV DB_PASSWORD_2=db_password_2

# ------------------------------------------------------------------
# Use BASH, not SH
# ------------------------------------------------------------------
SHELL ["/bin/bash", "-c"]

# ------------------------------------------------------------------
# Update Package Cache and Set Timezone
# ------------------------------------------------------------------
RUN apt-get update

RUN apt-get install -y tzdata
ENV TZ "America/New_York"
RUN echo "America/New_York" > /etc/timezone \
    && dpkg-reconfigure --frontend noninteractive tzdata

# ------------------------------------------------------------------
# Install Packages and Dependencies
# ------------------------------------------------------------------
RUN DEBIAN_FRONTEND='noninteractive' apt-get install -y --no-install-recommends \
    # -- General Utilities --
    git \
    nano \
    # -- Apache --
    apache2 \
    libapache2-mod-php \
    # -- Maria DB --
    mariadb-server \
    # -- PHP | 20.04 repos point to 7.4 --
    php \
    php-gd \
    php-xml \
    php-zip \
    php-mysql \
    php-cli \
    php-curl \
    php-mbstring

# ------------------------------------------------------------------
# Install Composer Globally
# https://getcomposer.org/doc/faqs/how-to-install-composer-programmatically.md
# ------------------------------------------------------------------
WORKDIR /
COPY ./docker/install-composer.sh install-composer.sh
#RUN chmod +x /install-composer.sh \
#    && /install-composer.sh \
#    && mv composer.phar /usr/local/bin/composer
