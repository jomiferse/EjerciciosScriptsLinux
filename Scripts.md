# Ejercicios Scripts Linux

### 1
~~~
#!/bin/sh
dialog --yesno "¿Está seguro que desea eliminar el archivo o directorio?" 0 0;\
case $? in
if test $# -lt 1
then echo "Error. Sintaxis de uso: $0 archivo_|_directorio"
elif test -d $1
then echo "$1 es un directorio."
rmdir $1 
echo "El directorio $1 ha sido eliminado." 
test -f $1 then echo "$1 es un archivo."
rm $1 echo "El archivo $1 ha sido eliminado."
echo "Error. Sintaxis de uso: $0 archivo_|_directorio"
fi;;
1) # En caso que el usuario seleccione "No".
echo "No se ha eliminado ningún archivo ni directorio.";;
255) # En caso que el usuario presione la tecla ESC".
echo "No se ha eliminado ningún archivo ni directorio.";;
esac
~~~

### 2
