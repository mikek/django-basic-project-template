# Django-basic-project-template

This Django project template is customized to our workflow. It can be used
as is or as a starting point to make your own template.

The `bc` branch contains a few specific settings and relies on some internal
tools. For a random stranger the `master` branch is a way to go.

## Make sure you have virtualenvwrapper configured (once)

Install virtualenvwrapper and deps with pip or your packagemanager.

    pip install virtualenvwrapper

Add something like this to .bashrc:

    # virtualenvwrapper
    export PROJECT_HOME=~/Workplace/Sources/web/django
    source /usr/bin/virtualenvwrapper_lazy.sh

Source it or launch a new shell.

## Django project setup

### Start new django project from template

    curl https://raw.githubusercontent.com/mikek/django-basic-project-template/master/create.sh | bash -s yourprojectname

 * adjust files in `requirements` directory
 * edit `settings/_common.py` *INSTALLED_APPS*

Install all dependencies and sync database

    workon yourprojectname
    pip install -r requirements/development.txt
    ./manage.py syncdb

### Integration with optional tools

This template integrates with a few optional tools

#### Fabric's fabfile.py based on webdev-fab project

Included `fabfile.py` has helpful comments.

#### Chef's kitchen to provision a host to be able to run Django project

[django-kitchen](https://github.com/mikek/django-kitchen) project provides
initial kitchen structure and example node configuration. You can place it
anywhere you like.

#### Vagrant setup to work on a project inside a VM

If you are working in a full featured UNIX-like environment with recent version
of Python installed - you can safely remove all Vagrant-related stuff:

    rm -rf Vagrant*

Otherwise, please refer to the included `Vagrantfile.README`.

## Work on existing project

To work on existing project - clone it in the same directory instead
of using project template.

The resulting structure should look like this:

    yourprojectname/
    |-- project/
    |   |-- .git
    |   |-- manage.py
    |   |-- fabfile.py
    [...]
    |   |-- yourprojectname/
    |   |   |-- apps/
    |   |   |-- core/
    |   |   |-- media/
    [...]

## Daily workflow

    workon yourprojectname
    ./manage.py runserver

## Related links

 * [webdev-fab](https://github.com/mikek/webdev-fab)
 * [django-kitchen](https://github.com/mikek/django-kitchen)
 * [Vagrant](http://www.vagrantup.com)
