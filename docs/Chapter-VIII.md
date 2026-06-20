## Chapter VIII: Experiment Driven Development
### 8.1. Experiment Planning
#### 8.1.1. As-Is Summary
La plataforma Veyra actualmente ofrece funcionalidades centrales para la gestion de casas de reposo, residentes, medicamentos, seguimiento de salud y comunicacion con familiares. La solucion ya cubre el core operacional del negocio, pero todavia presenta oportunidades claras de aprendizaje sobre la experiencia real de los usuarios y el valor percibido de ciertas mejoras.

Desde la perspectiva del negocio, el sistema permite registrar instituciones, administrar residentes, controlar inventario de medicamentos y almacenar metricas de salud. Sin embargo, no todas las funcionalidades han sido evaluadas aun con suficiente evidencia de uso para confirmar si realmente resuelven los puntos mas criticos del flujo diario del personal, administradores y familiares.

Problemas identificados:

- Visibilidad limitada sobre la informacion mas usada por cada perfil de usuario.
- Posible friccion en tareas repetitivas como busqueda de residentes, registro de medicacion y seguimiento clinico.
- Falta de evidencia suficiente sobre la utilidad real de algunos elementos de interfaz y paneles de informacion.
- Necesidad de validar si ciertas mejoras aumentan la eficiencia del trabajo del personal y la confianza de los familiares.

Objetivos de mejora:

- Reducir el tiempo necesario para completar tareas frecuentes en el sistema.
- Mejorar la claridad de los flujos mas usados por administradores y personal asistencial.
- Validar si una mejor organizacion de la informacion incrementa la adopcion de la plataforma.
- Confirmar que las mejoras propuestas aportan valor medible al negocio y a la experiencia del usuario.

#### 8.1.2. Raw Material: Assumptions, Knowledge Gaps, Ideas, Claims
Assumptions:

- Se asume que el personal de las casas de reposo necesita acceso mas rapido a informacion critica de residentes y medicamentos.
- Se asume que los familiares valoran notificaciones claras y actualizaciones frecuentes sobre el estado de sus seres queridos.
- Se asume que una interfaz mas ordenada y con jerarquia visual mas fuerte reduce errores operativos.
- Se asume que la centralizacion de metricas de salud mejora la toma de decisiones del personal asistencial.
- Se asume que una mejor navegacion dentro del sistema puede reducir la curva de aprendizaje de nuevos usuarios.

Knowledge Gaps:

- No se conoce con exactitud que seccion de la plataforma consume mas tiempo durante el uso diario.
- Falta evidencia sobre que informacion consideran mas prioritaria los administradores frente al personal de cuidado.
- No esta claro si los familiares consultan con frecuencia el portal o si necesitan mas recordatorios y resumenes.
- No se dispone aun de mediciones comparativas sobre tiempos de tarea antes y despues de una mejora de interfaz.
- Falta validar que elementos de la interfaz generan mas confianza y cuales generan confusion.

Ideas:

- Priorizar un dashboard con accesos rapidos a residentes, medicamentos y alertas de salud.
- Reorganizar la informacion critica para que los flujos frecuentes requieran menos clics.
- Implementar resumenes visuales mas claros para el estado de cada residente.
- Mejorar las notificaciones para familiares con mensajes mas utiles y faciles de entender.
- Aplicar ajustes de usabilidad para reducir errores y acelerar tareas repetitivas.

Claims:

- Un dashboard mejor estructurado puede reducir el tiempo de acceso a datos criticos.
- Mostrar resumentes de salud de forma mas visible puede mejorar la reaccion ante incidentes.
- Una navegacion mas simple puede aumentar la satisfaccion del personal que usa la plataforma a diario.
- Un sistema de notificaciones mas claro puede fortalecer la confianza de los familiares.
- Una mejor jerarquia visual puede disminuir errores durante registros operativos.

#### 8.1.3. Experiment Ready Questions

| Question | Confidence | Risk | Impact | Interest | Total Score |
|---|---:|---:|---:|---:|---:|
| Will a more visible dashboard reduce the time needed to access resident and health information? | 8 | 2 | 9 | 8 | 27 |
| Will a simpler navigation flow improve task completion for staff users? | 7 | 3 | 8 | 7 | 25 |
| Will clearer resident health summaries improve decision making during daily care routines? | 8 | 2 | 9 | 7 | 26 |
| Will improved family notifications increase trust and portal engagement? | 7 | 3 | 8 | 8 | 26 |
| Will better information hierarchy reduce operational mistakes when registering medication and health data? | 8 | 3 | 9 | 7 | 27 |

#### 8.1.4. Question Backlog

| Priority | Question |
|---:|---|
| 1 | Will a more visible dashboard reduce the time needed to access resident and health information? |
| 1 | Will better information hierarchy reduce operational mistakes when registering medication and health data? |
| 2 | Will clearer resident health summaries improve decision making during daily care routines? |
| 3 | Will a simpler navigation flow improve task completion for staff users? |
| 3 | Will improved family notifications increase trust and portal engagement? |

#### 8.1.5. Experiment Cards

| Question | Why | What | Hypothesis |
|---|---|---|---|
| Will a more visible dashboard reduce the time needed to access resident and health information? | Because staff users need fast access to critical data during daily care routines, and a stronger visual hierarchy can reduce search time. | Redesign the main dashboard to highlight residents, medications, alerts, and recent health metrics as the first visible elements. | We expect task access time to decrease by at least 20 percent and users to report better clarity in the main workflow. |
| Will a simpler navigation flow improve task completion for staff users? | Because repeated tasks such as resident lookup and medication registration should require as few steps as possible. | Simplify the navigation structure and reduce unnecessary intermediate screens for the most common actions. | We expect the average number of clicks per task to decrease and the completion rate for frequent tasks to improve. |
| Will clearer resident health summaries improve decision making during daily care routines? | Because medical and caregiving decisions depend on quick interpretation of relevant resident status. | Create more readable resident summary views with highlighted metrics, recent events, and alert indicators. | We expect users to identify critical resident conditions faster and to make more confident routine decisions. |
| Will improved family notifications increase trust and portal engagement? | Because families need concise and useful updates to feel informed and involved in the care process. | Redesign notification messages to include clearer context, status, and next actions for family users. | We expect notification open rates and portal engagement to increase after improving message clarity. |
| Will better information hierarchy reduce operational mistakes when registering medication and health data? | Because unclear layouts can lead to incorrect entries in high frequency operational tasks. | Reorganize forms and screens so that the most important fields appear first and the critical actions are visually emphasized. | We expect fewer input errors and fewer corrections during medication and health record registration. |

### 8.2. Experiment Design
#### 8.2.1. Hypotheses
The experimentation phase of Veyra was designed to validate whether the proposed product improvements actually solve the most relevant usability and operational problems detected during the planning stage.

The main hypotheses are:

- A clearer dashboard will reduce the time needed to access resident, medication, and health information.
- A simplified navigation flow will improve task completion for staff users.
- Better resident health summaries will improve decision making during daily care routines.
- Improved family notifications will increase trust and portal engagement.
- Better information hierarchy will reduce operational mistakes during data registration.

These hypotheses were selected because they are directly related to the core value of the platform and can be measured through observable user behavior and product analytics.

#### 8.2.2. Domain Business Metrics
The business metrics for Veyra were defined around the most important outcomes of the care management platform. The objective is not only to increase usage, but also to improve operational efficiency, information quality, and user confidence.

| Metric | Description | Why it matters |
|---|---|---|
| Task completion time | Time required to finish common actions such as search, register, or review | Measures efficiency in daily operations |
| Error rate in forms | Number of incorrect or incomplete submissions | Indicates quality of the interface and validation |
| Resident data access rate | Frequency of access to resident profiles and summaries | Shows whether critical data is easy to find |
| Medication registration success rate | Percentage of medication entries completed without correction | Reflects reliability in a critical workflow |
| Family portal engagement | Frequency of visits and interaction with notifications | Measures perceived value for family users |
| Health alert visibility | How quickly staff notices relevant health information | Important for timely care decisions |

These metrics connect the product experience with business value because Veyra is used in a context where speed, accuracy, and trust are essential.

#### 8.2.3. Measures
To validate the hypotheses, Veyra uses a combination of behavioral, performance, and perception measures. This allows the team to observe not only what users do, but also how they feel about the experience.

| Measure | Type | How it is captured |
|---|---|---|
| Time on task | Quantitative | Time between opening a screen and finishing the intended action |
| Click count | Quantitative | Number of interactions required to complete a flow |
| Form error count | Quantitative | Number of validation errors generated by the user |
| Completion rate | Quantitative | Percentage of tasks completed successfully |
| Notification engagement | Quantitative | Open rate or interaction rate with alerts |
| Satisfaction feedback | Qualitative | User comments after performing the task |
| Perceived clarity | Qualitative | User feedback about layout and information hierarchy |

The chosen measures were kept simple and practical so they can be compared before and after the proposed changes.

#### 8.2.4. Conditions
The experimentation conditions define when and how each improvement should be tested so the results can be interpreted with confidence.

| Condition | Description |
|---|---|
| Test group | Users interact with the improved version of the dashboard, navigation, summaries, or notifications |
| Control group | Users interact with the current version of the interface or current flow |
| Same user profile | Comparisons are made between similar roles such as administrator, staff member, or family member |
| Same task scope | The same task is used in both conditions to keep the comparison fair |
| Same environment | The test is performed under similar device and network conditions |
| Same success criteria | Both versions are evaluated using the same definition of completion and error |

These conditions help isolate the effect of the change itself and reduce bias caused by external factors.

#### 8.2.5. Scale Calculations and Decisions
The experiment scale was selected based on the scope of the product and the type of improvement being tested. Since Veyra is an operational platform, the experimentation does not require a very large sample to begin generating useful insights, but it does require enough coverage to observe patterns across the main user profiles.

The decision rules are:

- If a change reduces time on task and error rate, it is considered positive.
- If a change increases engagement without increasing confusion, it is considered positive.
- If a change improves clarity but adds friction to critical workflows, it must be revised before adoption.
- If results are mixed, the team should iterate on the design and test again.

For practical purposes, the experiment can be executed with a small to medium user group representing the core personas of the platform. The main goal is to detect strong signals early rather than wait for a perfect large-scale dataset.

#### 8.2.6. Methods Selection
The selected methods combine qualitative and quantitative validation so the team can understand both the observed behavior and the reasons behind it.

| Method | Purpose | Applied to |
|---|---|---|
| Usability testing | Observe how users complete tasks in the interface | Dashboard, navigation, forms, summaries |
| A/B comparison | Compare current and improved versions | Notifications, layout, task flows |
| Analytics tracking | Measure real usage behavior | Clicks, completion rate, time on task |
| User interviews | Collect direct perception and feedback | Staff, administrators, family members |
| Heuristic review | Identify obvious usability problems | Screens and critical workflows |

The selected methods were chosen because they are lightweight, practical, and compatible with the current stage of Veyra.

#### 8.2.7. Data Analytics: Goals, KPIs and Metrics Selection
The analytics strategy for Veyra focuses on understanding whether the product improvements really enhance operational efficiency and user experience. The goal is to compare behavior before and after the proposed changes and to detect which improvements create measurable value.

Goals:

- Reduce the time required to complete important tasks.
- Improve the clarity of the information presented in the platform.
- Increase the use of critical features by staff and family users.
- Reduce operational mistakes in forms and daily records.
- Strengthen trust in the platform through better notifications and summaries.

KPIs:

| KPI | Definition | Target direction |
|---|---|---|
| Average task completion time | Average seconds needed to finish a common action | Lower is better |
| Error-free form rate | Percentage of submissions without validation issues | Higher is better |
| Resident profile access rate | How often users open resident details | Higher is better |
| Notification engagement rate | Share of notifications that users open or review | Higher is better |
| Task completion rate | Percentage of flows completed successfully | Higher is better |
| User clarity score | User perception of how clear the interface is | Higher is better |

Metrics selection:

- Time on task for resident search, medication registration, and health review.
- Click path length to identify unnecessary navigation steps.
- Validation errors in forms that affect operational accuracy.
- Frequency of access to resident summaries and health alerts.
- Notification interaction to evaluate family communication value.
- User feedback collected after each test session.

<div align="center">
  <img src="../assets/img/chapter-VIII/Rendimiento1.png" alt="Veyra performance analytics evidence 1" width="90%">
  <p><em>Figure: Performance evidence for the experimentation phase, showing operational behavior relevant to the selected KPIs.</em></p>
</div>

<div align="center">
  <img src="../assets/img/chapter-VIII/Rendimiento2.png" alt="Veyra performance analytics evidence 2" width="90%">
  <p><em>Figure: Additional performance evidence used to interpret time, load, or interaction behavior during analysis.</em></p>
</div>

These artifacts support the evaluation of the experiment by providing evidence that can be compared against the selected goals and KPIs.

#### 8.2.8. Web and Mobile Tracking Plan
The tracking plan defines what should be observed in the web and mobile experience so the team can measure user behavior consistently across the main scenarios of the platform.

| Event | Trigger | Data captured |
|---|---|---|
| page_view_dashboard | User opens the main dashboard | Screen name, user role, timestamp |
| click_resident_search | User starts a resident lookup | Search action, result count, timestamp |
| submit_medication_form | User submits medication registration | Form type, success status, validation errors |
| open_health_summary | User opens a resident health summary | Resident id, screen name, timestamp |
| open_notification | User opens a family notification | Notification type, engagement status |
| click_navigation_item | User selects a menu item | Menu item, screen transition, timestamp |

Tracking principles:

- Track only events that are directly related to the hypotheses.
- Keep the event schema simple and consistent.
- Separate staff, administrator, and family user behavior.
- Use timestamps to support time on task analysis.
- Avoid collecting unnecessary personal data.

The tracking plan gives the team a clear way to connect user behavior with the business metrics defined for the experiment.

### 8.3. Experimentation
#### 8.3.1. To-Be User Stories
The experimentation stage translates the validated improvement ideas into concrete To-Be user stories. These stories represent the next version of Veyra after the insights from planning and design have been considered.

| ID | User Story | Expected value |
|---|---|---|
| TB-US01 | As an administrator, I want a clearer dashboard so I can access critical resident and medication information faster. | Faster decision making and reduced search time |
| TB-US02 | As a staff member, I want a simpler navigation flow so I can complete daily tasks with fewer steps. | Higher task completion efficiency |
| TB-US03 | As a care professional, I want resident health summaries to be easier to read so I can react quickly to critical situations. | Better clinical awareness |
| TB-US04 | As a family member, I want clearer notifications so I can understand updates about my relative more easily. | Greater trust and engagement |
| TB-US05 | As a user who registers health or medication data, I want a better information hierarchy so I can avoid mistakes. | Fewer errors and corrections |

These To-Be stories align the product direction with the hypotheses and the most relevant business outcomes.

#### 8.3.2. To-Be Product Backlog
The To-Be Product Backlog contains the improvements that should be implemented after experimentation confirms their value. The backlog was prioritized according to business impact, operational relevance, and expected user benefit.

| Priority | ID | To-Be Item | Description |
|---:|---|---|---|
| 1 | TB-01 | Dashboard redesign | Highlight residents, medication, alerts, and recent health metrics on the main screen |
| 1 | TB-02 | Information hierarchy update | Improve the visual order of forms and summaries to reduce confusion |
| 2 | TB-03 | Navigation simplification | Reduce unnecessary steps in common staff workflows |
| 2 | TB-04 | Health summary improvement | Make resident health indicators easier to scan and interpret |
| 3 | TB-05 | Notification redesign | Improve the clarity and usefulness of family notifications |

The backlog reflects the product direction that should be pursued if the experiment results confirm the expected benefits. This keeps the development effort focused on the improvements that create the strongest value for the platform.
