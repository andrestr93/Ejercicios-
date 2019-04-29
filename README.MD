Primeramente se debera descargar el "dialog", de esta forma:
# apt-get install dialog
Luego el script es este:
#!/bin/sh
# Este script elimina un archivo o directorio pasado como parámetro y le pregunta al usuario si está seguro de llevar a cabo tal acción.
dialog --yesno "¿Está seguro que desea eliminar el archivo o directorio?" 0 0;\
case $? in
0) # En caso que el usuario seleccione "Sí".
if test $# -lt 1 # Si el número de parámetros posicionales o argumentos que se le dan al script es menor que 1, donde "-lt" significa "lower than" y es equivalente a lo que en otros lenguajes se utiliza como "<".
then echo "Error. Sintaxis de uso: $0 archivo_|_directorio" # Error que mostrará el script cuando no se le den argumentos.
elif test -d $1 # Si el parámetro posicional "$1" existe y es un directorio.
then echo "$1 es un directorio."
rmdir $1 # Remover $1, donde "$1" es el directorio que el usuario puso como parámetro del script.
echo "El directorio $1 ha sido eliminado." # Nótese que ";;" se le pone cuando han terminado todos los elif.
test -f $1 # Si el parámetro posicional "$1" existe y es un archivo regular. then echo "$1 es un archivo."
rm $1 # Remover $1, donde "$1" es el directorio que el usuario puso como parámetro del script. echo "El archivo $1 ha sido eliminado." # Nótese que ";;" se le pone hasta que han terminado todos los else.
# Si el usuario no ha introducido ningún parámetro posicional o ningún argumento al script.
echo "Error. Sintaxis de uso: $0 archivo_|_directorio" # Error que mostrará el script cuando no se le den argumentos.
fi;;
1) # En caso que el usuario seleccione "No".
echo "No se ha eliminado ningún archivo ni directorio.";;
255) # En caso que el usuario presiona la tecla ESC".
echo "No se ha eliminado ningún archivo ni directorio.";;
esac
