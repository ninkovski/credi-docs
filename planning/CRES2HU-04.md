---
title: CRES2HU-04 - Historia 4 - Agregar contenerización a los microservicios
---

# 📂 Semana

2

# 🎯 Descripción de negocio

Como Asesor Quiero ver un listado de todas las solicitudes que necesitan mi revisión  aquellas que están "Pendiente de revisión", "Rechazadas", "Revision manual") para tomar la decisión final.	

# 🛠️ Descripción técnica

\- El endpoint (GET /api/v1/solicitud)\
- roles que pueden usar este endpoint (Asesor).\
- Debe seguir los principios de la arquitectura hexagonal, separando el dominio de la infraestructura.\
- Se deben agregar logs de traza para monitorear.\
- toda excepción que se produzca debe ser manejada y procesada, para que la usuario que usa la api no le lleguen mensajes inesperados.

# ✅ Criterios de aceptación

\- El sistema muestra una lista paginada y filtrable de solicitudes pendientes de la decisión del administrador.\
- Debe retornar un listado de solicitudes (monto, plazo, email, nombre, tipo_prestamo, tasa_interes, estado_solicitud, salario_base, deuda_total_mensual_solicitudes_aprobadas).
