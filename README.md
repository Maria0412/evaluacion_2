# 🎟️ Microservicio de Tickets - CI/CD con DevOps

Este proyecto corresponde a un microservicio desarrollado en **Java 17** y **Spring Boot**, implementando principios de Arquitectura Hexagonal junto con prácticas modernas de **DevOps**, automatización y contenerización.

El objetivo principal es automatizar completamente el ciclo de vida de la aplicación utilizando **GitHub Actions**, **Docker**, **SonarCloud** y **Docker Compose**.

---

# 🚀 Tecnologías Utilizadas

* Java 17
* Spring Boot
* Maven
* Docker
* Docker Compose
* GitHub Actions
* SonarCloud
* PostgreSQL
* GitHub Container Registry (GHCR)

---

# ⚙️ Pipeline CI/CD

El pipeline se ejecuta automáticamente al realizar cambios en la rama principal (`main`) y cuenta con tres etapas principales:

## 🧪 1. Pruebas y Calidad de Código

En esta etapa se ejecutan:

* Pruebas unitarias automatizadas
* Validación del proyecto con Maven
* Análisis estáico de código usando SonarCloud
* Verificación del Quality Gate

Si alguna prueba falla o el análisis de calidad no cumple los requisitos mínimos, el pipeline se detiene automáticamente.

---

## 🐳 2. Construcción de Imagen Docker

La aplicación se empaqueta utilizando Docker mediante una estrategia de **multi-stage build**, permitiendo:

* Reducir el tamaño final de la imagen
* Mejorar la seguridad
* Optimizar el despliegue

La imagen generada se publica automáticamente en:

```bash
ghcr.io/maria0412/evaluacion_2/tickets-app
```

---

## 📦 3. Despliegue Automatizado

Con Docker Compose se levanta un entorno completo compuesto por:

* `tickets_app`
* `tickets_db` (PostgreSQL)

El sistema incorpora:

* Restart Policy
* Límites de memoria y CPU
* Healthchecks
* Variables de entorno seguras mediante GitHub Secrets

---

# 🔍 Trazabilidad

Cada despliegue utiliza el identificador único del commit (`github.sha`), permitiendo rastrear exactamente qué versión del código fue desplegada.

---

# ▶️ Ejecución Local

Para levantar el proyecto localmente:

```bash
docker compose up -d --build
```

Verificar contenedores activos:

```bash
docker ps
```

Ver consumo de recursos:

```bash
docker stats
```

---

# 📌 Reflexión

Este proyecto permitió comprender la importancia de DevOps y la automatización dentro del desarrollo moderno de software. Se aprendió cómo integrar pruebas, análisis de calidad, contenerización y despliegue continuo en un mismo flujo automatizado, mejorando la estabilidad, seguridad y trazabilidad de la aplicación.
