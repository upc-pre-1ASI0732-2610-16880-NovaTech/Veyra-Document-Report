# Capítulo VII: DevOps Practices
## 7.1. Continuous Integration

La Integración Continua (CI) es una práctica fundamental que permite a los desarrolladores de **NovaTech** integrar su código en un repositorio compartido de forma frecuente. Cada integración es verificada por un proceso automático de compilación y pruebas para detectar errores lo antes posible.

### 7.1.1. Tools and Practices.

Durante el desarrollo y validación del backend de VeyraPlatform se emplearon herramientas y prácticas orientadas al aseguramiento de la calidad del software, con el propósito de garantizar la estabilidad técnica de la aplicación, la correcta compilación del código fuente y la ejecución confiable de pruebas automatizadas. La estrategia adoptada no se limitó únicamente a verificar la construcción del sistema, sino que también buscó comprobar el comportamiento de los principales componentes funcionales dentro de un entorno de pruebas controlado.

El backend fue implementado con **Java 25** y **Spring Boot**, mientras que Maven se utilizó como herramienta de gestión de dependencias, compilación y ejecución del ciclo de pruebas. La suite automatizada se organizó en el directorio estándar <code>src/test/java</code>, respetando la arquitectura del proyecto basada en bounded contexts. Esta organización facilita la trazabilidad entre los módulos funcionales del sistema y sus respectivas pruebas, además de contribuir a la mantenibilidad y escalabilidad de la estrategia de validación.

Con la finalidad de aislar el entorno de pruebas respecto del entorno real de ejecución, se configuró un perfil específico denominado test. Dicho perfil permite cargar propiedades de configuración seguras y controladas, evitando el uso de credenciales reales y la conexión a servicios externos. En este contexto, se utilizó H2 Database como base de datos en memoria para pruebas de persistencia, así como valores dummy para propiedades relacionadas con autenticación, documentación y servicios externos. De igual forma, se emplearon mocks para impedir llamadas reales a servicios de terceros como Stripe y Cloudinary.

La estrategia de testing fue diseñada con un enfoque de aseguramiento de calidad, incorporando diferentes niveles de validación según la naturaleza del componente evaluado. En la suite actual se incluyeron pruebas de arranque del contexto de Spring Boot, pruebas unitarias, pruebas de integración livianas, pruebas de controladores REST mediante MockMvc y pruebas de persistencia con H2. Todas estas pruebas fueron organizadas en función de los bounded contexts reales del sistema: <code>activities</code>, <code>analytics</code>, <code>hcm</code>, <code>health</code>, <code>iam</code>, <code>nursing</code>, <code>payments</code>, <code>profiles</code>, <code>shared</code> y <code>tracking</code>.

Las herramientas y prácticas principales utilizadas en este proceso se presentan en la siguiente tabla.

<table border="1" cellspacing="0" cellpadding="6" width="100%"> <thead> <tr> <th>Herramienta / Práctica</th> <th>Tipo</th> <th>Descripción</th> <th>Propósito dentro del proyecto</th> </tr> </thead> <tbody> <tr> <td>JUnit 5</td> <td>Framework de pruebas automatizadas</td> <td>Herramienta utilizada para definir, estructurar y ejecutar casos de prueba en Java.</td> <td>Permite validar de manera repetible el comportamiento de clases, métodos y componentes del backend.</td> </tr> <tr> <td>Spring Boot Test</td> <td>Soporte para pruebas de integración</td> <td>Módulo de Spring Boot que permite cargar el contexto de la aplicación durante la ejecución de pruebas.</td> <td>Verifica la correcta configuración de beans, inyección de dependencias y propiedades del sistema.</td> </tr> <tr> <td>Mockito</td> <td>Framework de simulación</td> <td>Herramienta utilizada para crear mocks y simular dependencias internas o externas.</td> <td>Facilita la prueba aislada de servicios sin depender de repositorios, APIs o infraestructura real.</td> </tr> <tr> <td>MockMvc</td> <td>Pruebas de controladores REST</td> <td>Utilidad de Spring que permite simular solicitudes HTTP sin desplegar la aplicación en un servidor real.</td> <td>Valida endpoints REST, códigos de respuesta, estructura del JSON y manejo de errores.</td> </tr> <tr> <td>H2 Database</td> <td>Base de datos en memoria</td> <td>Motor de base de datos temporal utilizado exclusivamente durante la ejecución de pruebas.</td> <td>Permite validar la persistencia sin conectarse a una base de datos externa.</td> </tr> <tr> <td>Maven</td> <td>Herramienta de build</td> <td>Herramienta utilizada para compilar el proyecto, resolver dependencias y ejecutar el ciclo de pruebas.</td> <td>Automatiza la validación técnica del backend mediante el comando <code>./mvnw test</code>.</td> </tr> <tr> <td>Spring Profiles</td> <td>Gestión de configuración por ambiente</td> <td>Mecanismo de Spring Boot para separar configuraciones según el entorno de ejecución.</td> <td>Permite ejecutar pruebas con el perfil <code>test</code>, evitando dependencias del entorno real.</td> </tr> <tr> <td>@MockBean</td> <td>Mocking dentro del contexto Spring</td> <td>Anotación utilizada para reemplazar beans reales por implementaciones simuladas dentro del contexto.</td> <td>Evita la inicialización de servicios externos durante pruebas que requieren cargar el contexto de Spring.</td> </tr> <tr> <td>Dummy Properties</td> <td>Aislamiento de configuración externa</td> <td>Uso de valores ficticios para propiedades relacionadas con JWT, Stripe, Cloudinary y OpenAPI.</td> <td>Permite ejecutar pruebas sin exponer secretos reales ni depender de servicios externos.</td> </tr> <tr> <td>Testing por bounded context</td> <td>Práctica de organización</td> <td>Estructuración de pruebas según los contextos funcionales reales del dominio.</td> <td>Mejora la trazabilidad, mantenibilidad y claridad del alcance cubierto por la suite automatizada.</td> </tr> </tbody> </table>


El uso combinado de estas herramientas permitió establecer una estrategia de pruebas controlada, segura y repetible. Al reemplazar dependencias externas por mocks, utilizar una base de datos en memoria y definir un perfil exclusivo de pruebas, se redujo el riesgo de fallos asociados a infraestructura externa y se fortaleció la validación técnica del backend antes de avanzar hacia etapas posteriores del ciclo de desarrollo.

### 7.1.2. Build & Test Suite Pipeline Components.

El componente Build & Test Suite Pipeline del backend de VeyraPlatform se implementó sobre el ciclo de vida de Maven, con el objetivo de compilar el proyecto, resolver dependencias y ejecutar automáticamente la suite de pruebas ubicada en src/test/java. Este proceso permite validar de forma temprana que la aplicación pueda construirse correctamente y que su configuración base sea consistente antes de continuar con etapas posteriores de integración o despliegue.

Como parte de esta estrategia, se mantuvo la clase <code>VeyraPlatformApplicationTests</code>.java, ubicada en <code>src/test/java/com/novaperutech/veyra/platform/</code>. Esta clase utiliza <code>@SpringBootTest</code> y <code>@ActiveProfiles("test")</code>, e incluye el método shouldLoadApplicationContext(), cuyo propósito es verificar que el contexto general de Spring Boot pueda inicializarse correctamente bajo el perfil de pruebas. Este tipo de prueba funciona como un smoke test, ya que permite detectar fallos de configuración, errores de inyección de dependencias, propiedades faltantes o problemas durante la creación de beans.

No obstante, la validación del backend no se limita únicamente a la carga del contexto. La suite de pruebas fue reorganizada de acuerdo con los bounded contexts reales del sistema, incorporando pruebas unitarias, pruebas de integración livianas, pruebas de controladores REST mediante MockMvc y pruebas de persistencia con H2 cuando corresponde. Esta reorganización mejora la mantenibilidad, la trazabilidad y la cobertura funcional del backend.

Durante la configuración del pipeline se identificaron dependencias hacia infraestructura externa, tales como Stripe, Cloudinary, JWT y componentes de persistencia. Para evitar conexiones reales durante la ejecución de pruebas, se empleó una base de datos H2 en memoria, propiedades dummy en <code>application-test.properties</code> y mocks para los servicios externos que no debían inicializarse ni consumir recursos reales. Como resultado, la suite puede ejecutarse en un entorno aislado, seguro y reproducible.

La ejecución de la suite se realizó mediante el siguiente comando:

```text
./mvnw test
```
Como resultado de la ejecución, Maven reportó 35 pruebas ejecutadas, 0 fallos, 0 errores y 0 pruebas omitidas. El proceso finalizó con el mensaje BUILD SUCCESS, lo cual confirma que el backend pudo compilarse correctamente y que la suite automatizada validó satisfactoriamente la configuración y el comportamiento esperado de los principales bounded contexts bajo el perfil test.

Tabla 7.1. Componentes del pipeline de build y pruebas del backend
<table> <thead> <tr> <th>Componente del pipeline</th> <th>Descripción</th> <th>Resultado esperado</th> </tr> </thead> <tbody> <tr> <td>Compilación del código fuente</td> <td>Maven compila las clases ubicadas en <code>src/main/java</code>.</td> <td>El código fuente principal compila sin errores.</td> </tr> <tr> <td>Compilación de pruebas</td> <td>Maven compila las clases definidas en <code>src/test/java</code>.</td> <td>Las clases de prueba son reconocidas y compiladas correctamente.</td> </tr> <tr> <td>Activación del perfil de pruebas</td> <td>Se utiliza el perfil <code>test</code> mediante <code>@ActiveProfiles("test")</code>.</td> <td>La aplicación se ejecuta con una configuración aislada del entorno real.</td> </tr> <tr> <td>Persistencia en memoria</td> <td>Se emplea H2 para las pruebas que requieren acceso a datos.</td> <td>Las pruebas de persistencia se ejecutan sin conexión a una base de datos externa.</td> </tr> <tr> <td>Smoke test del contexto</td> <td>Se ejecuta <code>shouldLoadApplicationContext()</code> con <code>@SpringBootTest</code>.</td> <td>El contexto general de Spring Boot inicia correctamente.</td> </tr> <tr> <td>Pruebas unitarias</td> <td>Se validan servicios y lógica de negocio con JUnit 5 y Mockito.</td> <td>Los componentes funcionales responden correctamente en escenarios positivos y negativos.</td> </tr> <tr> <td>Pruebas de controladores</td> <td>Se validan endpoints REST mediante <code>MockMvc</code>.</td> <td>Los controladores devuelven estados HTTP y respuestas acordes a lo esperado.</td> </tr> <tr> <td>Pruebas de repositorio</td> <td>Se validan operaciones de persistencia con <code>@DataJpaTest</code> y H2.</td> <td>Los repositorios funcionan correctamente en un entorno controlado.</td> </tr> <tr> <td>Servicios externos simulados</td> <td>Se mockean o aíslan servicios como Stripe y Cloudinary.</td> <td>No se realizan conexiones reales a infraestructura externa.</td> </tr> <tr> <td>Ejecución automatizada con Maven</td> <td>Se ejecuta el comando <code>./mvnw test</code>.</td> <td>Maven ejecuta la suite automatizada completa.</td> </tr> <tr> <td>Resultado del build</td> <td>Maven reporta el resumen final de la ejecución.</td> <td>El proceso concluye con <code>BUILD SUCCESS</code>.</td> </tr> </tbody> </table>

![Figura 7.1. Ejecución exitosa de la suite de pruebas con Maven](../assets/img/chapter-VII/image%20copy.png)


**Figura 7.1. Ejecución exitosa del ciclo de pruebas del backend mediante Maven. El resultado muestra 35 pruebas ejecutadas, 0 fallos, 0 errores y estado final BUILD SUCCESS.**

Adicionalmente, la suite fue reorganizada siguiendo la arquitectura por bounded contexts del backend. Cada módulo funcional dispone de una carpeta específica dentro de <code>src/test/java/com/novaperutech/veyra/platform/</code>, lo que permite mantener una separación clara entre los contextos del sistema y facilita la trazabilidad entre el código productivo y las pruebas asociadas.

La organización contempla los bounded contexts reales del proyecto: <code>activities</code>, <code>analytics</code>, <code>hcm</code>, <code>health</code>, <code>iam</code>, <code>nursing</code>, <code>payments</code>, <code>profiles</code>, <code>shared</code> y <code>tracking</code>. Esta estructura posibilita la implementación ordenada de pruebas unitarias, pruebas de integración livianas, pruebas de controladores y pruebas de repositorios, evitando una distribución desorganizada o excesivamente dependiente de detalles internos de implementación.

La siguiente tabla resume la suite automatizada implementada por bounded context.

Tabla 7.2. Resumen de la suite de pruebas por bounded context
<table> <thead> <tr> <th>Bounded Context</th> <th>Tipo de prueba</th> <th>Clase de prueba</th> <th>Objetivo validado</th> </tr> </thead> <tbody> <tr> <td>Platform</td> <td>Smoke Test</td> <td><code>VeyraPlatformApplicationTests</code></td> <td>Validar que el contexto general de Spring Boot cargue correctamente bajo el perfil <code>test</code>.</td> </tr> <tr> <td>Activities</td> <td>Unit Test</td> <td><code>ActivitiesServiceUnitTest</code></td> <td>Validar la creación de actividades y el manejo de escenarios donde no existe el residente asociado.</td> </tr> <tr> <td>Analytics</td> <td>Unit Test</td> <td><code>AnalyticsServiceUnitTest</code></td> <td>Validar consultas o métricas del módulo analítico y el rechazo de entradas inválidas.</td> </tr> <tr> <td>HCM</td> <td>Unit Test</td> <td><code>HcmServiceUnitTest</code></td> <td>Validar operaciones básicas del módulo y el manejo de escenarios sin resultados.</td> </tr> <tr> <td>Health</td> <td>Unit Test</td> <td><code>HealthServiceUnitTest</code></td> <td>Validar consultas de salud y el tratamiento de escenarios donde no existe información asociada.</td> </tr> <tr> <td>IAM</td> <td>Unit Test / Controller Integration Test</td> <td><code>IamAuthenticationUnitTest</code>, <code>IamAuthenticationControllerIntegrationTest</code></td> <td>Validar autenticación, credenciales inválidas, creación de usuarios y respuesta HTTP de endpoints mediante MockMvc.</td> </tr> <tr> <td>Nursing</td> <td>Unit Test</td> <td><code>NursingServiceUnitTest</code></td> <td>Validar consultas de residentes y el manejo de escenarios donde no se encuentra la entidad esperada.</td> </tr> <tr> <td>Payments</td> <td>Unit Test con mocks</td> <td><code>PaymentCommandServiceUnitTest</code></td> <td>Validar el procesamiento de pagos y el manejo de errores de Stripe sin llamadas reales al servicio externo.</td> </tr> <tr> <td>Profiles</td> <td>Unit Test / Repository Integration Test</td> <td><code>ProfilesServiceUnitTest</code>, <code>ProfilesStorageUnitTest</code>, <code>ProfilesRepositoryIntegrationTest</code></td> <td>Validar creación, actualización, almacenamiento de imágenes y persistencia de perfiles mediante H2 y mocks.</td> </tr> <tr> <td>Shared</td> <td>Unit Test</td> <td><code>SharedNamingStrategyUnitTest</code></td> <td>Validar componentes compartidos de configuración o comportamiento reutilizable del backend.</td> </tr> <tr> <td>Tracking</td> <td>Unit Test</td> <td><code>TrackingServiceUnitTest</code></td> <td>Validar consultas de dispositivos y recuperación de listas filtradas dentro del módulo de tracking.</td> </tr> </tbody> </table>

![Figura 7.2. Estructura de carpetas de pruebas organizada por bounded context](../assets/img/chapter-VII/image%20copy%203.png)

**Figura 7.2. Estructura de carpetas de la suite de pruebas automatizadas organizada por bounded context bajo src/test/java/com/novaperutech/veyra/platform, lo que mejora la trazabilidad, mantenibilidad y claridad de la estrategia de testing del backend.**

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

El Monitoreo Continuo permite a **NovaTech** supervisar la salud, el rendimiento y la disponibilidad de la solución en tiempo real, garantizando que el sistema opere según los niveles de servicio esperados.

### 7.4.1. Tools and Practices

**Tools:**
* **Azure Monitor:** Servicio integral para recopilar y analizar datos de telemetría de la infraestructura en la nube.
* **Application Insights:** Herramienta específica para el monitoreo de aplicaciones web que rastrea tasas de error, tiempos de respuesta y dependencias.
* **Log Analytics:** Para el almacenamiento y consulta de logs detallados de la aplicación y el servidor.

**Practices:**
* **Rastreo de Excepciones:** Identificación y diagnóstico de errores en tiempo de ejecución para reducir el tiempo medio de reparación.
* **Uptime Monitoring:** Verificación constante de la disponibilidad de los endpoints de la API y del sitio web.
* **Performance Profiling:** Análisis de la latencia y el consumo de recursos para optimizar la experiencia del usuario.

### 7.4.2. Monitoring Pipeline Components

Los componentes del pipeline de monitoreo aseguran que la información fluya desde la aplicación hasta el equipo de desarrollo:
* **Ingestión de Telemetría:** Recopilación automática de solicitudes HTTP, tiempos de carga y eventos personalizados desde el frontend y el backend.
* **Agregación de Logs:** Consolidación de registros de eventos en un repositorio centralizado para facilitar auditorías y diagnósticos.
* **Dashboards de Salud:** Visualización en tiempo real de métricas críticas como el consumo de CPU y el rendimiento de la base de datos.

### 7.4.3. Alerting Pipeline Components
### 7.4.4. Notification Pipeline Components.
