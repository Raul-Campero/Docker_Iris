# Docker_Iris

Hola, bienenido a este repositorio.

Aquí encontrarás como conectar una API REST con ejercicios de Machine Learning del conjunto datos Iris Dataset.

Los créditos correspondientes al repositorio son: [gitbook/miguelevangelista/api-rest-and-machine-learning/docker](https://miguelevangelista.gitbook.io/herramientasavanzadas/ejemplos/api-rest-and-machine-learning/docker)

## Docker

Es una plataforma para desarrollar, empaquetar y ejecutar aplicaciones dentro de contenedores.

Un **contenedor** es una manera de empaquetar nuestras aplicaciones y también todas las dependencias que tenga, incluyendo sus archivos de configuración.

## Agregar archivos

Se dará por visto que ya se cuenta con una carpeta llamada machine__learning_api en donde agregaremos nuestros archivos. 

Los archivos se pueden subir a un editor de texto como _Visual Studio Code_.

Si se opta por utilizar ese IDE (editor de texto) se deben guardar los archivos de la siguiente manera:

* `dockerfile` (se debe guardar así como viene este ejemplo)
* `docker-compe.yml` (segundo archivo que se debe guardar)

El primer archivo que se agregará es **Dockergfile** es cuál debe contener lo siguiente:

FROM python:3.10

WORKDIR /app

### Copiar archivos
COPY app.py .
COPY models/ ./models/

### Instalar dependencias
RUN pip install flask joblib scikit-learn

EXPOSE 5001

### Comando de inicio
CMD ["python", "app.py"]


