# Capítulo VI: Product Verification & Validation
## 6.1. Testing Suites & Validation
### 6.1.1. Core Entities Unit Tests.
En esta sección se implementaron y ejecutaron pruebas unitarias para las entidades principales del sistema desarrolladas en Java utilizando el framework Spring Boot. Estas pruebas estuvieron enfocadas en validar el correcto funcionamiento de los modelos, clases de servicio y métodos principales de la aplicación de manera aislada.

El propósito de las pruebas unitarias fue asegurar que cada componente cumpla con los requisitos funcionales establecidos y que su lógica interna opere correctamente ante distintos escenarios de ejecución.

Para la implementación de las pruebas se utilizaron herramientas como:

JUnit 5 para la creación y ejecución de pruebas unitarias.
Mockito para simular dependencias y aislar componentes durante las pruebas.
Spring Boot Test para facilitar la integración de pruebas dentro del entorno Spring.

Las pruebas realizadas permitieron validar:

- La correcta creación y manipulación de entidades.
- El funcionamiento adecuado de métodos de servicios y repositorios.
- La validación de datos de entrada.
- El manejo de excepciones y errores.
- El cumplimiento de reglas de negocio definidas en el sistema.

Además, se emplearon mocks para evitar dependencias externas como conexiones a bases de datos o servicios externos, garantizando que las pruebas se enfoquen únicamente en la lógica de cada componente.

<div align="center">
  <img src="../assets/img/chapter-VI/core-entities-unit-tests.png" alt="Evidencia de core entities unit tests" width="90%">
  <p><em>Figura: Ejecución satisfactoria de las pruebas de entidades principales.</em></p>
</div>


Los resultados obtenidos evidenciaron que las entidades principales del sistema funcionan correctamente bajo los escenarios evaluados, contribuyendo a mejorar la estabilidad, mantenibilidad y confiabilidad de la aplicación.

### 6.1.2. Core Integration Tests.

Las pruebas de integración fueron desarrolladas con el objetivo de validar la correcta comunicación entre los controladores REST, los servicios de aplicación, la configuración de seguridad, la persistencia de datos y las dependencias principales del backend de Veyra. A diferencia de las pruebas unitarias, estas pruebas permiten comprobar el comportamiento del sistema cuando varios componentes trabajan en conjunto dentro del contexto de Spring Boot.

Para esta validación se implementó la clase `CoreIntegrationTests`, orientada a verificar flujos esenciales del sistema, tanto técnicos como funcionales. En particular, se evaluaron procesos de autenticación, generación de token, restricción de acceso a endpoints protegidos, registro de casas de reposo, creación de residentes y registro de medicamentos asociados a un residente.

#### Evidencia de ejecución: `testSuccessfulSignUp()`

Este caso de prueba valida el flujo de **registro exitoso de usuario** dentro del backend de Veyra. La prueba envía una solicitud HTTP `POST` al endpoint de autenticación con datos válidos de usuario, verificando que el sistema pueda procesar el registro correctamente.

| Campo | Descripción |
|---|---|
| ID | ITC-01 |
| Clase de prueba | `AuthenticationControllerIntegrationTest` |
| Método evaluado | `testSuccessfulSignUp()` |
| Flujo relacionado | Registro de usuario |
| Módulos involucrados | Authentication Controller, User Service, repositorio de usuarios y configuración de seguridad |
| Tipo de prueba | Integration Test |
| Entrada | Credenciales válidas de registro |
| Resultado esperado | El sistema registra al usuario y retorna una respuesta HTTP exitosa |
| Estado | Aprobado |

<div align="center">
  <img src="../assets/img/chapter-VI/test1.png" alt="Evidencia de prueba de integración testSuccessfulSignUp" width="90%">
  <p><em>Figura: Ejecución satisfactoria de la prueba de integración para el registro de usuario.</em></p>
</div>

La ejecución satisfactoria de este caso confirma que el backend puede recibir una solicitud de registro, procesarla mediante la lógica de autenticación y devolver una respuesta válida. Esto evidencia la correcta integración entre la capa REST, el servicio de usuarios y la persistencia asociada.

#### Evidencia de ejecución: `testSuccessfulSignIn()`

Este caso de prueba valida el flujo de **inicio de sesión exitoso** dentro del backend de Veyra. La prueba primero registra un usuario de prueba y luego envía una solicitud HTTP `POST` al endpoint de inicio de sesión con credenciales válidas.

| Campo | Descripción |
|---|---|
| ID | ITC-02 |
| Clase de prueba | `AuthenticationControllerIntegrationTest` |
| Método evaluado | `testSuccessfulSignIn()` |
| Flujo relacionado | Inicio de sesión |
| Módulos involucrados | Authentication Controller, User Service, JWT, seguridad y repositorio de usuarios |
| Tipo de prueba | Integration Test |
| Entrada | Usuario registrado y credenciales válidas |
| Resultado esperado | El sistema autentica al usuario y retorna un token de acceso |
| Estado | Aprobado |

<div align="center">
  <img src="../assets/img/chapter-VI/test2.png" alt="Evidencia de prueba de integración testSuccessfulSignIn" width="90%">
  <p><em>Figura: Ejecución satisfactoria de la prueba de integración para el inicio de sesión.</em></p>
</div>

La ejecución satisfactoria de este caso confirma que el backend puede autenticar usuarios registrados y generar una respuesta válida para el acceso al sistema. Este flujo es crítico porque habilita el ingreso seguro a los módulos protegidos de Veyra.

#### Evidencia de ejecución: `testProtectedEndpointWithoutToken()`

Este caso de prueba valida el comportamiento de seguridad del backend cuando se intenta acceder a un endpoint protegido sin enviar un token de autenticación. La prueba realiza una solicitud HTTP `GET` a un recurso protegido sin incluir encabezado `Authorization`.

| Campo | Descripción |
|---|---|
| ID | ITC-03 |
| Clase de prueba | `AuthenticationControllerIntegrationTest` |
| Método evaluado | `testProtectedEndpointWithoutToken()` |
| Flujo relacionado | Protección de endpoints |
| Módulos involucrados | Spring Security, filtros de autenticación, endpoint protegido y configuración JWT |
| Tipo de prueba | Integration Test |
| Entrada | Solicitud sin token de autenticación |
| Resultado esperado | El sistema rechaza la solicitud y retorna una respuesta de no autorizado |
| Estado | Aprobado |

<div align="center">
  <img src="../assets/img/chapter-VI/test3.png" alt="Evidencia de prueba de integración testProtectedEndpointWithoutToken" width="90%">
  <p><em>Figura: Ejecución satisfactoria de la prueba de integración para endpoint protegido sin token.</em></p>
</div>

La ejecución satisfactoria de este caso confirma que el backend aplica correctamente las reglas de seguridad sobre endpoints protegidos. Esto permite validar que los recursos sensibles del sistema no puedan ser consultados por usuarios no autenticados.

#### Evidencia de ejecución: `testSuccessfulCreateNursingHome()`

Este caso de prueba valida el flujo de **registro de una casa de reposo** dentro del backend de Veyra. Este flujo representa el proceso de onboarding institucional, mediante el cual una residencia geriátrica puede quedar registrada en la plataforma para posteriormente gestionar residentes, personal, actividades y servicios asociados.

| Campo | Descripción |
|---|---|
| ID | ITC-04 |
| Clase de prueba | `NursingHomeControllerIntegrationTest` |
| Método evaluado | `testSuccessfulCreateNursingHome()` |
| Flujo relacionado | Registro de casa de reposo |
| Módulos involucrados | Nursing Home Controller, servicio de casas de reposo, persistencia y validaciones de dominio |
| Tipo de prueba | Integration Test |
| Entrada | Datos válidos de la institución geriátrica |
| Resultado esperado | El sistema registra la casa de reposo y retorna una respuesta HTTP exitosa |
| Estado | Aprobado |

<div align="center">
  <img src="../assets/img/chapter-VI/test4.png" alt="Evidencia de prueba de integración testSuccessfulCreateNursingHome" width="90%">
  <p><em>Figura: Ejecución satisfactoria de la prueba de integración para el registro de casa de reposo.</em></p>
</div>

La ejecución satisfactoria de este caso confirma que el backend permite registrar correctamente una institución geriátrica dentro de la plataforma. Esto valida uno de los flujos principales del modelo SaaS de Veyra, ya que cada casa de reposo representa una organización cliente dentro del sistema.

#### Evidencia de ejecución: `testSuccessfulCreateResident()`

Este caso de prueba valida el flujo de **registro de residente** dentro del backend de Veyra. La prueba comprueba que el sistema pueda recibir los datos principales de un adulto mayor y almacenarlos correctamente, permitiendo su posterior gestión clínica, administrativa y asistencial.

| Campo | Descripción |
|---|---|
| ID | ITC-05 |
| Clase de prueba | `ResidentControllerIntegrationTest` |
| Método evaluado | `testSuccessfulCreateResident()` |
| Flujo relacionado | Registro de residente |
| Módulos involucrados | Resident Controller, servicio de residentes, perfil del residente, persistencia y validaciones |
| Tipo de prueba | Integration Test |
| Entrada | Datos válidos del residente |
| Resultado esperado | El sistema registra al residente y retorna una respuesta HTTP exitosa |
| Estado | Aprobado |

<div align="center">
  <img src="../assets/img/chapter-VI/test5.png" alt="Evidencia de prueba de integración testSuccessfulCreateResident" width="90%">
  <p><em>Figura: Ejecución satisfactoria de la prueba de integración para el registro de residente.</em></p>
</div>

La ejecución satisfactoria de este caso confirma que Veyra puede registrar residentes dentro del sistema, lo cual constituye una funcionalidad central para la gestión de casas de reposo. Este flujo es relevante porque permite centralizar la información del adulto mayor y sirve como base para módulos posteriores como seguimiento médico, actividades, comunicaciones familiares y reportes.

#### Evidencia de ejecución: `testSuccessfulRegisterHealthMetric()`

Este caso de prueba valida el flujo de **registro de métricas de salud** de un residente. La prueba comprueba que el sistema pueda recibir y almacenar información clínica relacionada con el seguimiento del adulto mayor, como presión arterial, temperatura, frecuencia cardiaca u otros indicadores relevantes.

| Campo | Descripción |
|---|---|
| ID | ITC-06 |
| Clase de prueba | `HealthTrackingIntegrationTest` |
| Método evaluado | `testSuccessfulRegisterHealthMetric()` |
| Flujo relacionado | Registro de métricas de salud |
| Módulos involucrados | Tracking Controller, servicio de métricas de salud, repositorio de mediciones y persistencia |
| Tipo de prueba | Integration Test |
| Entrada | Datos válidos de una medición clínica |
| Resultado esperado | El sistema registra la métrica de salud y retorna una respuesta HTTP exitosa |
| Estado | Aprobado |

<div align="center">
  <img src="../assets/img/chapter-VI/test6.png" alt="Evidencia de prueba de integración testSuccessfulRegisterHealthMetric" width="90%">
  <p><em>Figura: Ejecución satisfactoria de la prueba de integración para el registro de métricas de salud.</em></p>
</div>

La ejecución satisfactoria de este caso confirma que el backend permite registrar información clínica relevante para el monitoreo del residente. Este flujo se relaciona directamente con el valor de negocio de Veyra, ya que facilita el seguimiento continuo del estado de salud del adulto mayor y contribuye a una toma de decisiones más informada por parte del personal asistencial.

#### Resumen de pruebas de integración ejecutadas

| ID | Caso de prueba | Flujo validado | Enfoque | Resultado |
|---|---|---|---|---|
| ITC-01 | `testSuccessfulSignUp()` | Registro de usuario | Seguridad y acceso | Aprobado |
| ITC-02 | `testSuccessfulSignIn()` | Inicio de sesión y generación de token | Seguridad y acceso | Aprobado |
| ITC-03 | `testProtectedEndpointWithoutToken()` | Bloqueo de acceso sin autenticación | Seguridad de endpoints | Aprobado |
| ITC-04 | `testSuccessfulCreateNursingHome()` | Registro de casa de reposo | Onboarding institucional | Aprobado |
| ITC-05 | `testSuccessfulCreateResident()` | Registro de residente | Gestión del adulto mayor | Aprobado |
| ITC-06 | `testSuccessfulRegisterHealthMetric()` | Registro de métrica de salud | Seguimiento clínico | Aprobado |

Las pruebas de integración ejecutadas permiten validar flujos técnicos y de negocio relevantes para el backend de Veyra. Los casos relacionados con autenticación comprueban el acceso seguro al sistema, mientras que los casos orientados al negocio validan procesos centrales como el registro de instituciones, la gestión de residentes y el seguimiento clínico de adultos mayores.

### 6.1.3. Core Behavior-Driven Development

En esta sección se definen los escenarios de prueba utilizando el lenguaje Gherkin (Given-When-Then) para asegurar que el comportamiento del sistema cumpla con los criterios de aceptación de las Historias de Usuario principales (Core).

#### Epic: Medication Management

**User Story (US14):** As an administrator, I want to control the medication intake of the residents to ensure treatment compliance.

```gherkin
Feature: Health Metric Registration

  Scenario: Administrator successfully registers a medication intake
    Given the administrator is on the medication management module
    And the medication has available stock
    When the administrator registers a new dose intake for the resident
    Then the system should decrease the medication stock by one unit
    And the system should save the date and time of the intake
    And the system should display a "Medication registered successfully" message

  Scenario: Attempting to register a medication intake with no stock
    Given the administrator is on the medication management module
    And the selected medication has zero stock
    When the administrator attempts to register a new dose intake
    Then the system should prevent the registration
    And the system should display an "Out of stock" warning message
```

#### Epic: Family Communication

**User Story (US20):** As a family member, I want to send direct questions to the staff about my relative's daily routine to resolve specific doubts.
```gherkin
Feature: Family Portal Activity Viewing

  Scenario: Family member sends a direct question to the staff
    Given the family member is authenticated in the family portal
    And is viewing their relative's profile
    When the family member submits a question via the direct message form
    Then the system should send the message to the assigned staff member
    And the system should display a "Message sent successfully" confirmation
```

### 6.1.4. Core System Tests.

<div align="center">
  <img src="../assets/img/chapter-VI/Product_Core_1.png" alt="Evidencia de prueba de integración testSuccessfulCreateNursingHome" width="90%">
</div>
<div align="center">
  <img src="../assets/img/chapter-VI/Core_System_Test_1.png" alt="Evidencia de prueba de integración testSuccessfulCreateNursingHome" width="90%">
</div>

<br>
<br>

<div align="center">
  <img src="../assets/img/chapter-VI/Product_Core_2.png" alt="Evidencia de prueba de integración testSuccessfulCreateNursingHome" width="90%">
</div>
<div align="center">
  <img src="../assets/img/chapter-VI/Core_System_Test_2.png" alt="Evidencia de prueba de integración testSuccessfulCreateNursingHome" width="90%">
</div>

<br>
<br>

<div align="center">
  <img src="../assets/img/chapter-VI/Product_Core_3.png" alt="Evidencia de prueba de integración testSuccessfulCreateNursingHome" width="90%">
</div>
<div align="center">
  <img src="../assets/img/chapter-VI/Core_System_Test_3.png" alt="Evidencia de prueba de integración testSuccessfulCreateNursingHome" width="90%">
</div>

<br>
<br>

<div align="center">
  <img src="../assets/img/chapter-VI/Product_Core_4.png" alt="Evidencia de prueba de integración testSuccessfulCreateNursingHome" width="90%">
</div>
<div align="center">
  <img src="../assets/img/chapter-VI/Core_System_Test_4.png" alt="Evidencia de prueba de integración testSuccessfulCreateNursingHome" width="90%">
</div>

<br>
<br>

<div align="center">
  <img src="../assets/img/chapter-VI/Product_Core_11.png" alt="Evidencia de prueba de integración estSuccessfulCreateNursingHome" width="90%">
</div>
<div align="center">
  <img src="../assets/img/chapter-VI/Core_System_Test_5.png" alt="Evidencia de prueba de integración testSuccessfulCreateNursingHome" width="90%">
</div>

## 6.2. Static testing & Verification 
### 6.2.1. Static Code Analysis 
### 6.2.1.1. Coding standard & Code conventions. 
### 6.2.1.2. Code Quality & Code Security. 
### 6.2.2. Reviews 
## 6.3. Validation Interviews. 
### 6.3.1. Diseño de Entrevistas. 

La entrevista tuvo como objetivo conocer la opinión del usuario sobre la aplicación Veyra. Para ello, se le mostraron las principales pantallas y funcionalidades de la plataforma y posteriormente se le preguntó qué le parecía, si la consideraba útil y qué aspectos mejoraría. Se utilizó una entrevista semiestructurada, permitiendo que la participante expresara libremente sus comentarios y recomendaciones. 
Las preguntas principales fueron: 
- ¿Qué te parece la aplicación? 
- ¿Consideras que sería útil para una casa de reposo? - ¿Qué funcionalidad te pareció más importante? 
- ¿Qué aspecto de la aplicación mejorarías? 
- ¿La información presentada te pareció clara?

### 6.3.2. Registro de Entrevistas. 

**Segmento 1: Administrador de casas de reposo**

| Campo | Información |
|---|---|
| Nombre | Lucía |
| Apellido | Carbajal |
| Edad | 19 años |
| Distrito | Surquillo |
| Evidencia | ![Entrevista](../assets/img/chapter-II/entrevista1-validacion.png) |
| Link | [Link Entrevistas](https://upcedupe-my.sharepoint.com/:v:/g/personal/u202210334_upc_edu_pe/IQBIUqqLXAH4SJPzByX9OzdGAUNio18RULQrItvzFyKrt3o?e=qwdetZ&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D) |
| Resumen | **Perfil y experiencia:**<br>Lucía Carbajal es una joven de 19 años que pertenece al segmento relacionado con la administración y gestión de casas de reposo. Ha realizado voluntariado en este tipo de instituciones, experiencia que le permitió conocer de cerca las actividades del personal y las necesidades de atención de los adultos mayores.<br><br>**Percepción y necesidades:**<br>Considera que la aplicación sería útil y de mucha ayuda para las casas de reposo, ya que permitiría organizar, centralizar y consultar la información de los residentes de manera más rápida. También facilitaría las labores del personal al reducir la dependencia de registros manuales y documentos separados.<br><br>**Mejoras propuestas:**<br>Como principal mejora, Lucía propone que la aplicación permita visualizar de manera más clara y detallada la información de los medicamentos, incluyendo sus nombres, dosis y horarios de administración. Asimismo, considera importante mejorar la visualización de los horarios de los trabajadores, para identificar fácilmente sus turnos, disponibilidad y responsabilidades. |

### 6.3.3. Evaluaciones según heurísticas

A continuación, se presenta la evaluación exhaustiva del sistema de la plataforma Veyra basada en las 10 heurísticas de usabilidad de Jakob Nielsen. Esta evaluación nos permite identificar el nivel de madurez de la interfaz y las interacciones del usuario.

| # | Heurística | Cumple (Sí/No/Parcial) | Observación / Evidencia |
|---|---|---|---|
| 1 | Visibilidad del estado del sistema | Sí | El sistema utiliza componentes visuales reactivos (Snackbars y Toasts de Angular Material) para confirmar acciones exitosas (ej. registro de pacientes) y notificar sobre procesos en curso como la carga de datos del Dashboard. |
| 2 | Relación entre el sistema y el mundo real | Sí | Se ha implementado un lenguaje de dominio (Ubiquitous Language) del sector geriátrico y de salud, utilizando términos familiares como "Nursing Home", "Residents", "Health Metrics" y "Inventory". |
| 3 | Control y libertad del usuario | Parcial | Los usuarios pueden navegar fluidamente entre módulos mediante el Sidebar. Sin embargo, en flujos de creación extensos (ej. registrar un nuevo empleado o residente), faltan botones de "Deshacer" o "Cancelar" más prominentes para salir del flujo rápidamente. |
| 4 | Consistencia y estándares | Sí | Se mantiene una interfaz uniforme a través de los 10 *bounded contexts*. Las paletas de colores, las tablas de datos, la iconografía y los formularios siguen estrictamente los lineamientos de Angular Material. |
| 5 | Prevención de errores | Parcial | Los formularios de los módulos IAM y Nursing cuentan con validaciones reactivas. No obstante, se pueden mejorar las advertencias visuales proactivas, como alertar al usuario *antes* de que el stock de un medicamento llegue a cero. |
| 6 | Reconocimiento antes que recuerdo | Sí | El módulo *Analytics* (Dashboard) centraliza la información vital, como la ocupación y las estadísticas de residentes, evitando que el administrador deba memorizar o buscar datos navegando por múltiples pantallas. |
| 7 | Flexibilidad y eficiencia de uso | Parcial | Existen buscadores y filtros funcionales en las listas de residentes e inventario. Sin embargo, para usuarios expertos o administradores, la plataforma aún carece de atajos de teclado o acciones masivas (ej. eliminar varios registros a la vez). |
| 8 | Estética y diseño minimalista | Sí | La interfaz sigue un enfoque minimalista, mostrando únicamente la información esencial en las tablas (ej. Nombre, DNI, Rol, Estado) y delegando la información secundaria a las vistas de detalle. |
| 9 | Ayuda a los usuarios a reconocer, diagnosticar y recuperarse de errores | Sí | Al ingresar credenciales inválidas en el login (Módulo IAM) o fallar en una petición de API, el sistema captura las excepciones del backend (Spring Boot) y muestra un mensaje de error HTTP amigable, indicando la acción correctiva. |
| 10 | Ayuda y documentación | Parcial | Aunque el sistema cuenta con documentación técnica completa en Swagger para los desarrolladores, la interfaz de usuario final carece de tooltips contextuales avanzados o un submódulo de "Centro de Ayuda" integrado. |

---

## 6.4. Auditoría de Experiencias de Usuario

### 6.4.1. Auditoría realizada

En esta fase, nuestro equipo (NovaTech) auditó la plataforma web desarrollada por el equipo hermano para evaluar su nivel de madurez en aspectos de seguridad, usabilidad y validación de datos.

#### 6.4.1.1. Información del grupo auditado
*   **Nombre del Grupo:** EcatLeasing
*   **Proyecto Auditado:** PCpedia (Plataforma de Autenticación, Soporte, Gestión de Usuarios, Inventario y Facturación)
*   **Alcance:** Entorno de Staging y Producción. Evaluación bajo criterios OWASP Top 10, OWASP ASVS 4.0, ISO/IEC 25010 y WCAG 2.1.

#### 6.4.1.2. Cronograma de auditoría realizada
| Actividad | Fecha de Inicio | Fecha de Fin | Responsables (NovaTech) |
|---|---|---|---|
| Auditoría de Autenticación (Admin Login) y Seguridad | 06/07/2026 | 06/07/2026 | Equipo Auditor 1 y 2 |
| Auditoría de Gestión de Clientes (Admin Clients) | 07/07/2026 | 07/07/2026 | Equipo Auditor 1 y 2 |
| Auditoría de Módulos Transaccionales (Contratos, Facturas, Catálogo) | 07/07/2026 | 07/07/2026 | Equipo Auditor 1 y 2 |
| Evaluación de Tickets de Soporte | 07/07/2026 | 07/07/2026 | Equipo Auditor 1 y 2 |

#### 6.4.1.3. Contenido de auditoría realizada
Tras la ejecución exhaustiva del plan de pruebas sobre la plataforma PCpedia, se identificaron vulnerabilidades críticas de seguridad y fallas en la validación de formularios. A continuación, se documentan todos los hallazgos (estado REPROBADO) y los flujos que quedaron PENDIENTES por inestabilidad del sistema:

**Hallazgos Reportados (Casos Reprobados):**

| ID Prueba | Módulo Evaluado | Tipo de Hallazgo | Severidad | Descripción del Hallazgo |
|---|---|---|---|---|
| CP1-03 | Admin Login | Seguridad | Alta | **Enumeración de usuarios válidos:** Al intentar iniciar sesión con un correo no registrado, el sistema arroja mensajes diferenciales, permitiendo a un atacante inferir qué correos existen en la base de datos. |
| CP1-05 | Admin Login | Seguridad | Alta | **Ausencia de control de fuerza bruta:** Se enviaron 5 intentos consecutivos de login con contraseña incorrecta. El sistema no bloqueó la cuenta, no incrementó la latencia ni exigió CAPTCHA. |
| CP1-06 | Admin Login | Seguridad | Alta | **Falta de penalización:** El sistema permitió un login exitoso de manera inmediata justo después de múltiples intentos fallidos, confirmando la vulnerabilidad de fuerza bruta. |
| CP1-08 | Admin Login | Seguridad | Crítica | **Persistencia de sesión insegura:** El cierre de sesión en la interfaz (frontend) no revoca el token JWT en el servidor. El token capturado sigue siendo válido para peticiones autenticadas. |
| CP1-09 | Admin Login | Seguridad | Crítica | **Falta de validación de estado en peticiones:** Se desactivó una cuenta desde el panel de administración, pero la sesión activa de ese usuario no fue expulsada. El estado solo se valida al hacer el primer login. |
| CP2-08 | Admin Clients | Validación | Media | **Longitud mínima deficiente:** El sistema permitió editar y guardar un número telefónico ingresando solo 6 dígitos, violando la regla de negocio (exactamente 9 dígitos). |
| CP2-09 | Admin Clients | Validación | Media | **Longitud máxima deficiente:** El sistema permitió guardar un número telefónico con más de 9 dígitos. |
| CP2-13 | Admin Clients | Validación | Media | **Ausencia de control de duplicidad (Teléfono):** La plataforma permitió registrar un nuevo cliente utilizando el mismo número de teléfono que ya pertenecía a otro usuario registrado. |

**Pruebas Pendientes de Ejecución:**
Debido a comportamientos inesperados o alcance de tiempo, el bloque de gestión de soporte no pudo ser evaluado completamente. Quedaron **Pendientes** las validaciones del módulo **Tickets (CP3 y CP4)**, las cuales abarcaban:
*   Pruebas de vulnerabilidad IDOR (Control de acceso horizontal) al intentar ver tickets de otros clientes.
*   Inyección de payloads XSS (`<script>alert(1)</script>`) en la caja de comentarios de los tickets.
*   Comportamiento de la paginación de tickets frente a un volumen alto de registros.

---

### 6.4.2. Auditoría recibida

En contraparte, nuestra aplicación Veyra fue auditada por el grupo hermano para validar el nivel de cumplimiento funcional frente a los requerimientos documentados en nuestro Informe de Software.

#### 6.4.2.1. Información del grupo auditor
*   **Nombre del Grupo:** EcatLeasing
*   **Proyecto:** PCpedia
*   **Equipo Auditor:** Joaquín Enrique Carranza Tesén (Auditor Líder), Rúbens Bendezu Navarro, Sebastian Eduardo Hernandez Poma, Emily Juliette Arroyo Gonzales.
*   **Observadores:** Docente Julio M. Noriega Meléndez.

#### 6.4.2.2. Cronograma de auditoría recibida
| Actividad | Fecha | Detalle de la Sesión |
|---|---|---|
| Revisión Arquitectónica y CI/CD | 05/07/2026 | Análisis del despliegue en Firebase, Render, Aiven y revisión de los 35 tests en GitHub Actions. |
| Pruebas de Módulos IAM, Nursing y HCM | 05/07/2026 | Verificación de los *Bounded Contexts*, validaciones de Angular y pruebas de integración ITC-01 a ITC-06. |
| Pruebas de Módulos Payments y Analytics | 05/07/2026 | Comprobación de integración de la pasarela Stripe y validación de generación de reportes en el Dashboard. |

#### 6.4.2.3. Contenido de auditoría recibida
El equipo de EcatLeasing evaluó un total de 7 módulos (IAM, Nursing, HCM, Analytics, Payments, Activities, Questions) cubriendo más de 14 *User Stories*. La auditoría arrojó un resultado general **Conforme**, superando todas las pruebas unitarias y de integración. 

Sin embargo, se reportaron de manera oficial **2 No Conformidades (NC)** y **7 Oportunidades de Mejora (OM)** detalladas a continuación:

| ID | Módulo Evaluado | Severidad | Descripción del Hallazgo (Según Informe) | Referencia |
|---|---|---|---|---|
| NC-01 | IAM | Menor | **MFA Parcial:** La autenticación multifactor (MFA) documentada en TS18 se evidencia con implementación parcial en frontend. | Chapter III, TS18 |
| NC-02 | Payments | Menor | **Historial de transacciones:** El registro visual del historial de transacciones (Stripe) no se encuentra completamente implementado. | Chapter III, TS17 |
| OM-01 | Nursing / Inventory | Mejora | **Alertas Visuales:** Faltan alertas visuales más prominentes para medicamentos con stock bajo. | Chapter VIII, US14 |
| OM-02 | Analytics | Mejora | **Accesibilidad:** Dashboard más visible/accesible directamente desde la vista Home (Experimento #1). | Chapter VIII, TS-ST001 |
| OM-03 | Questions | Mejora | **Notificaciones:** Agregar notificaciones en tiempo real (WebSocket) para la mensajería de comunicación con familias. | Chapter VIII, US20 |
| OM-04 | Activities | Mejora | **Participación:** Completar la funcionalidad de registro de asistencia/participación en actividades. | Chapter IV |
| OM-05 | General (DevOps)| Mejora | **Monitoreo:** Implementar monitoreo con Azure Monitor / Application Insights como estaba documentado. | Chapter VII |
| OM-06 | General (Móvil) | Mejora | **Desarrollo Móvil:** Cumplir con el desarrollo de la app móvil mencionada en las conclusiones futuras. | Conclusions |
| OM-07 | Nursing (IoT) | Mejora | **Integración IoT:** Planificar integración IoT para monitoreo en tiempo real mediante sensores en residentes. | Chapter I, IV |

#### 6.4.2.4. Resumen de modificaciones para subsanar hallazgos

Nuestro equipo de desarrollo (NovaTech) procedió a realizar un análisis de impacto de los hallazgos reportados. Todas las No Conformidades fueron corregidas inmediatamente en código, y las Oportunidades de Mejora fueron priorizadas para el *sprint* actual o derivadas al Backlog futuro de la plataforma:

| ID Hallazgo | Modificación y Acción Técnica Realizada en Veyra | Estado Actual |
|---|---|---|
| **NC-01** | Se implementó y conectó la vista de verificación de código OTP (Time-Based One-Time Password) en Angular, cerrando el flujo completo de autenticación de dos factores con el backend. | **Subsanado** |
| **NC-02** | Se desarrolló el componente visual `<app-transaction-history>` que consume el endpoint de pagos, listando las suscripciones y montos procesados exitosamente por Stripe. | **Subsanado** |
| **OM-01** | Se programó una directiva estructural en la tabla de inventario que colorea en rojo la fila y emite un *badge* de advertencia cuando el umbral de un medicamento llega a su mínimo definido. | **Subsanado** |
| **OM-02** | Se rediseñó el ruteo del frontend (`app-routing.module.ts`) para que el Home actúe directamente como contenedor del Dashboard, reduciendo la cantidad de clics necesarios. | **Subsanado** |
| **OM-03** | Se inició la configuración de dependencias de `STOMP.js` y `SockJS` en Angular para habilitar WebSockets bidireccionales con Spring Boot en el módulo Questions. | **En Proceso** |
| **OM-04** | Se incorporó una columna de "Check-in" en el componente de calendario de actividades, permitiendo marcar la asistencia de los residentes con un solo clic. | **Subsanado** |
| **OM-05** | Se configuró y anidó la instrumentación de *Application Insights* dentro del *pipeline* de despliegue, permitiendo monitorear las latencias y carga en el servidor Render. | **Subsanado** |
| **OM-06** | El desarrollo móvil ha sido trasladado y formalizado como una Épica principal en el Product Backlog para la Versión 2.0 (Release Futuro), ya que excede el alcance del entregable actual. | **Derivado a Backlog** |
| **OM-07** | Al igual que la app móvil, el soporte de telemetría IoT ha sido documentado como una historia técnica a investigar para integraciones futuras con *hardware* de las casas de reposo. | **Derivado a Backlog** |
