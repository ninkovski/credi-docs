---
title: CRES4HU-09 - Historia 9 - Mostrar Monto total de prestamo
---

# 📂 Semana

4

# 🎯 Descripción de negocio

Como administrador Necesito un reporte que me muestre el monto total de todos los préstamos aprobados para tener una visión clara del capital que se ha prestado.

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
la usuario que usa la api no le lleguen mensajes inesperados

# ✅ Criterios de aceptación

\- El sistema muestra un número actualizado que representa el monto
total de todos los préstamos aprobados.\
- El reporte debe ser preciso y reflejar el estado actual del negocio.\
- Debe persistirse un registro que se actualice a medida que van
llegando mas prestamos aprobados
