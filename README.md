# Ejecutar jenkin para usar Docker del Host

docker run -p 8080:8080 -p 50000:50000 -d --name jenkinsv1 -v /var/run/docker.sock:/var/run/docker.sock -v jenkins_home:/var/jenkins_home  --restart=always jenkins/jenkins:alpine

# Conectarse al contenedor con usuario root

docker exec -it --user root jenkinsv1 sh

# Instalar Docker en Jenkins

apk update
apk add docker-cli

# Validar grupo Docker

ls -l /var/run/docker.sock

Veremos algo similar : srw-rw---- 1 root root 0 Jun 27 20:04 /var/run/docker.sock

# Crear grupo Docker y agregar usuario Jenkins al grupo Docker

# addgroup docker
# addgroup jenkins docker
# chgrp docker /var/run/docker.sock
# chmod 660 /var/run/docker.sock
# docker restart jenkinsv1
