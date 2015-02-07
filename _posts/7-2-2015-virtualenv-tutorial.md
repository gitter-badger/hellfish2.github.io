---
layout: post
title: Tutorial Virtualenv
---
![_config.yml]({{ site.baseurl }}/images/python.jpg)

Cuando se está desarrollando software con Python, es común utilizar diferentes versiones de una mismo paquete. Por ejemplo, imaginemos que se está desarrollando un juego con la versión 1.2 de Pygame y mientras eso pasa, se comienza el desarrollo de un nuevo juego que necesita las nuevas características presentes en la versión 1.3 del mismo paquete.

En este punto ya se tiene instalada una versión del paquete en el sistema que no puede ser eliminada en favor de la nueva versión. Así que el problema a solucionar radica en como poder instalar las dos versiones de la misma librería con el fin de poder desarrollar ambos proyectos de forma simultánea.

La solución consiste en crear virtualenvs o entornos virtuales. En palabras simples, un entorno virtual de Python es un espacio completamente independiente de otros entornos virtuales y de los paquetes instalados globalmente en el sistema. Esto significa que es posible instalar la versión 1.2 de Pygame en un entorno virtual y la versión 1.3 en otro diferente o de forma global sin problema alguno.

Para poder utilizar este simple pero poderoso concepto es necesario instalar una utilidad que permita gestionar la creación y utilización de dichos entornos virtuales llamada virtualenv.

Cómo instalar la utilidad virtualenv

Se puede instalar la utilidad virtualenv utilizando el gestor de paquetes de las distribuciones Linux:

Los comandos mostrados en este tutorial aplican para Python 2.x.
# Archlinux
$ sudo pacman -S python2-virtualenv

# Fedora
$ sudo yum install python-virtualenv

# Debian, Ubuntu
$ sudo apt-get install python-virtualenv
También es posible instalar virtualenv utilizando pip:

# Linux, Mac OS X
$ sudo pip install virtualenv

# Archlinux
# (si pip fue instalado usando el gestor de paquetes)
$ sudo pip2 install virtualenv

# Fedora
# (si pip fue instalado usando el gestor de paquetes)
$ sudo pip-python install virtualenv
Cómo crear un Python virtualenv

Para crear un virtualenv simplemente se ejecuta el siguiente comando desde una terminal:

# Linux, Mac OS X
$ virtualenv mi_proyecto

# Archlinux
$ virtualenv2 mi_proyecto
Lo que crea el directorio mi_proyecto/ con la siguiente estructura.

mi_proyecto/
bin/
include/
lib/
En el directorio bin/ se encuentran los ejecutables necesarios para interactuar con el virtualenv. En include/ se encuentran algunos archivos de cabecera de C (archivos .h) necesarios para compilar algunas librerías de Python. Y finalmente en lib/ se encuentra una copia de Python así como un directorio llamado site-packages/ en el cual se aloja el código fuente de los paquetes Python instalados en el virtualenv.

Cómo activar un Python virtualenv

Para activar un virtualenv o entorno virtual, se procesa el archivo bin/activate que se encuentra en la carpeta que se ha creado al ejecutar la utilidad virtualenv:

$ cd mi_proyecto
$ source bin/activate
(mi_proyecto)$
El prompt de la terminal indica que el virtualenv está activado. De esta manera ya es posible utilizar los paquetes Python instalados así como instalar paquetes adicionales.

Cómo desactivar un Python virtualenv

Para desactivar un virtualenv porque se necesita trabajar en otro diferente, por ejemplo, se ejecuta el comando deactivate. No es necesario ir a la carpeta del virtualenv para realizar la operación:

(mi_proyecto)$ deactivate
$
El prompt de la terminal indica que el virtualenv ha sido desactivado con éxito.

Cómo instalar paquetes en un Python virtualenv

Después de activarlo, lo único que resta es instalar los paquetes que sean necesarios usando el ejecutable pip que viene por defecto en cada virtualenv creado.

Por ejemplo, si se desea instalar django, se ejecuta el siguiente comando:

(mi_proyecto)$ pip install django
Notese que el prompt de la terminal indica que el virtualenv mi_proyecto ya está activado.

¿En qué directorio ubico el código fuente de mi proyecto?

La ubicación del código fuente del proyecto en el que se está trabajando no es importante. Puede ser colocado inclusive dentro del directorio del virtualenv. Una vez que el virtualenv está activado, todas las librerías de Python que instalen solo podrán ser usadas al activar ese virtualenv específico.
