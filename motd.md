# MOTD (mot of the day) #

## Installation ##
Necesitas instalar strfile y fortune.

## Fichero motds ##
Es el fichero que tiene las frases en lineas independientes, separadas por el signo "%".

```
Frase1
%
Frase2
```

## Preparar fichero motds ##
`strfile motds`

Te genera un fichero motds.dat que es el que usa el programa fortune.

## Fichero .profile ##
```
echo
fortune   # Genera un mensaje usando la base de datos de frases del sistema
echo
fortune $HOME/motd/motds   # Genera un mensaje usando la base de datos de frases del usuario (no hay que poner extensión .dat)
echo
#Otra opcion (que lo diga Tux): fortune | cowsay -f tux
#Otra opcion (categorias concretas de fortune): fortune science linux politics
```

