# Descargar la imagen 
Para descargar la imagen, ejecutar en cmd la siguiente instrucción:
```cmd
docker run --rm -it --name ubuntu -v "%cd%":/workspace jdvelasq/ubuntu:20.04
```
Eliminar una imagen:

```cmd
rem Eiliminar una imagen
docker rmi nombre_de_la_imagen
rem por medio del id de la imagen
docker rmi ID_de_la_imagen
rem lista de contenerdores ene ejecución
docker ps
rem detener un contenedor
docker stop ID_del_contenedor
rem se puede detener y eliminar el contenedor en una sola linea de la siguiente forma
docker stop $(docker ps -aq) && docker rmi nombre_de_la_imagen
rem Eliminar una imagen que esta en uso de forma forzada
docker rmi -f nombre_de_la_imagen

```

# Taller 
Realice los siguientes ejercicios usando la terminal:

1. En una carpeta compartida entre VM y su local, cree cree un directorio llamado paractica-bash-1
2. Dentro del directorio practica-bash-1 cree tres carpetas llamadas 1, 2 y 3
3. En el directorio 1, cree los directorios 1-1, 1-2, 1-3
4. En el directorio 2, cree los directorios 2-1, 2-2, 2-3
5. En el directorio 3, cree los directorios 3-1, 3-2, 3-3
6. Estando posicionado en la carpeta practica-bash-1, use el comando tree para visualizar la estructura de los subdirectorios.
7. En el directorio 1-1 cree los archivos SUCCESS y part-0
8. Copie el archivo part-0 a part-1 y part-2
9. Renombre part-0 a part-00001 y part-2 a part-00002
10. Estando posicionado en la carpeta practica-bash-1, use el comando tree para visualizar la estructura de los subdirectorios.
11. Mueva el contenido de la carpeta 1-1 a la carpeta 3-3
12. Borre el directorio practica-bash-1

## Solución
```bash
# Revisamos los directorios
ls
# creamos el directorio
mkdir practica-bash-1
# Creamos las carpetas 1, 2 y 3
mkdir 1 2 3
# o
mkdir -p {1}{2}{3}

# Desarrollo del punto 4
cd 1
mkdir 1-1 1-2 1-3
# Desarrollo del punto 5
cd ..
cd 2
mkdir 2-1 2-2 2-3
# Desarrollo del punto 6
cd ..
cd 3
mkdir 3-1 3-2 3-3
# Desarrollo del punto 7
#SUCCESS y part-8
cd 1/1-1
touch SUCCESS part-0
# Desarrollo del punto 8
cp part-0 part-1
cp part-0 part-2
# Desarrollo del punto 9
mv part-0 part-00001
mv part-2 part-00002
# Desarrollo del punto 10
cd ../../../
tree
# Desarrollo del punto 11
mv 1/1-1/* 3/3-3/
# Desarrollo del punto 12
rm -r practica-bash-1
#Nota, cuando necesitamos eliminar una carpeta es rm, para eliminar un archivo es rmdir


# Ejemplo2
#Creamos un archivo
echo "hola mundo!" > holamundo.txt
cat holamundo.txt
# Cambiamos el texto
echo "Chau mundo!" >>holamundo.txt
cat holamundo.txt

echo "hola" >>holamundo.txt
cat holamundo.txt

# Vamos a realizar un cambio
# Cambiamos hola por Chau
sed 's/hola/Chau/g' holamundo.txt
#Nota, notar que /g es la que hace que se cambie todas las palabras hola del arhivo, de lo contrario se cambia la primera
cat holamundo.txt
# Cambiamos el primer hola
sed 's/Chau/Hola/' holamundo.txt


#Ejemplo 2
echo "Hola mundo!" > taller.txt
echo "Chau mundo!" >> taller.txt
echo "Hola mundote Eres un ganador" >> taller.txt
cat taller
# Queremos que reemplace algo especifico con un flag
sed "s/Hola/chau/g" taller.txt
# Cambiamos Chau y agregamos signo pesos. Todo lo que termine en chau lo cambiamos por hola
sed "s/chau$/hola" taller.txt

# con expresiones regulares
# -E Denotacióin extendida, a todo se le va a aplicar
# Todo lo vamos a reemplazar por la palabra hola. Finaliza con como estas

sed -E "s/(.*)/Hola\1,como estas?/" taller.txt

# Creamos un archivo
echo "Danilo:31:Ingeniero" > empleados.txt
echo "Girleza:49:Data science" >> empleados.txt
echo "Santiago:19:asistente" >> empleados.txt
echo "Ana:40:secretario" >> empleados.txt
cat empleados.txt

# Imprimimos la primera columna
# awk '{print $1}' empleados.txt #(no funciona)
awk -F: '$2>40 {print $1}' empleados.txt
# otra forma
cut -d: -f1 empleados.txt

# Vamos a imprimir el nombre de las personas cuyo cargo comience con s

awk -F: '$3~/^s/ {print $1}' empleados.txt



```

