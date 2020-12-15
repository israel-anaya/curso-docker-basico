
# Para mas información sobre instrucciones del Dockerfile: https://docs.docker.com/engine/reference/builder/

# La instrucción FROM inicializa una nueva etapa de construcción y establece la imagen base 
# para instrucciones posteriores. Un Dockerfile válido debe comenzar con una instrucción FROM. 
# La imagen puede ser cualquier imagen válida; es especialmente fácil comenzar usando una imagen de los repositorios públicos.

# Indicamos que la base de nuestra imagen sera la versión adoptopen
FROM adoptopenjdk:8-jre-openj9
LABEL author="Israel Anaya"

# La instrucción USER especifica el nombre de usuario (o UID), que se usara para las instrucciónes RUN, CMD y ENTRYPOINT
# Sintaxis: USER <user>

# Especifica que usaremos root para las operaciones de aqui en adelante 
USER root

# La instrucción ENV configura una variable de ambiente dentro de nuestra imagen Docker 
# Sintaxis: ENV <key> <value>

# Configuramos la variables de ambiente que usaremos en nuestra imagen docker
ENV SPRING_BOOT_HOME /usr/spring-boot-app
ENV SPRING_BOOT_LOG /var/log/spring-boot-app
ENV SPRING_BOOT_USER sbapp
ENV SPRING_BOOT_GROUP sbapp
ENV SPRING_BOOT_ARTIFACT_NAME spring-boot-application.jar
ENV JAVA_OPTS -Djava.security.egd=file:/dev/./urandom -XX:+UnlockExperimentalVMOptions -XX:+UseCGroupMemoryLimitForHeap -XX:MaxRAMFraction=1

ENV TZ America/Mexico_City
ENV LANG es_MX.UTF-8
ENV LANGUAGE es_MX.UTF-8
ENV LC_ALL es_MX.UTF-8

# Actualizamos, creamos el usuario el grupo así como los directorios en la imagen Docker
RUN apt-get update \
	&& apt-get install -y --no-install-recommends tzdata \
	&& locale-gen es_MX.UTF-8 && update-locale \
	&& addgroup --system ${SPRING_BOOT_GROUP} && adduser --system ${SPRING_BOOT_USER} --ingroup ${SPRING_BOOT_GROUP} \ 
	&& mkdir -p ${SPRING_BOOT_HOME} \
	&& chown -R ${SPRING_BOOT_USER} ${SPRING_BOOT_HOME} \
	&& chgrp -R ${SPRING_BOOT_GROUP} ${SPRING_BOOT_HOME} \
	&& mkdir -p ${SPRING_BOOT_LOG} \
	&& chown -R ${SPRING_BOOT_USER} ${SPRING_BOOT_LOG} \
	&& chgrp -R ${SPRING_BOOT_GROUP} ${SPRING_BOOT_LOG}

# Copiamos nuestra aplicación a la imagen
COPY discovery-server.jar ${SPRING_BOOT_HOME}/${SPRING_BOOT_ARTIFACT_NAME}

# La instrucción WORKDIR configura el directorio de trabajo de las instrucciones RUN, CMD, ENTRYPOINT, ADD y COPY
# Sintaxis: WORKDIR <path>

# Establecemos el directorio de trabajo para el contenedor (Será el directorio de trabajo de nuestra aplicación)
WORKDIR $SPRING_BOOT_HOME

# Especifica que usaremos el nuevo usuario, con este usuario ejecutará la aplicación de Java
USER $SPRING_BOOT_USER

# Configuramos nuestra ejecutable
ENTRYPOINT java $JAVA_OPTS ${JAVA_OPTS_MEM} -jar ${SPRING_BOOT_HOME}/${SPRING_BOOT_ARTIFACT_NAME} ${SPRING_OPTS}