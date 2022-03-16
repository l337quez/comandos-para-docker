### Mis Apuntes de Docker
By: Ronal Forero

<p align="center"><img src="https://github.com/l337quez/comandos-para-docker/blob/main/images/docker.png"></p>  

 <br/>

### Índice 
* [Instalar Docker en GNU Linux ARCH](#install_docker_arch)
* [Correr servicio de Docker](#item1)
* [Levantar Contenedor](#Levantar_Contenedor)
* [Listar imagenes creadas](#view_images)
* [Salir de un contenedor sin parar ejecucion](#out_container)
* [Ver logs del contenedor](#view_logs)
* [Eliminar imagenes](#delete_images)

 <br/>
 
 
 <a name="install_docker_arch"></a>
#### Instalar Docker en GNU Linux ARCH

```
sudo pacman -S docker docker-compose
```

</br>
 
 
<a name="item1"></a>
#### Correr Servicio en Docker

> systemctl start docker.service
 
> systemctl enable docker.service



para correr 
npm start
ahora debe existir el .env

</br>

Toda la informacion del contenedor, todolo referente a el, se encuentra en un archivo  .yml

</br>

Hay una herramienta llamada docker compouse, el encargado de leer los archivos .yml


</br>

<a name="Levantar_Contenedor"></a>
## Levantar un Contenedor
```
> docker-compose up -d
```
<br/>

## Listar contenedores levantados
```
> docker ps
```
<br/>

<br/>

## Listar imagenes
```
>  sudo docker images
```
<br/>

## Entrar a un  contenedor 
Una vez listados los contenedores, podremos ver una informacion de cada uno.  entre esta informacion esta el id del contenedor. Para levantar el contenedor debemos tipear ese id
```
docker exec -i -t aqui_va_el_id /bin/bash
```
o puede ser 
```
docker exec -it aqui_va_el_id /bin/bash
```
<br/>

## Listar conexiones Network
```
> docker network ls
```
<br/>

<a name="out_container"></a>
## Salir de un contenedor sin detener su ejecucion
debemos hacer una combinacion de teclas CTRL + P + Q

<br/>

## Salir de un contenedor 
```
> exit
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

<br/>

## Entrar a mongo dentro de un contendor
Para entrar a mongo en un contenedor, debemos colocar el username y la clave despues del flag
```
> mongo --username username --password password
```

<br/>

## Reiniciar un contenedor

```
> sudo docker restart nombre_del_container
```

<br/>

## Detener un contenedor
Con el siguieten comando detenemos todos los contenedores
```
> sudo docker stop $(docker ps -a -q)
```

<br/>


```
> sudo docker stop nombre_del_contenedor
```

<br/>

## Eliminar un contenedor
Con el siguieten comando ELIMINAMOS todos los contenedores
```
> sudo docker rm $(docker ps -a -q)
```

<br/>

```
> sudo docker rm nombre_del_contenedor
```

<br/>

<a name="view_logs"></a>
## Para ver los Logs de un contenedor
```
> sudo docker logs nombre_contenedor
```

<br/>

Para imprimir un log debemos  poner esto en el codigo
```
Logger.info(`--------> ${nombre_variable}`, 'texto');
```

<br/>

## Detener todos los contenedores usando docker compose
```
sudo docker-compose down
```

<br/>

## Levantar todos los contenedores usando docker compose
```
sudo docker-compose build
```

<br/>


<a name="view_images"></a>
## Ver las imagenes 
```
sudo docker images
```

<br/>

<a name="delete_images"></a>
## Eliminar imagenes
```
sudo docker rmi nombre_imagene
```

<br/>

https://rafaelgamezdiaz.github.io/Docker-Chuleta/
