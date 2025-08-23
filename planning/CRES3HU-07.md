---
title: CRES3HU-07 - Historia 7 - Agregar al sistema prestamo con validación
  automatica
---

# 📂 Semana

3

# 🎯 Descripción de negocio

Como sistema de análisis de crédito, quiero calcular la capacidad de endeudamiento DISPONIBLE de un solicitante (restando sus cuotas de préstamos activos), para tomar una decisión de aprobación o rechazo más precisa y responsable.

# 🛠️ Descripción técnica

\- Lambda CAPACIDAD DE ENDEUDAMIENTO\
- El endpoint (POST /api/v1/calcular-capacidad)\
- Debe seguir los principios de la arquitectura hexagonal, separando el dominio de la infraestructura.\
- La lambda de calcular capacidad debe responder con un resultado claro (ej. \'APROBADO\', \'RECHAZADO\') que el microservicio de solicitudes utilizará para actualizar el estado.\
- La actualización del estado de la solicitud en la base de datos de solicitudes debe ser una operación atómica.\
- Se deben agregar logs de traza para monitorear\
- toda excepción que se produzca debe ser manejada y procesada, para que
la usuario que usa la api no le lleguen mensajes inesperados

# ✅ Criterios de aceptación

\- Si se crea una solicitud con un tipo de prestamo que tenga habilita la opción de \'validacion_automatica\', el sistema debera encolar la petición desde el microservicio SOLICITUDES, para que la lambda de CAPACIDAD DE ENDEUDAMIENTO lo procese\

- Cálculo de la Capacidad de Endeudamiento Máxima:\
\-- Se establece una política de riesgo donde un solicitante no puede
destinar más del 35% de sus ingresos totales al pago de deudas.\
\-- Fórmula: CapacidadEndeudamientoMaxima = IngresosTotales \* 0.35\

- Cálculo de Deuda Mensual Actual:\
\-- El sistema debe tener el estado de todos los préstamos del
solicitante que tengan un estado = \'Aprobado\'.\
\-- Para cada préstamo activo encontrado, se debe calcular su cuota
mensual utilizando la fórmula de amortización.\
\-- Se suman todas las cuotas calculadas para obtener el total de las
obligaciones mensuales actuales.\
\-- Fórmula: DeudaMensualActual =
SUM(CuotaMensual_de_cada_prestamo_activo)\

- Cálculo de la Capacidad de Endeudamiento Disponible:\
\-- Es la capacidad máxima menos las deudas que el solicitante ya tiene
activas.\
\-- Fórmula: CapacidadDisponible = (CapacidadEndeudamientoMaxima -
DeudaMensualActual)\

- Cálculo de la Cuota del Nuevo Préstamo y Decisión Final:\
\-- Se calcula la cuota mensual para el nuevo préstamo que se está
evaluando (CuotaPrestamoNuevo).\
\-- Fórmula de Cuota: Cuota=P(1+i)n−1i(1+i)n Donde: P= Monto, i= Tasa de
interés mensual, n= Plazo en meses.\

- Lógica de Decisión:\
\-- SI CuotaPrestamoNuevo ≤ CapacidadDisponible ➔ El préstamo se
APRUEBA.\
\-\-- Si se aprueba y el prestamo es de mas de 5 salarios de la persona,
queda en estado \'REVISION MANUAL\'\
\-- SI CuotaPrestamoNuevo \> CapacidadDisponible ➔ El préstamo se
RECHAZA.\

- Debe responder por correo al usuario el plan de pago, osea el listado
de todas las cuotas que debe pagar diferenciando el abono a capital del
pago de intereses.
