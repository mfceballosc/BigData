# Taller 20-05-2024

imagen con la que vamos a trabajar

```cmd
rem Imagen con la que vamos a trabajar:
docker run --rm -it --name hadoop -p 50070:50070 -p 8088:8088 -p 8888:8888 -v "%cd%":/workspace jdvelasq/hadoop:2.10.1
```

Si la imagen ya la tenemos descargada, podemos volverla a iniciar de la siguiente manera:

```cmd

```

comandos comunes en hadoop para realizar computación distribuida

Siempre vamos a utilzar la palabra hdfs
Esto lo podemos realizar porque descargamos una imagen de hadoop.

```cmd
rem ayuda sobre la imagen
hdfs --help
rem siempre nos vamos a quedar con
hdfs dfs -ls
rem creamos una carpeta
hdfs dfs -mkdir /user/root/workshop1
rem visualizamos
hdfs dfs -ls /user/root

rem creamos un archivo
rem vemos lo que contiene la carpeta
ls -la 
echo "analitica y big data, 300123, 58, 1" > prueba.txt
rem añadir datos al archivo prueba.txt
echo "analitica y big data, 300123, 58, 2" >> prueba.txt
rem vamos a subir el archivo a hadoop, tambien se puede hacer con el comando -copyFromLocal
hdfs dfs -put prueba.txt /user/root/workshop1/
rem imprimo lo que tiene la carpeta
hdfs dfs -ls /user/root/workshop1/

rem eliminar el archivo copiado
rem hdfs dfs -rm /user/root/workshop1/prueba.txt

rem Descargar el archivo desde el remoto al local
hdfs dfs -get /user/root/workshop1/prueba.txt .

hdfs dfs -ls /user/root/workshop1/
hdfs dfs -get /user/root/workshop1/prueba.txt /tmp/pruebaV2.txt
rem visualizamos el archivo copiado
ls /tmp




```



