buildout.plone.wsgi
===================

Configuración de buildout para ejecutar el CMS Plone 4 con WSGI.

Requerimientos
==============

Estos son los requerimientos mínimos de instalación: ::

  # aptitude install gcc g++ make tar unzip bzip2 libssl-dev libxml2-dev zlib1g-dev libjpeg62-dev libreadline6-dev readline-common wv xpdf-utils python2.7-dev libxslt1-dev python-pip
  # pip install virtualenv==1.9.1 ; exit

Crear entorno virtual
=====================

Para la inicialización del proyecto Buildout, ejecute el siguiente comando: ::

  $ virtualenv --no-setuptools python2.7
  $ source ./python2.7/bin/activate

Inicialización del proyecto
===========================

Para la inicialización del proyecto Buildout, ejecute el siguiente comando: ::

  (python2.7)$ python bootstrap.py

Construcción del proyecto
=========================

Para la construcción del proyecto Buildout, ejecute el siguiente comando: ::

  ./bin/buildout

Iniciar procesos
================

Para iniciar Zope con WSGI lo realiza mediante supervisor, ejecute el siguiente comando: ::

  ./bin/supervisord

Puede acceder a la interfaz administrativa de supervisor en la siguiente dirección http://127.0.0.1:9001/

Para iniciar la instancia Zope, ejecute el siguiente comando: ::

  ./bin/plone fg

Puede acceder a la ZMI para crear su sitio Plone en la siguiente dirección http://127.0.0.1:8000/manage

Para entrar detener el proceso supervisor, ejecute el siguiente comando: ::

  ./bin/supervisorctl -i
  gunicorn                         RUNNING    pid 28138, uptime 0:00:01
  zeo                              RUNNING    pid 28139, uptime 0:00:01
  supervisor>

Para detener cada proceso, ejecute el siguiente comando: ::

  supervisor> stop zeo
  supervisor> stop gunicorn

Para salir del shell interactivo de supervisor, ejecute el siguiente comando: ::

  supervisor> exit
