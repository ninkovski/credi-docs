# 🏗️ Arquitectura del Sistema (visión)

- Microservicios independientes (repos separados)
- Comunicación:
  - HTTP síncrono entre `autenticacion` y `solicitudes`
  - SQS asíncrono para eventos (`aprobado`, `rechazado`, etc.)
- Procesos:
  - Validación automática en Lambda (capacidad)
  - Notificaciones en Lambda + SNS
- Reportes materializados en DynamoDB

> Ver ADR-0001 para justificación del arquetipo Bancolombia + hexagonal.
