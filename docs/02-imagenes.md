## Imágenes

Ver las imágenes descargadas en el sistema

```
docker images
```

Crear una imagen a partir de un Dockerfile

```
docker build -t IMAGE_NAME DOCKERFILE_DIRECTORY

docker build -t codelytv-hello-world .
```

- _-t_: para asignar un nombre a la imagen resultante
- .: directorio actual

Crear una imagen a partir de un Dockerfile que no tiene como nombre Dockerfile

```
docker build -t IMAGE_NAME DOCKERFILE_DIRECTORY -f DOCKERFILE_NAME

docker build -t codelytv-hello-world . -f Dockerfile_custom_extension
```

- _-f_: indicar nombre Dockerfile

Ejecutar un contenedor basado en en la imagen _codely-tv-helloworld_ en modo interactivo y exportar el puerto 80 del contenedor en el puerto 8000 del host

```
docker run --rm -p 8000:80 -it "codely-tv-helloworld"
```

- _--rm_: para que se borre el contenedor automáticamente después de que se detenga la ejecución
- _p 8000:80_: mapea el puerto 80 del contenedor al puerto 8000 del host, lo que permite acceder a la aplicación que se está ejecutando dentro del contenedor a través del puerto 8000

Hacer una solicitud http y mostrar la respuesta del contenedor

```
curl -i localhost:8000/

Hello CodelyTV!
```

<br>

### Variables de entorno para configurar el contenedor

- Se utilizan para configurar y pasar información a los contenedores durante su creación y ejecución.
- Son pares de clave-valor que se pueden utilizar para personalizar la configuración de una aplicación o para proporcionar información específica que el contenedor necesita para funcionar correctamente
- Formas de definir y usar
  - En el Dockerfile con las instrucción _ENV_, lo que permite establecer valores predeterminados para variables que se usarán dentro del contenedor
    ```
    FROM ubuntu
    ENV MY_VARIABLE=value
    ```
  - Al ejecutar el contenedor, utilizando _-e_ o _--env_ seguido del nombre de la variable y su valor. Si la variable ya existe en el _Dockerfile_, se usa la que se establece en el _docker run_
    ```
    docker run -e MY_VARIABLE=value MY_IMAGE
    ```
  - Crear un archivo con las variables de entorno
    ```
    # env_file.txt
    MY_VARIABLE=value
    ```
    y usar _--env-file_ al ejecutar el contenedor
    ```
    docker run --env-file env_file.txt MY_IMAGE
    ```
