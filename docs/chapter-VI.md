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

A continuación, se presenta la evaluación del prototipo y sistema de la plataforma Veyra basada en las 10 heurísticas de usabilidad de Jakob Nielsen, identificando el nivel de cumplimiento actual de nuestra interfaz.

| # | Heurística | Cumple (Sí/No/Parcial) | Observación / Evidencia |
|---|---|---|---|
| 1 | Visibilidad del estado del sistema | Sí | El sistema utiliza componentes visuales (Snackbars/Toasts de Angular Material) para confirmar acciones exitosas como el guardado de un residente o la emisión de alertas de error en la API. |
| 2 | Relación entre el sistema y el mundo real | Sí | Se utiliza terminología familiar para el sector médico y administrativo (Ej. "Nursing Home", "Residents", "Stock de Medicamentos", "Métricas de Salud"). |
| 3 | Control y libertad del usuario | Parcial | Los usuarios pueden navegar fluidamente entre módulos mediante el Sidebar, pero en algunos flujos de creación (ej. crear empleado) el botón de "Cancelar" o retroceder podría ser más prominente. |
| 4 | Consistencia y estándares | Sí | Se mantiene una interfaz uniforme en todos los *bounded contexts* mediante el uso consistente de tablas, formularios y paletas de colores definidos por Angular Material. |
| 5 | Prevención de errores | Parcial | Los formularios (ej. registro de IAM y Nursing) cuentan con validación reactiva en tiempo real; sin embargo, se detectaron áreas de mejora en la prevención visual (ej. alertas antes de que el stock llegue a cero). |
| 6 | Reconocimiento antes que recuerdo | Sí | El módulo *Analytics* centraliza la información vital (ocupación, residentes) en el Dashboard, evitando que el usuario deba memorizar datos de diferentes pantallas. |
| 7 | Flexibilidad y eficiencia de uso | Parcial | Existen filtros y buscadores en las listas de residentes e inventario, pero faltan atajos de teclado o vistas resumidas aceleradas para administradores avanzados. |
| 8 | Estética y diseño minimalista | Sí | La interfaz sigue un enfoque minimalista sin sobrecarga cognitiva, mostrando únicamente las columnas y acciones esenciales en cada tabla de datos. |
| 9 | Ayuda a los usuarios a reconocer, diagnosticar y recuperarse de errores | Sí | Al ingresar credenciales inválidas o datos erróneos, el sistema atrapa la excepción del backend (Spring Boot) y muestra un mensaje comprensible en la UI indicando qué falló. |
| 10 | Ayuda y documentación | Parcial | El sistema es intuitivo, pero carece de un módulo integrado de ayuda ("Help Center") o *tooltips* explicativos detallados para la configuración de planes de pago y roles. |

---

## 6.4. Auditoría de Experiencias de Usuario

### 6.4.1. Auditoría realizada

#### 6.4.1.1. Información del grupo auditado
*   **Nombre del Grupo:** EcatLeasing
*   **Proyecto:** PCpedia
*   **Integrantes:** Joaquín Enrique Carranza Tesén, Rúbens Bendezu Navarro, Sebastian Eduardo Hernandez Poma, Emily Juliette Arroyo Gonzales.

#### 6.4.1.2. Cronograma de auditoría realizada
| Actividad | Fecha de Inicio | Fecha de Fin | Responsables (NovaTech) |
|---|---|---|---|
| Auditoría de Autenticación, Roles y Seguridad | 06/07/2026 | 06/07/2026 | Equipo Auditor (NovaTech) |
| Auditoría del Módulo de Clientes y Perfiles | 07/07/2026 | 07/07/2026 | Equipo Auditor (NovaTech) |
| Auditoría de Módulos de Facturación y Tickets | 07/07/2026 | 07/07/2026 | Equipo Auditor (NovaTech) |

#### 6.4.1.3. Contenido de auditoría realizada
Durante la ejecución de la auditoría al aplicativo PCpedia, nuestro equipo encontró los siguientes hallazgos de usabilidad y seguridad de alta criticidad en sus flujos:

| ID | Módulo / Componente | Tipo de Hallazgo | Severidad | Descripción del Hallazgo |
|---|---|---|---|---|
| H-01 | Admin Login | Seguridad / Funcional | Alta | **Ausencia de control de fuerza bruta:** Al enviar 5 intentos consecutivos de login con contraseña incorrecta, el sistema no bloquea la cuenta ni exige CAPTCHA, permitiendo intentos ilimitados. |
| H-02 | Admin Login | Seguridad | Alta | **Persistencia de sesión insegura:** El cierre de sesión no revoca el acceso desde el punto de vista del servidor. Es posible reutilizar un token capturado contra endpoints protegidos tras hacer *logout*. |
| H-03 | Admin Login | Seguridad | Alta | **Falta de validación de estado en peticiones:** Con la sesión vigente, si se desactiva una cuenta desde el panel de administración, el acceso se mantiene activo. El estado solo se valida al hacer login. |
| H-04 | Admin Clients | Usabilidad / Validación | Media | **Validaciones de longitud deficientes:** Al editar el campo "Teléfono", el sistema permite guardar valores de 6 dígitos o mayores a 9 dígitos, ignorando la regla de negocio de exactamente 9 dígitos numéricos. |
| H-05 | Admin Clients | Usabilidad / Validación | Baja | **Falta de control de duplicidad:** El sistema permite registrar diferentes clientes utilizando el mismo número de teléfono. |

---

### 6.4.2. Auditoría recibida

#### 6.4.2.1. Información del grupo auditor
*   **Nombre del Grupo:** EcatLeasing
*   **Proyecto:** PCpedia
*   **Integrantes:** Joaquín Enrique Carranza Tesén (Auditor Líder), Rúbens Bendezu Navarro, Sebastian Eduardo Hernandez Poma, Emily Juliette Arroyo Gonzales.

#### 6.4.2.2. Cronograma de auditoría recibida
| Actividad | Fecha | Detalle de la Sesión |
|---|---|---|
| Reunión de Apertura y Mapeo Funcional | 05/07/2026 | Revisión de los criterios de auditoría (ISO/IEC 25010, DDD, UI/UX) y alcance de los módulos de Veyra. |
| Pruebas de Módulos IAM, Nursing y HCM | 05/07/2026 | Verificación de validaciones en frontend, RBAC, gestión de casas de reposo, stock e inventario. |
| Pruebas de Módulos Payments y Analytics | 05/07/2026 | Evaluación del Dashboard estadístico, planes de suscripción de Stripe y transacciones. |
| Reunión de Cierre | 05/07/2026 | Entrega formal del informe detallando No Conformidades (NC) y Oportunidades de Mejora (OM). |

#### 6.4.2.3. Contenido de auditoría recibida
El equipo auditor verificó un total de 7 módulos funcionales y 14 *User Stories*, contrastando el sistema en producción contra nuestros requerimientos. Los hallazgos reportados fueron:

| ID | Módulo Evaluado | Severidad | Descripción del Hallazgo |
|---|---|---|---|
| NC-01 | IAM | Menor | **Autenticación multifactor (MFA):** La funcionalidad está documentada en la TS18 pero su implementación en el frontend es solo parcial. |
| NC-02 | Payments | Menor | **Historial de transacciones:** El registro visual del historial de transacciones (Stripe) no se encuentra completamente implementado en la interfaz. |
| OM-01 | Nursing / Inventory | Mejora | **Alertas de Stock:** Faltan alertas visuales más prominentes para advertir cuando los medicamentos alcanzan niveles mínimos. |
| OM-02 | Analytics | Mejora | **Accesibilidad del Dashboard:** Se requiere que el dashboard estadístico sea más visible o tenga un acceso más rápido desde la pantalla de inicio (Home). |
| OM-03 | Questions | Mejora | **Comunicación en Tiempo Real:** El sistema de mensajería carece de notificaciones por WebSocket para alertar a las familias y al staff en tiempo real. |

#### 6.4.2.4. Resumen de modificaciones para subsanar hallazgos
A partir del informe recibido, el equipo de NovaTech priorizó y ejecutó las siguientes modificaciones en la plataforma Veyra para solucionar los errores:

| ID Hallazgo | Modificación Realizada en el Prototipo / Sistema | Estado |
|---|---|---|
| NC-01 | Se completó la implementación del flujo MFA en el Frontend de Angular, añadiendo las pantallas de confirmación de código TOTP vinculadas a las respuestas de la API. | Subsanado |
| NC-02 | Se diseñó y conectó una tabla en la vista de Pagos que consume y muestra el historial de transacciones previas extraído desde Stripe. | Subsanado |
| OM-01 | Se agregó lógica condicional en la vista de inventario (`*ngIf`) para mostrar "badges" rojos de advertencia cuando la cantidad de un medicamento es menor al nivel crítico. | Subsanado |
| OM-02 | Se reestructuró la navegación principal, colocando un acceso directo unificado hacia las métricas del *Analytics Dashboard* nada más iniciar sesión. | Subsanado |
| OM-03 | Se documentó la arquitectura para implementar WebSockets mediante SignalR/STOMP en el siguiente *sprint* de integración del módulo *Questions*. | En Proceso |
