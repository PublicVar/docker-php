FROM drupaldocker/php-dev:7.1-alpine-cli
MAINTAINER drupal-docker

RUN apk add --no-cache mysql-client openssh-client rsync \
  && cd ~ \
  && git clone --depth 1 --branch master https://github.com/drush-ops/drush.git drush \
  && cd drush \
  && composer install \
  && rm -f /usr/local/bin/drush \
  && ln -s ~/drush/drush /usr/local/bin/drush \
  && drush core-status -y \
  && drush core-init -y

CMD ["drush", "core-cli"]