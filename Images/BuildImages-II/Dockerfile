
# Para mas información sobre instrucciones del Dockerfile: https://docs.docker.com/engine/reference/builder/

# La instrucción FROM inicializa una nueva etapa de construcción y establece la imagen base 
# para instrucciones posteriores. Un Dockerfile válido debe comenzar con una instrucción FROM. 
# La imagen puede ser cualquier imagen válida; es especialmente fácil comenzar usando una imagen de los repositorios públicos.

# Indicamos que la base de nuestra imagen sera alpine
FROM alpine:latest
LABEL author="Israel Anaya"


# La instrucción RUN es para ejecutar comandos en una nueva capa de la imagen. El resultado de esta ejecución será usado para los siguientes pasos del Dockerfile
# Cabe aclarar que estos comando son ejecutados dentro de la imagen de Docker
# Sintaxis: RUN <command>

# Ejecuta una serie de comando dentro del contenedor (actualiza el OS e instala el comando curl) 
RUN apk --no-cache --update upgrade \
    && apk --no-cache add curl



# La instrucción ENTRYPOINT permite configurar el ejecutable que ejecuta el contenedor al crearse
# Sintaxis: ENTRYPOINT <command> <param1> <param2> ...

# Ejecuta el comando curl para mostrar lo headers del sitio www.google.com
ENTRYPOINT curl -I http://www.google.com