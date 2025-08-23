---
title: CRES3HU-05 - Historia 5 - Agregar contenerización a los microservicios
---

# 📂 Semana

3

# 🎯 Descripción de negocio

Como equipo de desarrollo Necesito que cada microservicio de nuestro sistema (SOLICITUDES, AUTENTICACION) esté empaquetado en un contenedor Docker, y que todos puedan ser orquestados para funcionar juntos como un único servicio en un entorno local. Esto asegurará que la aplicación funcione de manera uniforme en cualquier entorno.

# 🛠️ Descripción técnica

\- Se crea un Dockerfile para cada microservicio.\
- Se crea un archivo docker-compose.yml que define la red, los servicios
de aplicación y las bases de datos (por ejemplo, MySQL).\
- La aplicación dentro del contenedor debe exponer el puerto correcto y
ser accesible.\
- Se valida que los microservicios se comuniquen correctamente entre
ellos utilizando los nombres de los servicios definidos en el archivo de
Docker Compose (por ejemplo, la URL para el servicio de riesgo sería
http://evaluacion-riesgo:8080).\
- Se valida que las bases de datos persistan la información
correctamente, incluso después de reiniciar los contenedores.\
- toda excepción que se produzca debe ser manejada y procesada, para que
la usuario que usa la api no le lleguen mensajes inesperados

# ✅ Criterios de aceptación

\- Todos los microservicios (SOLICITUDES, AUTENTICACION) pueden ser
ejecutados de forma local dentro de contenedores Docker.\
- El comportamiento de cada microservicio dentro del contenedor es
idéntico a su comportamiento al ser ejecutado de forma nativa.\
- La aplicación completa (SOLICITUDES llamando a AUTENTICACION) puede
ser levantada con un solo comando en el entorno local.
