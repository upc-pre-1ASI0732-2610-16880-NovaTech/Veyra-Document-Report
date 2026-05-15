# Capítulo VII: DevOps Practices
## 7.1. Continuous Integration
### 7.1.1. Tools and Practices.
### 7.1.2. Build & Test Suite Pipeline Components.
## 7.2. Continuous Delivery

Continuous Delivery (CD) es una práctica de desarrollo que permite que los equipos entreguen software de forma continua y segura a los clientes. El objetivo principal de CD es reducir el tiempo entre la escritura del código y su disponibilidad en un entorno de pruebas o *staging*, asegurando que el software esté siempre en un estado desplegable y listo para el paso a producción.

### 7.2.1. Tools and Practices.

En esta sección se detallan las herramientas y prácticas utilizadas para mantener un flujo constante de entregas hacia los entornos intermedios.

**Tools:**
* **GitHub Actions:** Plataforma principal de integración y entrega continua (CI/CD) utilizada en el proyecto. Permite automatizar flujos de trabajo directamente desde el repositorio de NovaTech en GitHub. Con GitHub Actions, se crean *workflows* personalizados para compilar, probar y desplegar el código cada vez que se integran cambios en ramas clave.
* **Azure App Service (Staging Slots):** Servicio de alojamiento web que permite crear entornos de *staging* o pre-producción. Facilita la validación del sistema completo en un entorno idéntico al de producción antes del lanzamiento final.

**Practices:**
* **Automatización de despliegues:** Permite publicar nuevas versiones del software en entornos intermedios de manera rápida y consistente mediante *pipelines* automatizados, minimizando el error humano.
* **Pruebas automatizadas (Testing Suites):** Consiste en la ejecución estricta de pruebas unitarias y de integración de manera automática. El código no avanza al entorno de entrega si no supera estas validaciones.
* **Gestión de la configuración:** Mantener la paridad de configuración entre entornos, asegurando que las variables y credenciales de *staging* estén correctamente separadas de las de desarrollo y producción.

### 7.2.2. Stages Deployment Pipeline Components.
## 7.3. Continuous deployment
### 7.3.1. Tools and Practices.
### 7.3.2. Production Deployment Pipeline Components.
## 7.4. Continuous Monitoring
### 7.4.1. Tools and Practices
### 7.4.2. Monitoring Pipeline Components
### 7.4.3. Alerting Pipeline Components
### 7.4.4. Notification Pipeline Components.
