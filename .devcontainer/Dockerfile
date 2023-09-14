FROM debian:bullseye

ARG USERNAME=librenms
ARG USER_UID=1000
ARG USER_GID=1000

# Create the user
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && apt-get update \
    && apt-get install -y sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

# install requirements
RUN apt update \
    && apt install -yq apt-transport-https lsb-release ca-certificates wget \
    && wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg \
    && echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/sury-php.list \
    && apt update \
    && apt install -yq \
       acl \
       curl \
       fping \
       git \
       graphviz \
       imagemagick \
       mariadb-client \
       mariadb-server \
       mtr-tiny \
       nginx-full \
       nmap \
       php-cli \
       php-curl \
       php-fpm \
       php-gd \
       php-gmp \
       php-json \
       php-mbstring \
       php-mysql \
       php-snmp \
       php-xml \
       php-zip \
       python3-dotenv \
       python3-pymysql \
       python3-redis \
       python3-setuptools \
       python3-systemd \
       python3-pip \
       rrdtool \
       snmp \
       snmpd \
       whois \
    && apt -yq autoclean

ENV SHELL /bin/bash
USER $USERNAME
