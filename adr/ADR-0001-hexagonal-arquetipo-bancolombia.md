# ADR-0001: Arquitectura Hexagonal + Plugin Bancolombia

- **Fecha**: 2025-08-22
- **Estado**: aceptada

## Contexto
Se requiere una base que fomente separación de dominios, testeabilidad y adaptabilidad tecnológica.

## Decisión
Usar el arquetipo de Bancolombia *scaffold-clean-architecture* como base de cada microservicio (WebFlux), con capas:
- Dominio (entidades, casos de uso)
- Entry Points (REST, SQS/Lambda)
- Driven Adapters (RDS, DynamoDB, SQS)

## Consecuencias
+ Estandariza estructura y prácticas.
+ Facilita pruebas y mantenimiento.
- Curva de aprendizaje para el equipo.
