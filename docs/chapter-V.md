## 5.1. Software Configuration Management

En esta sección se describen las decisiones, convenciones y principios adoptados por el equipo para garantizar la coherencia, trazabilidad y control de versiones durante el ciclo de vida del desarrollo de la solución **Veyra**.  

Se establecen los lineamientos para:

- Configuración del entorno de desarrollo  
- Gestión del código fuente  
- Convenciones de estilo  
- Configuración de despliegue  

---

## 5.1.1. Software Development Environment Configuration

En esta sección se especifican los productos de software utilizados durante el ciclo de vida del proyecto. Para cada herramienta se detalla:

- Nombre  
- Propósito técnico dentro del proyecto Veyra  
- Ruta de referencia (software SaaS) o ruta de descarga (instalación local)  

Las herramientas se organizan según las siguientes disciplinas:

1. **Project Management**
2. **Requirements Management**
3. **Product UX/UI Design**
4. **Software Development**
5. **Software Testing**
6. **Software Documentation**

### Project Management

Esta disciplina se centra en la planificación, seguimiento y control de las actividades del proyecto, asegurando el cumplimiento de los objetivos dentro del tiempo y recursos establecidos.

**Jira**  
Plataforma de gestión de proyectos ágiles utilizada para:
- Administración del Product Backlog  
- Planificación de Sprints  
- Asignación de User Stories y Tasks  
- Seguimiento mediante tableros Scrum (To-Do, In-Process, To-Review, Done)  

**Ruta de referencia:** https://www.atlassian.com/software/jira  

---

### Requirements Management

Este proceso se enfoca en la documentación, verificación y seguimiento de los requisitos del proyecto, asegurando que las necesidades de los stakeholders sean satisfechas.

**Trello**  
Plataforma de gestión visual utilizada para:
- Organización del Sprint Backlog  
- Gestión de User Stories por estado  
- Priorización colaborativa de requisitos  

**Ruta de referencia:** https://trello.com  

---

### Product UX/UI Design

El diseño de la experiencia e interfaz de usuario contempla un sitio web responsivo compatible con escritorio y dispositivos móviles.

**UXPressia**  
Elaboración de User Personas, Empathy Maps, Customer Journey Maps e Impact Maps.  
**Ruta:** https://uxpressia.com/  

**Miro**  
Soporte para EventStorming (Big Picture y Design-Level) e identificación de elementos del dominio.  
**Ruta:** https://miro.com/es/  

**Figma**  
Diseño de Wireframes, Mockups y prototipos interactivos aplicando Material Design.  
**Ruta:** https://www.figma.com/es-es/  

**Lucidchart**  
Creación de Wireflows, User Flows, diagramas UML y diagramas de base de datos.  
**Ruta:** https://www.lucidchart.com/pages/es  

**Overflow**  
Diseño de User Flow Diagrams con rutas de navegación detalladas.  
**Ruta:** https://overflow.io/  

---

### Software Development

El desarrollo abarca Landing Page, Frontend Web Application y Backend Web Services.

**GitHub**  
Control de versiones y gestión de repositorios con GitFlow, Conventional Commits y Semantic Versioning.  
**Ruta:** https://github.com  
**Organización:** https://github.com/NovaPeru-Tech  

**WebStorm**  
IDE para desarrollo Frontend con Angular, HTML5, CSS3, JavaScript y TypeScript.  
**Descarga:** https://www.jetbrains.com/webstorm/  
**Licencia:** https://www.jetbrains.com/community/education/  

**IntelliJ IDEA**  
IDE para desarrollo Backend con Java y Spring Boot, con integración a Azure.  
**Descarga:** https://www.jetbrains.com/idea/  
**Licencia:** https://www.jetbrains.com/community/education/  

**Angular Framework**  
Desarrollo de aplicaciones frontend con componentes reutilizables y consumo de APIs.  
**Ruta:** https://angular.io/  

**Angular Material**  
Componentes UI basados en Material Design.  
**Ruta:** https://material.angular.io/  

**Spring Boot**  
Desarrollo de servicios RESTful con persistencia y documentación integrada.  
**Ruta:** https://spring.io/projects/spring-boot  

**Tecnologías base**
- HTML5: https://html.spec.whatwg.org/  
- CSS3: https://www.w3.org/Style/CSS/  
- JavaScript: https://developer.mozilla.org/es/docs/Web/JavaScript  

**TypeScript**  
Lenguaje tipado para Angular.  
**Ruta:** https://www.typescriptlang.org/  

**Java (JDK 17)**  
Lenguaje backend compatible con Azure.  
**Ruta:** https://openjdk.org/  

---

### Software Testing

Las pruebas permiten verificar que el software cumple con los requisitos especificados.

**Gherkin**  
Lenguaje DSL para criterios de aceptación en formato Given–When–Then.  
Permite definir escenarios comprensibles y automatizables.

**Keywords:** Feature, Scenario, Given, When, Then, And, But  

**Ruta de referencia:** https://cucumber.io/docs/gherkin/  

---

### Software Documentation

La documentación facilita el mantenimiento y evolución del sistema.

**OpenAPI / Swagger**  
Documentación interactiva de APIs REST (endpoints, parámetros, respuestas, códigos HTTP).  
**Ruta:** https://swagger.io/  
**URL:** https://veyrav01.azurewebsites.net/swagger-ui/index.html  

**Markdown**  
Lenguaje de marcado ligero para documentación en GitHub.  
**Ruta:** https://www.markdownguide.org/  

### 5.1.2. Source Code Management. 

En esta sección se establecen los medios y esquemas de organización aplicados para el seguimiento de modificaciones del código fuente. Se utiliza GitHub como plataforma y sistema de control de versiones distribuido.

---

#### Repositorios del Proyecto

| Producto                    | URL del Repositorio |
|----------------------------|---------------------|
| Organización NovaPeru-Tech | https://github.com/upc-pre-1ASI0732-2610-16880-NovaTech |
| Landing Page               | https://github.com/upc-pre-1ASI0732-2610-16880-NovaTech/Veyra-Landing-Page |
| Frontend Web Application   | https://github.com/upc-pre-1ASI0732-2610-16880-NovaTech/Veyra-Frontend-Application |
| Backend Web Services       | https://github.com/upc-pre-1ASI0732-2610-16880-NovaTech/Veyra-Backend-Application |
| Project Report             | https://github.com/upc-pre-1ASI0732-2610-16880-NovaTech/Veyra-Document-Report |

---

#### GitFlow Workflow

Se implementa GitFlow como modelo de flujo de trabajo para el control de versiones, permitiendo desarrollo paralelo y gestión estructurada de releases.

**Ramas principales:**

- **main** → versiones estables en producción  
- **develop** → integración de funcionalidades  

**Ramas de soporte:**

- **feature/<feature-name>** → nuevas funcionalidades  
- **release/<version>** → preparación de versiones  
- **hotfix/<issue>** → correcciones urgentes  

---

#### Convenciones de nomenclatura para ramas

| Tipo   | Formato                                      | Ejemplo                                  |
|--------|----------------------------------------------|------------------------------------------|
| Feature| `feature/<bounded-context>-<feature-description>` | `feature/residents-add-medical-history` |
| Release| `release/<major.minor.patch>`               | `release/1.0.0`                          |
| Hotfix | `hotfix/<issue-description>`                | `hotfix/fix-login-validation`            |

---

#### Conventional Commits

<p>
  Se aplica la especificación Conventional Commits para los mensajes de commit, siguiendo la estructura:
</p>

<pre><code>&lt;type&gt;[optional scope]: &lt;description&gt;

[optional body]

[optional footer(s)]
</code></pre>

**Tipos:**

| Tipo   | Descripción                         |
|--------|-------------------------------------|
| feat   | Nueva funcionalidad                |
| fix    | Corrección de bug                  |
| docs   | Cambios en documentación           |
| style  | Formato sin afectar lógica         |
| refactor | Refactorización                  |
| perf   | Mejora de rendimiento              |
| test   | Pruebas                            |
| build  | Build o dependencias               |
| chore  | Mantenimiento                      |

**Ejemplos:**

<p><strong>Ejemplos de Commits:</strong></p>

<pre><code>feat(residents): add medical history registration form
fix(auth): resolve token expiration validation issue
docs(readme): update deployment instructions
build(deps): upgrade Angular to version 17
chore(config): update environment variables for production
</code></pre>


---

#### Semantic Versioning

**Formato:** `MAJOR.MINOR.PATCH`

- **MAJOR** → cambios incompatibles  
- **MINOR** → nuevas funcionalidades  
- **PATCH** → correcciones  

**Ejemplos:**

- `1.0.0`  
- `1.1.0`  
- `1.1.1`  
- `2.0.0`  

---

#### Configuración de GitHub en WebStorm

1. Ir a **VCS > Enable Version Control Integration** y seleccionar Git  
2. Ir a **File > Settings > Version Control > GitHub** y agregar la cuenta  
3. Configurar usuario en **File > Settings > Version Control > Git**  
4. Conectar repositorio en **Git > Manage Remotes**  
5. Commit: `Ctrl + K`  
6. Push: `Ctrl + Shift + K`  

### 5.1.3. Source Code Style Guide & Conventions. 
### 5.1.4. Software Deployment Configuration. 
## 5.2. Product Implementation & Deployment. 
### 5.2.1. Sprint Backlogs. 
### 5.2.2. Implemented Landing Page Evidence 
### 5.2.3. Implemented Frontend-Web Application Evidence 
### 5.2.4. Implemented Native-Mobile Application Evidence 
### 5.2.5. Implemented RESTful API and/or Serverless Backend Evidence 
### 5.2.6. RESTful API documentation 
### 5.2.7. Team Collaboration Insights 
## 5.3. Video About-the-Product. 
