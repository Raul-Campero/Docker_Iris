# Docker_Iris

Hola, bienenido a este repositorio.

Aquí encontrarás como conectar una API REST con ejercicios de Machine Learning del conjunto datos Iris Dataset.

Los créditos correspondientes son de: [gitbook/miguelevangelista/api-rest-and-machine-learning/docker](https://miguelevangelista.gitbook.io/herramientasavanzadas/ejemplos/api-rest-and-machine-learning/docker)

Referencia de la definición de [dockerfile](https://docs.docker.com/reference/dockerfile/)

## Docker

Es una plataforma para desarrollar, empaquetar y ejecutar aplicaciones dentro de contenedores.

Un **contenedor** es una manera de empaquetar nuestras aplicaciones y también todas las dependencias que tenga, incluyendo sus archivos de configuración.

## Agregar archivos

Se dará por visto que ya se cuenta con una carpeta llamada machine__learning_api en donde agregaremos nuestros archivos. 

Los archivos se pueden subir a un editor de texto como _Visual Studio Code_.

Si se opta por utilizar ese IDE (editor de texto) se deben guardar los archivos de la siguiente manera:

* `dockerfile` (se debe guardar así como viene este ejemplo)
* `docker-compe.yml` (segundo archivo que se debe guardar)

### Dockerfile

Un dockerfile es un documento de texto que contiene todos los comandos, el usuario podría llamar a la línea de comandos para ensamblar una imagen.

El archivo de `dockerfile` debe contener lo siguiente:

```
FROM python:3.10

# Establece como directorio de trabajo dentro del contenedor
WORKDIR /app

# Copiar archivos
COPY app.py .
COPY models/ ./models/

# Instalar dependencias
RUN pip install flask joblib scikit-learn

# Ejecuta el puerto 5001 del contendor
EXPOSE 5001

# Comando de inicio
CMD ["python", "app.py"]
```
### Docker-compe.yml

Docker-compose es una herramienta para definir y ejecutar aplicaciones de varios contenedores.
Es ideal para aplicaciones que necesitan varios servicios, como una API con Flask y una base de datos.

El archivo de `docker-compose.yml` debe contener lo siguiente:

```
version: "3.8"

services:
  iris-api:
    build: .
    ports:
      - "5001:5001"
    volumes:
      - ./models:/app/models
```

_Nota_: Todo el contenido de los archivos lo puedes copiar y pegar a tu editor de texto.

# Levantar Docker

1) Se debe abrir Desktop

2) Se debe ejecutar `docker-compose up --build` en la terminal (consola) y en la carpeta `machine__learning_api`
