FROM php:7.4-cli

MAINTAINER Samuele "DonCallisto" Lilli <samuele.lilli@gmail.com>

RUN apt-get update \
    && apt-get install -y \
    git \
    zlib1g-dev \
    libzip-dev \
    unzip

RUN mkdir /user \
    && useradd -d /user -s /bin/bash user \
    && chown user /user

WORKDIR /var/codemotion2021

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php -r "if (hash_file('sha384', 'composer-setup.php') === '756890a4488ce9024fc62c56153228907f1545c228516cbf63f885e036d37e9a59d27d63f46af1d4d07ee0f76181c7d3') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" \
    && php composer-setup.php \
    && php -r "unlink('composer-setup.php');"

RUN cp composer.phar /usr/bin

ENTRYPOINT ["/bin/bash"]

USER user