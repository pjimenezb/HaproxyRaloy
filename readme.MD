# Haproxy Docker

## Descripción General
Este repositorio contiene los archivos de configuración y los scripts necesarios para implementar una solución robusta y escalable que integra HAProxy como un balanceador de carga. Esta combinación ofrece una plataforma altamente eficiente y confiable para el despliegue de aplicaciones web OXIRUS

![Ha proxy Raloy](image-1.png)

# Instalación 💿

Crear una carpeta certs con permisos

```
mkdir certs && chmod 777 certs && cd certs
```

Crear un certificado Open SSL, o de Cerbot
**📝 Nota: En este caso utilizaremos Open**

```
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout mi-certificado.key -out mi-certificado.crt
cat mi-certificado.crt mi-certificado.key > mi-certificado.pem
```

Finalmente nos vamos a la ruta del docker compose y ejecutamos

```
docker compose up -d 
```

**Permisos Linux en caso de no funcionar el comando directo**
```
sudo apt-get -y install docker-compose

chmod +x ~/.docker/cli-plugins/docker-compose

```

## Vista Web

Nos vamos a la sig ruta: http://localhost:1936/

```
Usuario: admin
Contraseña: 123
```
**📝 Nota: Para productivo se pueden cambiar estas configuraciones en el archivo haproxy.cfg**

La linea se encuentra al final

```
frontend stats
    bind *:1936
    stats enable
    stats uri /
    stats hide-version
    stats auth admin:123 # Esta es la linea a modificar
```

