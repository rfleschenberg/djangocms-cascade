.. _impatient:

=================
For the Impatient
=================

This HowTo gives you a quick instruction on how to get a demo of **djangocms-cascade** up and
running. It also is a good starting point to ask questions or report bugs, since its backend is
used as a fully functional reference implementation, used by the unit tests of project.


Create a Python Virtual Environment
===================================

To keep environments separate, first create a *virtualenv*.

.. code-block:: bash

	#!/bin/sh
	sudo pip install --upgrade virtualenv
	virtualenv --distribute --no-site-packages myvirtualenv
	source myvirtualenv/bin/activate
	(myvirtualenv)$


Clone the latest stable releases
================================

Create a temporary file, for instance named requirements.txt, containing these entries:

.. code-block:: guess

	Django==1.9.6
	Django-Select2==5.8.4
	Pillow==3.2.0
	Unidecode==0.4.18
	django-classy-tags==0.7.2
	django-cms==3.2.3
	django-filer==1.2.0
	django-treebeard==4.0
	django-polymorphic==0.9.2
	django-reversion==1.10.1
	django-sass-processor==0.3.4
	django-sekizai==0.9.0
	djangocms-bootstrap3==0.1.1
	-e git+https://github.com/jrief/djangocms-cascade.git#egg=djangocms-cascade
	djangocms-text-ckeditor==2.8.1
	easy-thumbnails==2.3
	html5lib==0.9999999
	jsonfield==1.0.3
	six==1.9.0

and install them into your environment:

.. code-block:: bash

	pip install -r requirements.txt

this will take a few minutes. After the installation finished, change into the folder containing
the demo application, install missing CSS and JavaScript files, initialize the database and
create a superuser:

.. code-block:: bash

	cd $VIRTUAL_ENV/src/djangocms-cascade
	bower install --require
	cd examples
	./manage.py migrate --settings=bs3demo.settings
	./manage.py createsuperuser --settings=bs3demo.settings
	./manage.py runserver --settings=bs3demo.settings

Point a browser onto http://localhost:8000/ and log in as the super user. Here you should be able
to add your first page. Do this by changing into into **Structure** mode on the top of the page.
Now a heading named ``MAIN CONTENT`` appears. This heading symbolizes a **djangoCMS** Placeholder.

Locate the plus sign right to the heading and click on it. From its context menu select
**Container** located in the section **Bootstrap**:

|add-container|

.. |add-container| image:: _static/add-container.png

This brings you into the editor mode for a Bootstrap container. To this container you may add one or
more Bootstrap **Rows**. Inside these rows you may organize the layout using some Bootstrap
**Columns**.

Please proceed with the detailled explanation on how to use the
:ref:`Bootstrap's grid <bootstrap3/grid>` system within **djangocms-cascade**.
