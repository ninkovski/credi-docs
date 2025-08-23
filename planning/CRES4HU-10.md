---
title: CRES4HU-10 - Historia 10 - Despliegue de la solución
---

# 📂 Semana

4

# 🎯 Descripción de negocio

Como equipo de desarrollo necesito desplegar la aplicación en un entorno de producción para que las funcionalidades puedan ser probadas por el negocio.

# 🛠️ Descripción técnica

\- Las imágenes de Docker se publican en ECR.\
- Los servicios se despliegan en ECS con Fargate.\
- Se configura un ELB para distribuir las solicitudes HTTP entrantes.\
- Se configura un API Gateway como punto de entrada de la aplicación\
- Se implementa el Auto Scaling para que los servicios puedan escalar
horizontalmente según la demanda (ej. CPU o cantidad de solicitudes).\
- Se configuran las reglas de Health Check en el ELB (se agrega
librerias como actuator para que nos muestre los health check) para
asegurar que el tráfico solo se envíe a los contenedores que están
funcionando correctamente.\
- Se implementa una RDS para usar una base de datos relacional
distribuida.\
- Se configuran alarmas en CloudWatch para notificar sobre fallos en los
servicios.\
- Toda excepción que se produzca debe ser manejada y procesada, para que
la usuario que usa la api no le lleguen mensajes inesperados

# ✅ Criterios de aceptación

\- Todas las APIs son accesibles y funcionales en un entorno de
producción.\
- El sistema permanece operativo durante picos de tráfico.
