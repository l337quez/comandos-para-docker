## Levantar una imagen
```
> docker-compose up -d
```
<br/>

## Listar imagenes levantadas
```
> docker ps
```
<br/>

## Entrar a un  contenedor 
Una vez listados los contenedores, podremos ver una informacion de cada uno.  entre esta informacion esta el id del contenedor. Para levantar el contenedor debemos tipear ese id
```
> docker network ls
```
<br/>

## Listar conexiones Network
```
> docker network ls
```
<br/>

## Eliminar conexiones Network
	> docker network rm nombre_de_la_conexion

</br>

* Para asignarle un puerto en nuestra pc (traducir el puerto interno al de la pc)
	> docker run -p 3000:80 nginx

Aquí 80 es el puerto interno donde está corriendo nginx dentro del contenedor, y 3000 es el puerto en nuestra pc a traves del cual es accesible el contenedor.

Si en el navegador ejecutamos localhost:3000 veremos que se carga el servidor nginx interno del contenedor.


Si queremos que al ejecutar el contenedor no se quede pegada la consola desde la que lo ejecutamos agregamos -d
	> docker run -p 80:80 -d nginx


* Para eliminar todos los contenedores
	> docker rm $(docker ps -aq)

* Podemos ejecutar un contenedor dándole un nombre personalizado
	> docker run -d -p 3306:3306 --name mydatabase mysql

* Para listar las imagenes que nos hemos descargado
	> docker images

* Para eliminar una imagen
	> docker rmi id_imagen
 
Para eliminar una imagen esta no puede estar siendo utilizada en un contenedor

* Listar id de las imagenes
	> docker images -aq

* Para copiar archivos dentro de un contenedor. Si por ejemplo queremos agregar archivos dentro de una carpeta del un contenedor de un servidor nginx usamos -v
	> docker run -p 80:80 -d -v /carpeta/origen:/carpeta/destino nginx 


* Si agregamos :ro el interior será de solo lectura
	> docker run -p 80:80 -d -v /carpeta/origen:/carpeta/destino:ro nginx


* Ejecutar un programa interno de un contenedor
	> docker exec -it nombre_contenedor nombre_programa

* Si agregamos 
	> docker run -p 80:80 -d -v /carpeta/origen:/carpeta/destino nginx
 

* Para crear una imagen
	> docker build -t wepabackend .


* Para detener todos los contenedores
    > docker stop $(docker ps -a -q)
