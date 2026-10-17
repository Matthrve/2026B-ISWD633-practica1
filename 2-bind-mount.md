# BIND MOUNT
En un bind mount mapeamos (montar) un directorio o archivo específico del sistema de archivos del host con una parte del sistema de ficheros del contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```
ó
```
docker run -d --name <nombre contenedor> --mount type=bind,source=<ruta carpeta host>,target=<ruta carpeta contenedor> <imagen>
```
- destination, dst, target: La ruta donde se monta el archivo o directorio en el contenedor.
- source, src: El origen del montaje.
  
### En tu computador crear una carpeta llamada nginx y dentro de esta carpeta crea otra llamada html. Como se aprecia en la figura.
![Volúmenes](directorio.PNG)

### Crear un contenedor con la imagen nginx:alpine, mapear todos por puertos, para la ruta carpeta host colocar el directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html (esta ruta se obtiene al revisar la documentación de la imagen)
![Volúmenes](volumen-host.PNG)
# COMPLETAR CON EL COMANDO
docker run -d --name mi_nginx -p 8080:80 -v "C:\EPN\SextoSemestre\Construccion_&_Evolucion_SW\Practicas\Practica1\nginx\html:/usr/share/nginx/html" nginx:alpine
### ¿Qué sucede al ingresar al servidor de nginx?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Al entrar al navegador en http://localhost:8080, el servidor responde pero muestra un mensaje de error 403 Forbidden. Esto ocurre porque la carpeta que compartimos desde el host está vacía y Nginx no encuentra un archivo que mostrar. 
### ¿Qué pasa con el archivo index.html del contenedor?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
El index.html que trae Nginx por defecto queda oculto y reemplazado. Al montar la carpeta local, Nginx ya no usa su archivo interno, sino únicamente lo tengamos en la carpeta del host.
### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html
### ¿Qué sucede al ingresar al servidor de nginx?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
El servidor ya no da error, ahora carga y muestra el template completo como página principal.
### Eliminar el contenedor
# COMPLETAR CON EL COMANDO
docker rm -f mi_nginx
### ¿Qué sucede al crear nuevamente un contenedor montado al directorio definidos anteriormente?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA


