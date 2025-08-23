---
title: CRES1HU-01 - Historia 1 - Registrar usuarios en el sistema
---

# 📂 Semana

1

# 🎯 Descripción de negocio

Como administrador/asesor del sistema, quiero registrar un nuevo usuarios proporcionando  sus datos personales básicos, incluyendo nombres y apellidos por separado, para mantener un registro claro y ordenado de los clientes potenciales.

# 🛠️ Descripción técnica

\- microservicio AUTENTICACION con WebFlux.\
- El endpoint (POST /api/v1/usuarios)\
- Debe seguir los principios de la arquitectura hexagonal, separando el dominio de la infraestructura.\
- La persistencia de datos debe ser transaccional para garantizar la atomicidad de la operación de guardado (ej. usando anotaciones \@Transactional).\
- Se deben agregar logs de traza para monitorear\
- toda excepción que se produzca debe ser manejada y procesada, para que
el usuario que usa la api no le lleguen mensajes inesperados


# ✅ Criterios de aceptación

\- Se debe poder registrar un nuevo solicitante proporcionando sus datos personales: nombres, apellidos, fecha_nacimiento, direccion, telefono, correo_electronico y salario_base.\
- El sistema debe validar que los campos nombres, apellidos, correo_electronico y salario_base no sean nulos o vacíos.\
- El sistema debe validar que el correo_electronico proporcionado no esté previamente registrado por otro solicitante.\
- El sistema debe validar el formato correcto de los datos, como por ejemplo, que el salario_base sea un valor numérico (este entre 0 y 15000000) y el correo_electronico tenga un formato de email válido.\
- Una vez registrado exitosamente, la información del solicitante debe quedar guardada permanentemente en la base de datos.
