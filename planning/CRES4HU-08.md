---
title: CRES3HU-08 - Historia 8 - Mostrar Cantidad de prestamos
---

# 📂 Semana

4

# 🎯 Descripción de negocio

Como administrador, quiero ver en un panel la cantidad total de solicitudes aprobadas para entender la tracción del negocio.

# 🛠️ Descripción técnica

\- microservicio REPORTES con WebFlux.\
- El endpoint (GET /api/v1/reportes)\
- Usará una base de datos DynamoDB.\
- Debe seguir los principios de la arquitectura hexagonal, separando el
dominio de la infraestructura.\
- El microservicio SOLICITUDES debe enviar un evento a SQS cada vez que
se aprueba una solicitud.\
- El microservicio REPORTES debe consumir estos eventos para actualizar
el contador en DynamoDB.\
- Se deben agregar logs de traza para monitorear\
- toda excepción que se produzca debe ser manejada y procesada, para que
la usuario que usa la api no le lleguen mensajes inesperados\
- el microsericio de REPORTES debe tener su docker y estar en
docker-compose

# ✅ Criterios de aceptación

\- El sistema muestra un número actualizado que representa la cantidad
total de préstamos aprobados.\
- La actualización de este número es casi en tiempo real, con una
latencia mínima.\
- Debe persistirse un registro que se actualice a medida que van
llegando mas prestamos aprobados
