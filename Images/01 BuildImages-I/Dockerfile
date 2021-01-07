
# Para mas información sobre instrucciones del Dockerfile: https://docs.docker.com/engine/reference/builder/

# La instrucción FROM inicializa una nueva etapa de construcción y establece la imagen base 
# para instrucciones posteriores. Un Dockerfile válido debe comenzar con una instrucción FROM. 
# La imagen puede ser cualquier imagen válida; es especialmente fácil comenzar usando una imagen de los repositorios públicos.

# Indicamos que la base de nuestra imagen sera nginx
FROM nginx:latest
LABEL author="Israel Anaya"

# La instrucción COPY es usada para copiar archivos desde el almacenamiento local a el destino de la imagen Docker
# Sintaxis: COPY <source> <destination>

# Copia nuestro index.html 
COPY index.html /usr/share/nginx/html


# La instrucción ADD es usada para copiar archivos y directorios dentro de una imagen docker. Este puede copiar los datos de tres formas:

# Copia los archivos desde el almacenamiento local a el destino dentro de la imagen Docker
# Copia un tarball (.tar) desde el almacenamiento local y extrae su contenido a el destino dentro de la imagen Docker
# Copia los archivos de una URL a el destino dentro de la imagen Docker

# Sintaxis: ADD <source> <destination>

# Copia y extrae las imagenes del archivo en la ruta destino dela imagen
ADD images.tar /usr/share/nginx/html