#### Buscar una imagen
	> docker search nombre_imagen* Descargar una imagen
</br>
	
	> docker pull nombre_imagen* Ejecutar una contenedor de una imagen descargada

</br>

	> docker run nombre_imagen* Ejecutar una aplicación de un contenedor de forma interactiva por consola
	
</br>

	> docker run -it nombre_imagen nombre_programa_interno_de_la_imagen
	
</br>	

#### Ejecutar mongo que se encuentra dentro de un contenedor

</br>

    > sudo docker exec -it nombre_contenedor mongo* Mostrar los contenedores que se están ejecutando

</br>

	> docker ps* Mostrar los contenedores que han sido ejecutados el algún momento

</br>

	> docker ps -a* Para eliminar un contenedor


</br>

	> docker rm id_del_contenedorpor ejemplo si vemos los contenedores que han sido creados:CONTAINER ID   IMAGE   COMMAND   CREATED  	STATUS                         PORTS            NAMES
a1bd3e3d3772   ubuntu  "bash"    27 minutes ago Exited (0) 26 minutes ago                       stoic_satoshipodemos eliminar el contenedor ubuntu con el comando
	
</br>
	
	> docker rm a1bd3e3d3772* Para ejecutar un contenedor que esta detenido

</br>

	> docker start id_del_contenedor* Para detener un contenedor que esta corriendo

</br>

	> docker stop id_del_contenedor	Tambien funciona si solamente tecleamos las primeras tres letras del id del contenedor.* Cada contenedor puede tener un puerto, esto para aplicaciones que puedan requerir un puerto, como son las bases de datos por ejemplo.Ejemplifiquemos con un servidor nginx	> docker pull nginx

</br>

	> docker run nginxEl contenedor se crea e inicializa. Si abrimos otra terminal vemos que se encuentra corriendo.
Al ejecutar docker ps, nos muestra que se encuentra corriendo en un puerto. Ese puerto se encuentra corriendo
en un puerto interno del contenedor.* Para asignarle un puerto en nuestra pc (traducir el puerto interno al de la pc)

</br>

	> docker run -p 3000:80 nginxAquí 80 es el puerto interno donde está corriendo nginx dentro del contenedor, y 3000 es el puerto en nuestra pc a traves del cual es accesible el contenedor.Si en el navegador ejecutamos localhost:3000 veremos que se carga el servidor nginx interno del contenedor.Si queremos que al ejecutar el contenedor no se quede pegada la consola desde la que lo ejecutamos agregamos -d

</br>

	> docker run -p 80:80 -d nginx* Para eliminar todos los contenedores

</br>

	> docker rm $(docker ps -aq)* Podemos ejecutar un contenedor dándole un nombre personalizado

</br>

	> docker run -d -p 3306:3306 --name mydatabase mysql* Para listar las imagenes que nos hemos descargado

</br>

	> docker images* Para eliminar una imagen

</br>

	> docker rmi id_imagenPara eliminar una imagen esta no puede estar siendo utilizada en un contenedor* Listar id de las imagenes

</br>

	> docker images -aq* Para copiar archivos dentro de un contenedor. Si por ejemplo queremos agregar archivos dentro de una carpeta del un contenedor de un servidor nginx usamos -v

</br>

	> docker run -p 80:80 -d -v /carpeta/origen:/carpeta/destino nginx* Si agregamos :ro el interior será de solo lectura

</br>

	> docker run -p 80:80 -d -v /carpeta/origen:/carpeta/destino:ro nginx* Ejecutar un programa interno de un contenedor

</br>

	> docker exec -it nombre_contenedor nombre_programa* Si agregamos

</br>

	> docker run -p 80:80 -d -v /carpeta/origen:/carpeta/destino nginx* Para crear una imagen

</br>

	> docker build -t wepabackend .* Para detener todos los contenedores


</br>

    > docker stop $(docker ps -a -q)////////////////////


</br>

#### Docker compose

</br>

    > docker-compose up -d
