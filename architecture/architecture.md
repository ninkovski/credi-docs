# 📐 Arquitectura Detallada – CrediYa

La plataforma está organizada en **microservicios independientes** bajo un enfoque **hexagonal**, permitiendo escalabilidad y mantenibilidad.

---

## 🔹 Actores
- **Solicitante** → Persona que aplica al crédito.
- **Administrador** → Valida, aprueba o rechaza las solicitudes.

---

## 🔹 Microservicios y Lambdas

### 1. Autenticación
- Registro e inicio de sesión.
- Persistencia: **BD Autenticación (RDS)**.
- Expuesto como API síncrona (WebFlux).

### 2. Solicitudes
- Creación y gestión de solicitudes de préstamo.
- Estado inicial: pendiente.
- Persistencia: **BD Solicitudes (RDS)**.

### 3. Capacidad de Endeudamiento (Lambda)
- Evalúa automáticamente si el cliente puede asumir el crédito.
- Comunicación asíncrona con **Solicitudes**.

### 4. Notificaciones (Lambda + SQS)
- Envía correos o mensajes SMS según cambios de estado.
- Manejado de forma desacoplada.

### 5. Reportes
- Consultas y reportes del negocio.
- Persistencia: **DynamoDB**.

---

## 🔹 Bases de datos
- **RDS (PostgreSQL)** → transacciones y usuarios.
- **DynamoDB (NoSQL)** → analítica y reportes.

---

## 🔹 Comunicación
- **Síncrona**: llamadas HTTP reactivas con WebFlux.
- **Asíncrona**: AWS SQS + Lambda (ejemplo: notificaciones).

---

## 🔹 Diagrama general
![Arquitectura](./architecture/architecture.png)

---

## 🔹 Futuras extensiones
- Integración con sistemas externos de scoring crediticio.
- Despliegue automatizado con pipelines CI/CD en AWS.
- Observabilidad centralizada con CloudWatch + Grafana.
