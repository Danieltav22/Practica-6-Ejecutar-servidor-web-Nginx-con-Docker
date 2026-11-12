# Práctica 1: servidor web Nginx con Docker Compose

Materia: Electiva 2

## Objetivo
Ejecutar Nginx en un contenedor local y mostrar una página con el mensaje Hola mundo.

## Archivos
- `src/index.html`: página web.
- `docker-compose.yml`: configuración del servidor y del directorio compartido.

## Requisitos
Docker Desktop instalado y en ejecución, usando contenedores Linux.

## Ejecutar en Windows
1. Extraer el ZIP.
2. Abrir la carpeta que contiene `docker-compose.yml` en el Explorador de archivos.
3. Escribir `cmd` en la barra de direcciones y presionar Enter.
4. Ejecutar:

```cmd
docker compose up -d
```

5. Visitar http://localhost:8080 y comprobar que aparece Hola mundo.
6. Revisar el contenedor:

```cmd
docker compose ps
```

La primera ejecución requiere internet para descargar la imagen de Nginx.

## Configuración
- `image`: utiliza la imagen oficial `nginx:stable-alpine`.
- `ports`: conecta el puerto 8080 de este PC con el puerto 80 del contenedor. Se publica solo en la interfaz local 127.0.0.1.
- `volumes`: comparte `./src` con `/usr/share/nginx/html`, donde Nginx busca las páginas.
- `ro`: permite al contenedor leer los archivos compartidos sin modificarlos.
- `-d`: deja el contenedor ejecutándose en segundo plano.

Al cambiar `src/index.html`, guardar y actualizar el navegador para ver el cambio.

## Detener
Desde la misma carpeta:

```cmd
docker compose down
```

## Subir a GitHub con GitHub Desktop
1. File > New repository.
2. Nombre sugerido: `electiva2-practica1-nginx`. Activar la creación de un README.
3. Crear el repositorio y abrir su carpeta con Repository > Show in Explorer.
4. Copiar allí `docker-compose.yml`, la carpeta `src` y este `README.md`, reemplazando el README inicial.
5. En GitHub Desktop, escribir el resumen `Agregar practica de Nginx con Docker Compose` y pulsar Commit to main.
6. Pulsar Publish repository, desmarcar Keep this code private y publicar.
7. Abrir View on GitHub y copiar la URL pública del repositorio para el foro.

Subir los archivos extraídos; no subir únicamente el ZIP.

## Evidencias sugeridas
Guardar una captura del navegador mostrando Hola mundo y otra de `docker compose ps` mostrando el servicio activo.

## Si ocurre un error
- Si Docker no responde, abrir Docker Desktop y esperar a que el motor esté listo.
- Si el puerto 8080 está ocupado, cambiar el mapeo a `127.0.0.1:8081:80`, ejecutar otra vez `docker compose up -d` y visitar http://localhost:8081.
- Si aparece la página predeterminada de Nginx, revisar que `src/index.html` exista y que se esté ejecutando Compose desde la carpeta correcta.

## Referencias
- https://docs.docker.com/compose/gettingstarted/
- https://hub.docker.com/_/nginx

La verificación de funcionamiento debe realizarse en el PC donde se ejecute Docker Desktop.
