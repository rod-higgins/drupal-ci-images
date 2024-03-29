# Drupal 9/10 CI Docker image for Gitlab CI

## Details

[Drupal 9/10](https://www.drupal.org) ci image based on official [docker Drupal](https://github.com/docker-library/drupal)
with some Php/NodeJs tools needed for CI or Local Build/Test/Lint.

Used with project [Gitlab CI Drupal](https://github.com/rod-higgins/gitlab-ci-drupal).

* Fork from [juampynr/drupal8ci](https://hub.docker.com/r/juampynr/drupal8ci/~/dockerfile/)
* Based on [Drupal official image](https://github.com/docker-library/drupal), added
  * [Node.js](https://nodejs.org/en/) + [Yarn](https://yarnpkg.com)
  * [Robo CI](http://robo.li)
  * [Phpqa](https://github.com/EdgedesignCZ/phpqa) including:
    * [Phpmetrics](https://www.phpmetrics.org)
    * [Phploc](https://github.com/sebastianbergmann/phploc)
    * [Phpcs](https://github.com/squizlabs/PHP_CodeSniffer)
    * [Phpmd](https://phpmd.org)
    * [Pdepend](https://pdepend.org)
  * [Security checker](https://github.com/fabpot/local-php-security-checker)
  * [phpstan](https://github.com/phpstan/phpstan)
  * [phpstan-drupal](https://github.com/mglaman/phpstan-drupal)
  * [Drupal Coder](https://www.drupal.org/project/coder)
  * Mariadb (MySQL) and PostgreSQL client
  * Php with extensions:
    * intl xsl mysqli bcmath calendar sockets pcntl opcache exif ftp imagick xdebug
  * [jq](https://stedolan.github.io/jq/)
  * [bc](https://www.gnu.org/software/bc/)
  * [xsltproc](http://xmlsoft.org/xslt/xsltproc.html)
  * [gettext](http://xmlsoft.org/xslt/xsltproc.html)

## Basic usage (local)

All images are based on official [docker Drupal](https://github.com/docker-library) images managed by Composer.

To use with a local Drupal 9/10 managed by Composer, mount your Drupal on `/opt/drupal/`

## Build

CI variable `CI_DO_RELEASE`, default to `1` to push to Docker hub.

```bash
make prepare
```

## Tests

Tests with [infratest](https://testinfra.readthedocs.io/en/latest/).

```bash
docker run -it --rm rodhiggins/gitlab-ci-drupal:1.x-dev-9.3 /tests/prepare-tests.sh && pytest
```
