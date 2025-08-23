---
title: CRES5HU-11 - Historia 11 - Generación de reportes de rendimiento de forma
  programada
---

# 📂 Semana

5

# 🎯 Descripción de negocio

Como administrador quiero visualizar el rendimiento total del negocio, por medio de un correo. Esto me permitirá tomar decisiones estratégicas de manera informada. 

# 🛠️ Descripción técnica

\- El proceso está implementado de forma reactiva y no bloqueante,
usando la programación funcional de WebFlux con Mono y Flux.\
- Se configura una tarea programada que se dispara automáticamente.\
- La lógica de agregación y procesamiento de datos se realiza de manera
eficiente en un flujo reactivo.\
- toda excepción que se produzca debe ser manejada y procesada, para que
la usuario que usa la api no le lleguen mensajes inesperados

# ✅ Criterios de aceptación

\- Enviar un correo consolidando la información de cantidad de prestamos
aprobados y monto total prestado.\
- Se genera enviara automaticamente a las 8pm
