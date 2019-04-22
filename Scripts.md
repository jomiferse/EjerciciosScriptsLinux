# Ejercicios Scripts Linux

### 1
~~~
#! /bin/bash
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
#! /bin/bash
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
#! /bin/bash
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
#! /bin/bash
PALABRA=`cat ./palabra.txt`
if [ $PALABRA == 'jm' ]; then
	echo La palabra es correcta, $PALABRA
else
	echo La palabra no es correcta, $PALABRA
fi
~~~

### 5
~~~
#! /bin/bash
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
#! /bin/bash
echo "Introduce una edad"
read n1
if [ $n1 -gt 17 ];
then
        echo "Es mayor de edad"
else
        echo "Es menor de edad"
fi
~~~

### 7
~~~
#! /bin/bash
 if [ -f $1 ]; then
echo "El parametro introducido es un fichero"
ls -l $1

    if [ -r $1 ];then
    echo " Tiene permisos de Lectura"

        if [ -w $1 ];then
        echo "Tiene permisos de escritura "
        chmod ug+x $1
        ls -l $1
      
        else
        echo "No es un fichero comun"
        fi

    else
    echo "No es un fichero comun"

    fi

else
echo "El fichero no existe "
fi
~~~

### 8
~~~
#! /bin/bash
read -n 1 tecla
case $tecla in
[a-z,A-Z]) echo " ha introducido una letra"
;;
[0-9]) echo " Ha introducido un numero"
;;
*) echo " Ha introducido un caracter especial"
;;
esac
~~~

### 9
~~~
#! /bin/bash
cont=0
contf=0

for var in $*; do
   if [ -d $var ]; then
   cont=`expr $cont + 1`
   elif [ -f $var ]; then
   contf=`expr $contf + 1`
   else
   echo "$var no es fichero ni directorio"
   fi
done
echo "Ha introducido $cont directorios y $contf ficheros."
echo "Se han introducido $# parametros"
~~~

### 10
~~~
#! /bin/bash
echo """"
echo "Bienvenido a la tienda Online - MERCADONA"
echo ""
echo "1. Refresco 1 euro"
echo "2. Sandiwch 3 euros"
echo "3. Tabaco 5 euros"
echo "4. Patatas 8 euros"
echo "5. Jamón 15 euros"
echo "6. Pollo frito 20 euros"
echo ""
read -p "Introduzca opcion:" op
read -p " Introduzca importe: " mon
case $op in
1)
precio=1
;;
2)
precio=3
;;
3)
precio=5
;;
4)
precio=8
;;
5)
precio=15
;;
6)
precio=20
;;
*)
echo "Opcion incorrecta"
esac
while [ $mon -lt $precio ]; do
falta=`expr $precio - $mon`
read -p " Introduzca $falta euros, por favor introduzcalos: " mas
mon=`expr $mon + $mas`
done
 if [ $mon -gt $precio ]; then
cambio=`expr $mon - $precio`
echo "Gracias por su compra, su cambio es de $cambio euros"

else
echo "Gracias por su compra. Buen provecho"
fi
~~~

### 11
~~~
#! /bin/bash
read -p "Introduzca la ruta de un directorio :" dir
until [ -d $dir ]; do
read -p "Introduzca la ruta de un directorio :" dir
done
cont=0
contf=0
     for var in `ls $dir`; do
            if [ -d $var ]; then
             cont=`expr $cont + 1`
             elif [ -f $var ]; then
             contf=`expr $contf + 1`
            fi
     done
echo "Ha introducido $cont directorios y $contf ficheros."
echo "Se han introducido $# parametros"
~~~

### 12
~~~
#! /bin/bash
echo " la tabla de multiplicar de $1 es: "
numerador=1
while [ $numerador -lt 11 ]; do
resul=`expr $1 \* $numerador`
echo "$1 x $numerador = $resul"
numerador=`expr $numerador + 1`
done
~~~

### 13
~~~
#! /bin/bash
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -t raw -F
iptables -t raw -X
iptables -t security -F
iptables -t security -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -I INPUT -j ACCEPT
~~~

### 14
~~~
#! /bin/bash
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -t raw -F
iptables -t raw -X
iptables -t security -F
iptables -t security -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP
~~~

### 15
~~~
#! /bin/bash
ifconfig
iptables -P INPUT ACCEPT
iptables -P OUTPUT DROP
~~~
