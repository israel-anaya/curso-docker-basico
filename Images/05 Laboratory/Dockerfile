# Indicamos que la base de nuestra imagen sera nginx
FROM httpd:latest
LABEL author="Israel Anaya"

# Copia nuestro index.html 
COPY index.html /usr/local/apache2/htdocs

# Copia y extrae las imagenes del archivo en la ruta destino dela imagen
ADD images.tar /usr/local/apache2/htdocs