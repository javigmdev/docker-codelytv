## Primeros pasos

1. Ejecuta un contenedor interactivo basado en la imagen de ubuntu:

   ```
   docker run -it ubuntu
   ```

   - _docker run_: crea y ejecuta contenedores a partir de imágenes
   - _-it_: opciones combinadas del comando _run_.
     - _-i_/_--iteractive_: permite mantener abierto el canal de entrada estándar del contenedor, lo que permite la interacción con el mismo
     - _-t_/_--tty_: asigna un pseudo-TTY (terminal) al contenedor, lo que hace que la interacción sea más fácil y cómoda
   - _ubuntu_: nombre de la imagen que se utiliza para crear el contenedor. En este caso, se está utilizando la imagen oficial de ubuntu desde el registro de Docker Hub

<br>

2. Mostrar los contenedores en ejecución
   ```
   docker ps
   ```

<br>

3. Mostrar log de un contenedor en ejecución

   ```
   docker logs CONTAINER_ID
   ```

<br>

4. Parar el contenedor
   ```
   docker stop CONTAINER_ID
   ```

<br>

5. Si se vuelve a ejecutar de nuevo el mismo comando _docker run_ de antes, se crearía otro contenedor en lugar de usarse el mismo. Para arrancar un contenedor creado que no esté en ejecución:

   1. Mostrar los contenedores, incluyendo los detenidos

   ```
   docker ps -a
   ```

   2. Arrancar el contenedor detenido

   ```
   docker start -i CONTAINER_ID
   ```

6. Borrar un contenedor
   ```
   docker rm CONTAINER_ID
   ```
