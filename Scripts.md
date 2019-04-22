# Ejercicios Scripts Linux

### 1
~~~
#!/bin/sh
dialog --yesno "¿Está seguro que desea eliminar el archivo o directorio?" 0 0;\
case $? in
0) # En caso de que el usuario seleccione "Sí".
if test $# -lt 1
then echo "Error. Sintaxis de uso: $0 archivo_|_directorio"
elif test -d $1
then echo "$1 es un directorio."
rmdir $1
echo "El directorio $1 ha sido eliminado."
test -f $1
rm $1 # Remover $1, donde "$1" es el directorio que el usuario puso como parámetro del script. echo "El archivo $1 ha sido eliminado." # Nótese que ";;" se le pone hasta que han terminado todos los else.
# Si el usuario no ha introducido ningún parámetro posicional o ningún argumento al script.
echo "Error. Sintaxis de uso: $0 archivo_|_directorio" # Error que mostrará el script cuando no se le den argumentos.
fi;;
1) # En caso que el usuario seleccione "No".
echo "No se ha eliminado ningún archivo ni directorio.";;
255) # En caso que el usuario presiona la tecla ESC".
echo "No se ha eliminado ningún archivo ni directorio.";;
esac

~~~

### 2
