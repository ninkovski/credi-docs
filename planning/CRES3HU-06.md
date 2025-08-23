---
title: CRES3HU-06 - Historia 6 - Aprobar o rechazar solicitud de credito
---

# 📂 Semana

3

# 🎯 Descripción de negocio

Como asesor, quiero poder aprobar o rechazar manualmente las solicitudes para tomar la decisión final. Como solicitante, quiero ser notificado por correo electrónico con la decisión final.

# 🛠️ Descripción técnica

\- microservicio SOLICITUDES con WebFlux.\
- El endpoint (PUT /api/v1/solicitud)\
- roles que pueden usar este endpoint (Asesor)\
- Al actualizar el estado a \'Aprobado\' o \'Rechazado\', el microservicio SOLICITUDES debe enviar un mensaje a una cola de SQS.\
- Se creará una lambda de NOTIFICACIONES. Este debe escuchar los mensajes de SQS y utilizar SNS para el envío del correo electrónico.\
- Se deben agregar logs de traza para monitorear\
- toda excepción que se produzca debe ser manejada y procesada, para que la usuario que usa la api no le lleguen mensajes inesperados

# ✅ Criterios de aceptación

\- Se puede cambiar el estado de una solicitud a \'Aprobada\' o \'Rechazada\'.\
- Al cambiar el estado, el solicitante recibe una notificación por correo electrónico con la decisión final.\
- El proceso de cambio de estado y la notificación deben ser consistentes.
