Speciality Distribution Wrapper
===============================

Wrap our Speciality Distribution with custom directories we are pleased to have.


Refer to https://github.com/Ecodev/typo3-cms-speciality-distribution


Installation
============

::

	# Download via composer
	composer create-project ecodev/typo3-cms-speciality-distribution htdocs dev-master
	cd htdocs
	composer update

Once done, here are the usually steps that I do:

Edit file `htdocs/.gitignore` and add all files to the git repository.

::

	cd htdocs
	nano .gitignore

	-> /typo3conf/ext/*
	-> !/typo3conf/ext/speciality
	-> remove LocalConfiguration + AdditionalConfiguration

	cd ..
	git add .

Next step is to configure the Virtual Host and local host name in /etc/hosts if developping locally.
After that open the browser pointing to the Virtual Host and follow the instructions. Eventually, install the Speciality distribution.
To finish the install, make sure to:

* Remove "speciality_distribution" and "speciality" from composer.json
* Remove the DB credientials from LocalConfiguration and add them into ../configuration/Settings.php
* Configure RealURL in the EM with this path `typo3conf/ext/speciality/Configuration/RealUrl/Configuration.php`
* Add sys_domain on the root page and test http://domain.tld/sitemap.xml
* Add at the end of robots.txt: Sitemap: http://www.domain.tld/sitemap.xml
* Truncate table `sys_news`

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
