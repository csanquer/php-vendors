php vendors - Simple script to manage vendors from git or svn
=============================================================

[![Project Status](http://stillmaintained.com/csanquer/php-vendors.png)](http://stillmaintained.com/csanquer/php-vendors)  For PHP >= 5.3 projects, you should use [Composer](http://getcomposer.org/) now.

php vendors is a simple dependencies manager based on original Symfony 2.0 Standard Edition vendors script.

This script should be used to manage dependencies from git or subversion repositories for PHP projects with PHP <= 5.2.

Installation / Usage
--------------------

1. Copy `bin` directory in your project root directory

2. create a deps file in your project root directory 

        [default]
            vendor= vendor       ; default vendor dir
            target=              ; default target dir
            externals= false     ; default externals config to retrieve dependencies proper VCS externals
        [<dependency name>]
            <git|svn>=<url>      ; type of repository and url
            version=             ; version to use
            vendor=              ; dependency specific vendor dir , overwrite default vendor dir
            target=              ; dependency specific target dir , overwrite default target dir
            externals=           ; dependency specific externals config , overwrite default externals config

  dependencies are saved into `<vendor>/<name>` or `<vendor>/<target>` if `<target>` is not empty

  example with a Symfony 1.4 project :

        [default]
            vendor = lib/vendor
            target =
            externals = false
        [symfony]
            git=https://github.com/symfony/symfony1.git
            version=v1.4.10
        [sfGuardPlugin]
            svn=http://svn.symfony-project.com/plugins/sfGuardPlugin/branches/1.3/
            vendor=plugins
        [sfPropelORMPlugin]
            git=https://github.com/propelorm/sfPropelORMPlugin.git
            vendor=plugins
            externals = true

3. run `bin/vendors` script (.gitignore is updated)

  - To install

        bin/vendors install

  - To reinstall

        bin/vendors install --reinstall

  - To lock versions and write a deps.lock file

        bin/vendors lock

  - To update to latest versions

        bin/vendors update

Requirements
------------

PHP >= 5.0

Authors
-------

Fabien Potencier <fabien@symfony.com> for original Symfony 2.0 vendors script <br />
Charles Sanquer <charles.sanquer@spyrit.net> <br />

License
-------

php vendors is licensed under the MIT License - see the LICENSE file for details
