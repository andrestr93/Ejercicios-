#1º SCRIPT
#!/bin/sh
# Este script elimina un archivo o directorio pasado como parámetro y le pregunta al usuario si está seguro de llevar a cabo tal acción.
dialog --yesno "¿Está seguro que desea eliminar el archivo o directorio?" 0 0;\

case $? in

0) # En caso que el usuario seleccione "Sí".

if test $# -lt 1 # Si el número de parámetros posicionales o argumentos que se le dan al script es menor que 1, donde "-lt" significa 

"lower than" y es equivalente a lo que en otros lenguajes se utiliza como "<".

then echo "Error. Sintaxis de uso: $0 archivo_|_directorio" # Error que mostrará el script cuando no se le den argumentos.

elif test -d $1 # Si el parámetro posicional "$1" existe y es un directorio.

then echo "$1 es un directorio."

rmdir $1 # Remover $1, donde "$1" es el directorio que el usuario puso como parámetro del script.

echo "El directorio $1 ha sido eliminado." # Nótese que ";;" se le pone cuando han terminado todos los elif.

test -f $1 # Si el parámetro posicional "$1" existe y es un archivo regular. then echo "$1 es un archivo."

rm $1 # Remover $1, donde "$1" es el directorio que el usuario puso como parámetro del script. echo "El archivo $1 ha sido eliminado." #

Nótese que ";;" se le pone hasta que han terminado todos los else.

# Si el usuario no ha introducido ningún parámetro posicional o ningún argumento al script.

echo "Error. Sintaxis de uso: $0 archivo_|_directorio" # Error que mostrará el script cuando no se le den argumentos.
fi;;
1) # En caso que el usuario seleccione "No".

echo "No se ha eliminado ningún archivo ni directorio.";;

255) # En caso que el usuario presiona la tecla ESC".

echo "No se ha eliminado ningún archivo ni directorio.";;

esac

#2º SCRIPT 

#!/bin/bash

# Este script recibe un comando como argumento y muestra información sobre dicho comando.

Error(){

echo "Error. Sintaxis de uso: $0 nombre_del_comando" # Error que mostrará el script cuando no se le den argumentos.

}
if test $# -lt 1 # Si el número de parámetros posicionales o argumentos que se le dan al script es menor que 1, donde "-lt" significa

"lower than" y es equivalente a lo que en otros lenguajes se utiliza como "<".

then Error # En caso que no se hayan dado argumentos para el script, manda el mensaje de error que se creó con la función.

else echo "La información o forma de usar el comando que usted busca es la siguiente:"

man $1 # Muestra el manual o forma de usar el comando que el usuario quiere saber. Si el usuario escribió "./8 ps" para ejecutar el

script, el parámetro posicional o "$1" será "ps", de modo que el script se ejecutará mostrando el manual de uso del comando "ps", lo que 

equivale a haber escrito en la consola "man ps" sin haber utilizado este script.

# Script 3º

# Nos pide la edad y nos dice si es mayor de edad o no .

#!/bind/bash
#Nos pide la edad y nos dice si es mayor de edad o menor

read -p "introduce tu edad: " edad
if [ $edad -lt 18 ]; then
echo " Eres menor de edad "

elif [ $edad -gt 18 ]; then
echo "Eres mayor de edad"

else
echo "Eres mayor de edad"

# Script 4º 
#Script que reciba un nombre de fichero, verifique que existe y que es un fichero comun (lectura-escritura) lo convierta en ejecutable para el usuario y el grupo y muestre el estado final de los permisos.

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

#Script 5º

#Script que nos diga al pulsar una tecla, si es letra, numero o caracter especial


read -n 1 tecla
case $tecla in
[a-z,A-Z]) echo "ha introducido una letra"
;;
[0-9]) echo "Ha introducido un numero"
;;
*) echo "Ha introducido un caracter especial"
;;
#Script 6º

#realizar un scrip que reciba varios parametros y nos diga cuantos de esos parametros son de directorios y cuantos son archivos. $# contador que indica cuantos parametros se pasan.

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

#Script 6º 

# Mostramos menu, con productos para vender, luego nos pide que introduzcamos la opcion. luego mensaje que indica que introduzca moneda. Si ponemos precio exacto nos da mensaje, "Gracias buen provecho", si ponemos menos, nos diga falta.
Si poner mas valor, nos indique el cambio con mensaje.

echo """"
echo "Bienvenido a la tienda On-line - CEPAL"
echo ""
echo "1. Refresco 1 euro"
echo "2. Sandiwch 3 euros"
echo "3. Tabaco 5 euros"
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
*)
echo "Opcion incorrecta"
esac
while [ $mon -lt $precio ]; do
falta=`expr $precio - $mon`
read -p " Introduzca $falta euros, por favor introduzcalos" mas
mon=`expr $mon + $mas`
done
 if [ $mon -gt $precio ]; then
cambio=`expr $mon - $precio`
echo "Gracias por su compra, su cambio es de $cambio euros"

else
echo "Gracias por su compra. Buen provecho"
fi

#Script 7º 
#Realizar un script que pida introducir la ruta de un directorio por teclado (Hay que validar que la variable introducida sea un directorio) nos diga cuantos archivos y cuantos directorios hay dentro de ese directorio.

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

#Script 8º

#Realiza un script que introduzca numero por parametro y muestre tabla de multiplicar

echo " la tabla de multiplicar de $1 es: "
numerador=1
while [ $numerador -lt 11 ]; do
resul=`expr $1 \* $numerador`
echo "$1 x $numerador = $resul"
numerador=`expr $numerador + 1`
done




