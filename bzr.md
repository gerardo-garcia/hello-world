#BZR (Bazaar)

Aquí viene una guía buena: http://doc.bazaar.canonical.com/latest/en/mini-tutorial/
La principal diferencia que he percibido es que bzr sincroniza ramas locales con ramas en launchpad,
de modo que Launchpad te muestra las ramas en las que trabajas, no los proyectos.

##Instalación
Hay que instalar el paquete bzr:
```
$ dpkg -l bzr
Deseado=desconocido(U)/Instalar/eliminaR/Purgar/retener(H)
| Estado=No/Inst/ficheros-Conf/desempaqUetado/medio-conF/medio-inst(H)/espera-disparo(W)/pendienTe-disparo
|/ Err?=(ninguno)/requiere-Reinst (Estado,Err: mayúsc.=malo)
||/ Nombre                                               Versión                         Arquitectura                    Descripción
+++-====================================================-===============================-===============================-==============================================================================================================
ii  bzr                                                  2.7.0-2ubuntu3                  all                             easy to use distributed version control system
```

##Configuración
Hay que poner un usuario y un correo, como en la configuración para Github:
`$ bzr whoami "Mr X <mr.x@gmail.com>"`

##Creación de un nuevo proyecto/repo local
```
$ bzr init-repo test
Shared repository with trees (format: 2a)
Location:
  shared repository: test
$ bzr init test/trunk
$ cd test/trunk
Created a repository tree (format: 2a)
Using shared repository: /home/mrx/test/
```

##Trabajar con el repo:
```
$ bzr add mytest.py
adding mytest.py

$ bzr commit -m "Added first file"
Confirmando  to: /home/mrx/test/trunk/
añadido mytest.py
Revisión 1 confirmada.

$ echo HOLA > test.txt
$ bzr add test.txt
adding test.txt
$ bzr commit -m "Added test file"
Confirmando  to: /home/mrx/test/trunk/
añadido test.txt
Revisión 2 confirmada.

$ echo ADIOS > test.txt
$ bzr diff test.txt
=== modified file 'test.txt'
--- test.txt    2017-03-02 10:33:07 +0000
+++ test.txt    2017-03-02 10:33:36 +0000
@@ -1,1 +1,1 @@
-HOLA
+ADIOS

$ bzr add test.txt
$ bzr diff test.txt
=== modified file 'test.txt'
--- test.txt    2017-03-02 10:33:07 +0000
+++ test.txt    2017-03-02 10:33:36 +0000
@@ -1,1 +1,1 @@
-HOLA
+ADIOS

$ bzr commit -m "Change in test file"
Confirmando  to: /home/mrx/test/trunk/
modificado test.txt
Revisión 3 confirmada.
```

##Ver el log
```
$ bzr log
------------------------------------------------------------
revno: 3
committer: Mr X <mr.x@gmail.com>
branch nick: trunk
timestamp: Thu 2017-03-02 11:34:37 +0100
message:
  Change in test file
------------------------------------------------------------
revno: 2
committer: Mr X <mr.x@gmail.com>
branch nick: trunk
timestamp: Thu 2017-03-02 11:33:07 +0100
message:
  Added test file
------------------------------------------------------------
revno: 1
committer: Mr X <mr.x@gmail.com>
branch nick: trunk
timestamp: Thu 2017-03-02 11:31:46 +0100
message:
  Added first file
```

##Publicar en launchpad
* Genera un par de claves y copia la clave pública en Launchpad
* (OPCIONAL) Crea en Launchpad un equipo para el proyecto. https://launchpad.net/people/+newteam
* (OPCIONAL) Crea en Launchpad un proyecto. https://launchpad.net/projects/+new
* Para cosas personales puedes usar el pseudo-proyecto "+junk". Más info aquí: https://help.launchpad.net/Code/PersonalBranches
* Indica a Bazaar tu nombre en launchpad:
`$ bzr launchpad-login mr.x`
* Haz un push del branch:
Para un proyecto con gente:
`$ bzr push lp:~sample-team/test/trunk`
Para algo personal, puedes usar el pseudo-proyecto "+junk"
`$ bzr push ~mr.x/+junk/trunk`
Si en vez de "+junk", uso el proyecto "test", se permite el push, pero dicho proyecto no existe en launchpad hasta que no lo cree.
`$ bzr push lp:~ggdb/test/trunk`
Rama nueva creada.
En mi opinión, lo mejor mientras no tienes un proyecto puede ser:
gerardo@milonga-ubuntu[12:18:46]:~/workspace/launchpad/test/trunk$ bzr push lp:~ggdb/+junk/test-trunk
Rama nueva creada.

##Clonar una rama (crear una copia local de una rama)
Por ejemplo, para crear una copia local de la rama trunk del proyecto gtk:
```
$ bzr init-repo bzr-gtk
$ bzr branch lp:~bzr/bzr-gtk/trunk bzr-gtk/mygtk
```
Para una copia de una rama del pseudo-proyecto "+junk", sería:
```
$ bzr init-repo test
$ bzr branch lp:~ggdb/+junk/test-trunk test/trunk
```

##Actualizar rama local con la rama remota (merge)


##Ayuda
```
$ bzr help
$ bzr help command
```
