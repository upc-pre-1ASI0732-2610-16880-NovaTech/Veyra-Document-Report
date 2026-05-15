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

Los resultados obtenidos evidenciaron que las entidades principales del sistema funcionan correctamente bajo los escenarios evaluados, contribuyendo a mejorar la estabilidad, mantenibilidad y confiabilidad de la aplicación.

### 6.1.2. Core Integration Tests.
### 6.1.3. Core Behavior-Driven Development

En esta sección se definen los escenarios de prueba utilizando el lenguaje Gherkin (Given-When-Then) para asegurar que el comportamiento del sistema cumpla con los criterios de aceptación de las Historias de Usuario principales (Core).

#### Epic: Resident Health Tracking

**User Story:** As a nursing home staff member, I want to record daily health metrics for residents so that their health status is constantly monitored.

```gherkin
Feature: Health Metric Registration

  Scenario: Staff registers a resident's daily vital signs successfully
    Given the staff member is on the resident's profile page
    And the resident has an active status in the system
    When the staff member enters the daily vital signs including blood pressure and temperature
    And clicks the "Save Metrics" button
    Then the system should save the new health record in the database
    And the system should display a "Health metrics updated successfully" message

  Scenario: Attempting to save metrics with missing required data
    Given the staff member is on the resident's profile page
    When the staff member leaves the "blood pressure" field empty
    And clicks the "Save Metrics" button
    Then the system should prevent the submission
    And the system should display a "Blood pressure is required" validation error
```

#### Epic: Family Communication

**User Story:** As a family member, I want to view my relative's daily activity logs so that I can stay informed about their well-being.
```gherkin
Feature: Family Portal Activity Viewing

  Scenario: Family member checks daily activities
    Given the family member is authenticated in the family portal
    And their account is linked to an active resident
    When the family member navigates to the "Daily Logs" section
    Then the system should display a chronological list of the resident's activities for the current day
```

### 6.1.4. Core System Tests.
