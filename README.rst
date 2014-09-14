Speciality Distribution Wrapper
===============================

Wrap our Speciality Distribution with custom directories we are pleased to have.


Refer to https://github.com/Ecodev/typo3-cms-speciality-distribution


Installation
============

::

	# Download via composer
	composer create-project ecodev/typo3-cms-speciality-wrapper speciality.distribution --repository-url=https://github.com/Ecodev/typo3-cms-speciality-distribution.git --prefer-source --keep-vcs


Phing build
===========

`Phing`_: is a build system for PHP and is used to replicate the website between production and development and do some low level tasks.
Also make sure to have a look at the `Frontend Development Workflow`_ which integrates itself with this build system
Some instructions how to get started with this development workflow::

	# Head to the home
	cd bootstrap_package

	# Installation of Composer is not already done
	curl -sS https://getcomposer.org/installer | php

	# Optional: install it globally. You may need to reload your terminal.
	mv composer.phar /usr/local/bin/composer

	# Install dependencies
	# If Composer is installed globally "composer install" is enought
	# This will basically installed Phing locally for this website.
	php composer.phar install

	./bin/phing
	-> read carefully instruction. A file must be generated in `configuration`.

	./bin/phing help

	[echo] ---------------------------------------------
	[echo] Handle cache
	[echo] ---------------------------------------------
	[echo] phing clear_cache     - Flush cached files along with database cache (depth 3)
	[echo] phing warmup          - Call Frontend to generate necessary files
	[echo]
	[echo] phing c               - Clear cache, depth 1: typo3temp/Cache files
	[echo] phing cc              - Clear cache, depth 2: all typo3temp files
	[echo] phing ccc             - Clear cache, depth 3: all typo3temp files + database
	[echo]
	[echo] ---------------------------------------------
	[echo] Import website locally
	[echo] ---------------------------------------------
	[echo] phing show            - Show Phing current configuration
	[echo] phing import-dump     - Fetch the database and build it again locally for TYPO3 6.0
	[echo] phing htaccess        - Fetch the htaccess from the remote server
	[echo] phing symlink         - Create symlinks to the core, current value "/t3core/typo3_src-6.1"
	[echo] phing uploads         - Fetch uploads folder
	[echo] phing fileadmin       - Fetch fileadmin
	[echo] phing user_upload     - Fetch user_upload folder
	[echo]
	[echo] phing d               - import-dump
	[echo] phing initialize6     - import-dump, htaccess, symlink, uploads, fileadmin
	[echo] phing reset           - import-dump, clear_cache, warmup

.. _Frontend Development Workflow:
.. _Phing: http://www.phing.info/



Behavior-driven development
===========================

The main purpose of `behavior-driven development`_ (abbreviated BDD) is to ensure the feature set is there taking
the point of view of a User (largely speaking). It is also referred as
"Acceptance tests". Acceptance criteria should be written in terms of scenarios and implemented as classes:
Given [initial context], when [event occurs], then [ensure some outcomes].

See it in practice::

	cd tests

	curl http://getcomposer.org/installer | php
	php composer.phar install

	./bin/behat

Feature tests files are to be found into ``tests/features``.

.. _behavior-driven development: http://en.wikipedia.org/wiki/Behavior-driven_development
Making your own introduction package