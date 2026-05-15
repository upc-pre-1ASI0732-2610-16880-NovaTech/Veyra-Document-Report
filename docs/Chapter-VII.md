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

Los componentes del pipeline para la entrega continua a entornos intermedios (*stages*) se estructuran de la siguiente manera y se encuentran orquestados a través de nuestro archivo de workflow (ej. `.github/workflows/cd-staging.yml`):

* **Source Code Checkout:** El pipeline se activa automáticamente mediante un trigger `on: push` o `pull_request` hacia ramas de integración (por ejemplo, `develop` o `release`) en GitHub.
* **Build Stage:** Etapa de compilación del código fuente. Para el backend, se restauran paquetes de NuGet y se compila el proyecto ASP.NET Core con C#. Para el frontend, se instalan dependencias y se empaqueta la aplicación en Vue.
* **Test Stage:** Ejecución automatizada de *Core Entities Unit Tests* y *Core Integration Tests*. Si alguna prueba falla, el pipeline se interrumpe y notifica al equipo.
* **Artifact Generation:** Creación de los artefactos desplegables (binarios listos para la nube en el backend y archivos estáticos minificados en el frontend).
* **Deploy to Staging:** Despliegue automático del artefacto generado en el entorno de pre-producción (Azure App Service Staging Slot) para habilitar las pruebas de aceptación.

## 7.3. Continuous deployment

El objetivo de Continuous Deployment (CD) es que los cambios aprobados en el código pasen automáticamente desde el entorno de desarrollo hasta la producción. Esto garantiza que cada nueva versión sea entregada a los usuarios finales sin intervención manual, siempre y cuando pase todas las métricas de calidad y pruebas establecidas por el equipo.

### 7.3.1. Tools and Practices.

En esta sección se detallan las herramientas y prácticas que aseguran un despliegue a producción automatizado, rápido y confiable.

**Tools:**
* **GitHub Actions:** Para automatizar el pipeline de despliegue final. Esta herramienta permite configurar *workflows* que integran el pase automático a producción al detectar cambios integrados en la rama `main` del repositorio de la organización NovaTech en GitHub.
* **Azure App Service:** Como plataforma de despliegue para la aplicación backend (RESTful API) desarrollada en ASP.NET Core con C#. Permite gestionar la infraestructura de forma automática y configurar las variables de entorno de forma segura en la sección *Configuration* del servicio.
* **Azure Cosmos DB:** Como servicio de base de datos NoSQL en la nube. Permite gestionar el clúster compatible con MongoDB, configurando reglas de firewall y proporcionando la cadena de conexión segura para el backend.
* **Plataforma de Hosting Estático (ej. Azure Static Web Apps / Vercel):** Utilizada para alojar y servir el Landing Page (HTML/CSS/JS) y la aplicación web Frontend en Vue.

**Practices:**
* **Despliegues sin tiempo de inactividad (Zero-downtime deployment):** Redirección del tráfico de usuarios hacia la nueva versión solo cuando el despliegue se ha completado y verificado.
* **Monitoreo Continuo:** Supervisión de la salud del sistema inmediatamente después del pase a producción para detectar anomalías.
* **Reversión automatizada (Rollback):** Capacidad del pipeline de volver a la última versión estable si las pruebas del sistema fallan en el entorno productivo.

### 7.3.2. Production Deployment Pipeline Components.

Esta sección describe los componentes que forman parte del pipeline de despliegue a producción para los distintos artefactos del ecosistema. Todo este proceso se define en el workflow principal (ej. `.github/workflows/cd-production.yml`).

**Componentes de Pipeline de la Base de Datos (Azure Cosmos DB):**
1. **Aprovisionamiento del clúster:** Al crear el recurso en el portal de Azure, se relaciona Azure Cosmos DB for MongoDB con el tipo de clúster vCore, configurando los parámetros de nombre de cuenta, grupo de recursos y opciones de rendimiento.
2. **Configuración de reglas de acceso (Firewall):** Habilitación del acceso exclusivo desde las direcciones IP de la aplicación backend desplegada en Azure, denegando el tráfico público no autorizado.
3. **Conexión desde el backend:** La aplicación en ASP.NET Core se conecta mediante la cadena de conexión de Cosmos DB, la cual se configura como una variable de entorno oculta en la sección *Configuration* de Azure App Service, garantizando que no quede expuesta en GitHub.
4. **Despliegue continuo de esquema:** Dado que MongoDB es una base de datos orientada a documentos, las modificaciones en el modelo de datos se reflejan automáticamente con la nueva versión del backend. Las nuevas colecciones se crean en tiempo de ejecución.

**Componentes de Pipeline del Backend (ASP.NET Core RESTful API):**
1. **Integración y Trigger:** Al aprobar un *Pull Request* hacia la rama `main` del repositorio de GitHub, se dispara automáticamente el flujo de *Continuous Deployment*.
2. **Build & System Tests:** GitHub Actions restaura las dependencias, compila la solución y ejecuta los *Core System Tests* para asegurar que el código es estable y seguro para producción.
3. **Publicación del proyecto:** El pipeline ejecuta el empaquetado del proyecto (vía `dotnet publish`) generando el artefacto final optimizado para el entorno en la nube.
4. **Deploy a Producción:** Utilizando la acción oficial de Azure para GitHub, el artefacto se publica automáticamente sobre el recurso de Azure App Service en su *slot* de producción, reemplazando la versión anterior.

**Componentes de Pipeline del Frontend (Vue App & Landing Page):**
1. **Trigger:** Un *Merge* hacia la rama `main` en los repositorios de las aplicaciones web desencadena el *workflow* de producción en GitHub Actions.
2. **Build & Optimize:** El pipeline instala las dependencias de Node, ejecuta validaciones de calidad estática y transpila el código de Vue construyendo los archivos estáticos minificados (`html`, `css`, `js`).
3. **Deploy a Producción:** Los archivos resultantes de la carpeta de construcción (`dist`) se suben automáticamente al servicio de alojamiento frontend en la nube, quedando disponibles de inmediato para los usuarios finales.
   
## 7.4. Continuous Monitoring
### 7.4.1. Tools and Practices
### 7.4.2. Monitoring Pipeline Components
### 7.4.3. Alerting Pipeline Components
### 7.4.4. Notification Pipeline Components.
