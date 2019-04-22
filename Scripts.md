# Ejercicios Scripts Linux

### 1
~~~
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
rm $1 echo "El archivo $1 ha sido eliminado."
echo "Error. Sintaxis de uso: $0 archivo_|_directorio"
fi;;
1) # En caso de que el usuario seleccione "No".
echo "No se ha eliminado ningún archivo ni directorio.";;
255) # En caso de que el usuario presiona la tecla ESC".
echo "No se ha eliminado ningún archivo ni directorio.";;
esac
~~~

### 2
~~~
Error(){
echo "Error. Sintaxis de uso: $0 nombre_del_comando"
}
if test $# -lt 1
then Error
else echo "La información o forma de usar el comando que usted busca es la siguiente:"
man $1
fi
~~~

### 3
~~~
USER=`whoami`
if [ $USER == 'blas' ]; then
	echo $USER
	echo $USER
	echo $USER
	echo $USER
	echo $USER
else
	echo "Adiós"
fi
~~~

### 4
~~~
PALABRA=`cat ./palabra.txt`
if [ $PALABRA == 'jm' ]; then
	echo La palabra es correcta, $PALABRA
else
	echo La palabra no es correcta, $PALABRA
fi
~~~

### 5
~~~
clear
PS3='Introduce una opción: '
opciones=("Sumar" "Restar" "Multiplicar" "Salir")
select opt in "${opciones[@]}"
do
    case $opt in
        "Sumar")
            echo -n "Introduce el primer número entero: "
	    read n1
            echo -n "Introduce el segundo número entero: "
	    read n2
	        S=$(expr $n1 + $n2)
            echo "$n1 + $n2 = $S"
            ;;
        "Restar")
            echo -n "Introduce el primer número entero: "
	    read n1
            echo -n "Introduce el segundo número entero: "
	    read n2
	        S=$(expr $n1 - $n2)
            echo "$n1 - $n2 = $S"
            ;;
        "Multiplicar")
            echo -n "Introduce el primer número entero: "
	    read n1
            echo -n "Introduce el segundo número entero: "
	    read n2
	        S=$(expr $n1 \* $n2)
            echo "$n1 * $n2 = $S"
            ;;
        "Salir")
            clear
            break
            ;;
        *) echo "Opción incorrecta $REPLY";;
    esac
done
~~~

### 6
~~~

~~~
