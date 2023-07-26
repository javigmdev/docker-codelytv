# Docker

- Los contenedores son parecidos a las máquinas virtuales en cuanto a que permiten aislar procesos
- Se basa en dos tecnologías de linux

  - **cgroups**: sirven para limitar la cantidad de recursos (cpu, memoria, etc) que un proceso puede utilizar
  - **namespaces**: permiten controlar qué puede ver un proceso dentro del sistema, como ellistado de procesos o el _file system_

- Diferencia entre imagen y contenedor: la imagen es una plantilla que se utiliza para generar un contenedor de dicha imagen

Las imágenes se descargan desde dockerhub: https://hub.docker.com/

**Dockerfile**: archivo de texto simple y sin formato que contiene una serie de instrucciones para crear una imagen. Una imagen es una plantilla que contiene un sistema de archivos y las configuraciones necesarias para ejecutar una aplicación o un servicio dentro de un contenedor
Ejemplo:

```
# Establecer la imagen base
FROM node:14

# Establecer el directorio de trabajo dentro del contenedor
WORKDIR /app

# Copiar los archivos de la aplicación al contenedor
COPY package.json package-lock.json /app/
COPY src /app/src/

# Instalar las dependencias (RUN ejecuta comandos dentro del contenedor)
RUN npm install

# Exponer el puerto que utiliza la aplicación
EXPOSE 3000

# Comando predeterminado para ejecutar la aplicación
CMD ["npm", "start"]
```
