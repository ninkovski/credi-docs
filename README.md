# 📘 CrediYa – Documentación (credi-docs)

Este repositorio centraliza la **planeación, estándares y avances** del proyecto **CrediYa**.

---

## 🏦 Enunciado del Proyecto

**CrediYa** es una plataforma que busca **digitalizar y optimizar la gestión de solicitudes de préstamos personales**, eliminando la necesidad de procesos manuales y presenciales.

El sistema permitirá a los solicitantes ingresar sus datos y la información del préstamo que desean.  
Una vez enviada la solicitud, el sistema realizará una **evaluación inicial automatizada** para determinar su viabilidad. Posteriormente, un **administrador** podrá revisar los casos pre-aprobados y tomar la decisión final.

### Funcionalidades Clave
- **Gestión de tipos de préstamos:** los administradores pueden crear, editar y eliminar productos de crédito.
- **Proceso de solicitud:** los solicitantes pueden enviar su información y la del préstamo deseado.
- **Capacidad de endeudamiento:** evaluación automática para aprobar o rechazar solicitudes.
- **Gestión de usuarios:** roles de solicitantes y administradores con permisos diferenciados.
- **Notificaciones automáticas:** comunicación sobre el estado de solicitudes.
- **Reportes de rendimiento:** métricas de negocio como préstamos aprobados.
- **Eficiencia y transparencia:** central en la experiencia del usuario.

---
# 🏗️ Arquitectura de CrediYa

CrediYa está construida bajo un **modelo de microservicios desacoplados**, combinando comunicación **síncrona (HTTP con WebFlux)** y **asíncrona (SQS + Lambdas)**.  
Cada microservicio gestiona su propio dominio y base de datos.

## 🔹 Componentes principales
- **Frontend Web** → interfaz para solicitantes y administradores.  
- **Microservicio de Autenticación** → registro e inicio de sesión, conectado a **BD Autenticación (RDS)**.  
- **Microservicio de Solicitudes** → registro y gestión de créditos, conectado a **BD Solicitudes (RDS)**.  
- **Lambda Capacidad de Endeudamiento** → evaluación automática de viabilidad crediticia.  
- **Lambda Notificaciones + SQS** → envío de correos y notificaciones de estado.  
- **Microservicio de Reportes** → métricas y estadísticas, conectado a **DynamoDB**.  

## 🔹 Comunicación
- **Síncrona**: entre microservicios usando WebFlux (ej: Solicitudes ↔ Autenticación).  
- **Asíncrona**: usando AWS SQS y Lambdas (ej: Notificaciones).  

📌 Para más detalle: ver [`/architecture/architecture.md`](./architecture/architecture.md)

### Reglas Técnicas
- Cada microservicio será un repositorio independiente.
- Arquitectura basada en el **modelo hexagonal**.
- Desarrollo con **Spring WebFlux** (reactivo).
- Cada Historia de Usuario (HU) implementada en su **rama única** siguiendo **Gitflow**.
- Validación de código con **SonarLint**.
- APIs documentadas con **Swagger/OpenAPI**.
- **Pruebas unitarias** obligatorias.
- Buenas prácticas de programación: nombramiento claro, manejo de constantes, métodos pequeños.
- Comunicación asíncrona con **SQS**.
- Despliegue en **AWS ECS con Fargate** + **API Gateway**.
- Persistencia de datos:
  - **RDS (PostgreSQL):** datos transaccionales.
  - **DynamoDB:** reportes.
- Versionamiento y CI/CD con **Docker + AWS ECR**.

---

## ✅ ¿Cómo evoluciona esta documentación?

- Todo cambia y se versiona.  
- Cada semana (📌 **Épica**) actualizamos los `.md` con avances reales.  
- Las PRs a este repo deben seguir los estándares en [Estándares](./standards).  
- Cambios semanales etiquetados con tags: `CRES1-Registro`, `CRES<n>-<tema>`, etc.  

👉 **Semana = Épica**. Cada semana agrupa varias Historias de Usuario (HU).

---

## 🔀 Flujo de ramas

Crear `release/release/CRES<n>HU-<n>` desde `develop`
Consulta la guía completa en [branching.md](./standards/branching.md).

---

## 🗺️ Índice de Documentación

### [Planeación](./planning)
- `/planning/CRES1HU-01.md` – Semana 1 (HU-1)
- `/planning/CRES1HU-02.md` – Semana 1 (HU-2)
- 
- `/planning/CRES2HU-03.md` – Semana 2 (HU-3)
- `/planning/CRES2HU-04.md` – Semana 2 (HU-4)
- 
- `/planning/CRES3HU-05.md` – Semana 3 (HU-5)
- `/planning/CRES3HU-06.md` – Semana 3 (HU-6)
- `/planning/CRES3HU-07.md` – Semana 3 (HU-7)
- 
- `/planning/CRES4HU-08.md` – Semana 4 (HU-8)
- `/planning/CRES4HU-09.md` – Semana 4 (HU-9)
- `/planning/CRES4HU-10.md` – Semana 4 (HU-10)
- 
- `/planning/CRES5HU-11.md` – Semana 5 (HU-11)

### [Estándares](./standards)
- `/standards/branching.md` – Estrategia de ramas
- `/standards/commit-convention.md` – Convención de commits
- `/standards/issues-and-prs.md` – Issues y Pull Requests

### [Arquitectura](./adr)
- `/adr/` – Documentación de decisiones clave (Architecture Decision Records)

---

## 🧩 Microservicios (visión inicial)

- `autenticacion` → síncrono (WebFlux)
- `solicitudes` → síncrono (WebFlux)
- `notificaciones` → asíncrono (SQS + Lambda)
- `capacidad` → asíncrono (Lambda cálculo endeudamiento)
- `reportes` → síncrono (WebFlux + DynamoDB)

---

## 🧱 Tech Stack (resumen)

- **Backend:** Java 17+, Spring WebFlux, SpringDoc OpenAPI  
- **Bases de Datos:** RDS (PostgreSQL), DynamoDB  
- **AWS:** SQS, Lambda, ECS Fargate, API Gateway, ECR, CloudWatch  
- **CI/CD:** Gitflow, Docker, AWS ECR  
- **Calidad:** SonarLint, Unit Testing  

---