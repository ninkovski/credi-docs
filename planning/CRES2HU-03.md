---
title: CRES2HU-03 - Historia 3 - Agregar Autenticación al sistema
---

# 📂 Semana

2

# 🎯 Descripción de negocio

Como administrador/asesor/cliente necesito agregar la autenticación al sistema para poder acceder a las funcionalidades que le corresponden a mi rol y exponer mis servicios solo a usuarios logiados

# 🛠️ Descripción técnica

\- microservicio AUTENTICACION con WebFlux.\
- El endpoint (POST /api/v1/login)\
- Debe seguir los principios de la arquitectura hexagonal, separando el dominio de la infraestructura.\
- El microservicio AUTENTICACION debe manejar la generación de tokens (por ejemplo, JWT).\
- Se deben agregar logs de traza para monitorear\
- toda excepción que se produzca debe ser manejada y procesada, para que la usuario que usa la api no le lleguen mensajes inesperados

# ✅ Criterios de aceptación

\- El inicio de sesión es a través de correo y clave.\
- Se debe validar usuario y contraseña correcta.\
- El número de intentos debe ser ilimitado.\
- Una vez iniciada la sesión, se debe garantizar que con esa sesión
iniciada, cada usuario tiene los permisos para realizar las acciones que
le correspondan a su rol.\
- Agregar validacion de autenticacion a los siguientes endpoint:\
\-- si registro un usuario validar que la persona que llamo el servicio
sea un usuario admin/asesor.\
\-- si creo una solicitud de prestamo, validar que la persona que llamo
el servicio sea un cliente y solo pueda crear solicitudes de prestamo a
el mismo.\
Nota: En esta versión de la aplicación, no está contemplada la
recuperación de contraseña.
