## Chapter VIII: Desarrollo Guiado por Experimentos

### 8.1. Experiment Planning

#### 8.1.1. As-Is Summary
La plataforma Veyra actualmente ofrece funcionalidades centrales para la gestión de casas de reposo (**TS-NH001**), residentes (**US12**), medicamentos (**US14**), personal (**TS-EM001**) y métricas operativas. La solución ya cubre el core operacional del negocio, pero todavía presenta oportunidades claras de aprendizaje sobre la experiencia real de los usuarios y el valor percibido de ciertas mejoras en la interfaz.

Desde la perspectiva del negocio, el sistema permite registrar instituciones, administrar residentes, controlar inventario de medicamentos (**TS-I002**) y almacenar expedientes detallados (**TS-RM002**). Sin embargo, no todas las funcionalidades han sido evaluadas aún con suficiente evidencia de uso para confirmar si realmente resuelven los puntos más críticos del flujo diario del personal, administradores y familiares.

**Problemas identificados:**
- Visibilidad limitada en herramientas analíticas iniciales como el Dashboard de Estadísticas (**TS-ST001**).
- Posible fricción en tareas repetitivas como la búsqueda de residentes, actualización de pacientes (**TS-RM-005**) y registro de medicación (**US14**).
- Falta de validación sobre el manejo de errores comprensibles (**US44**) durante pérdidas de conexión o ingresos incorrectos.
- Necesidad de validar si ciertas mejoras aumentan la eficiencia del trabajo del personal y la adopción por parte de familiares y visitantes (**US02**).

**Objetivos de mejora:**
- Reducir el tiempo necesario para completar tareas frecuentes en el sistema (ej. actualización de datos y registro de tomas).
- Mejorar la claridad de los flujos más usados por administradores y personal asistencial.
- Validar que el manejo de errores guíe correctamente al usuario (**US44**) para reducir la frustración.
- Confirmar que las mejoras propuestas aportan valor medible al negocio y a la experiencia del usuario.

#### 8.1.2. Raw Material: Suposiciones, Vacíos de Conocimiento, Ideas, Afirmaciones

**Suposiciones:**
- Se asume que el personal necesita acceso más rápido al Dashboard (**TS-ST001**) y a los expedientes detallados (**TS-RM002**).
- Se asume que los familiares valoran notificaciones claras sobre actualizaciones médicas.
- Se asume que una interfaz con un manejo de errores claro (**US44**) reduce la tasa de abandono de formularios críticos.
- Se asume que la centralización de datos mejora la toma de decisiones.

**Vacíos de conocimiento:**
- No se conoce con exactitud qué sección (Dashboard vs. Perfil de Residente) consume más tiempo de carga cognitiva.
- Falta evidencia sobre la eficiencia real al descontar medicamentos del inventario en el flujo diario (**US14**).
- No se dispone aún de mediciones comparativas sobre tiempos de tarea ante errores de red.

**Ideas:**
- Priorizar un dashboard (**TS-ST001**) con accesos rápidos a residentes, medicamentos y alertas de ocupación.
- Implementar validaciones visuales preventivas alineadas al manejo de errores (**US44**).
- Reorganizar la información del residente para que el endpoint de expediente (**TS-RM002**) alimente una vista rápida sin necesidad de recargar toda la página.

**Afirmaciones:**
- Un dashboard mejor estructurado puede reducir el tiempo de acceso a datos críticos.
- Una navegación más simple puede aumentar la satisfacción del personal.
- Una mejor jerarquía visual y un manejo de errores comprensible disminuirán errores en registros de medicamentos (**US14**).

#### 8.1.3. Experiment Ready Questions

<table>
  <thead>
    <tr>
      <th align="left">Pregunta</th>
      <th align="center">Confianza</th>
      <th align="center">Riesgo</th>
      <th align="center">Impacto</th>
      <th align="center">Interés</th>
      <th align="center">Puntaje total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="left">¿Un dashboard (TS-ST001) más visible reducirá el tiempo para acceder a info de residentes?</td>
      <td align="center">8</td>
      <td align="center">2</td>
      <td align="center">9</td>
      <td align="center">8</td>
      <td align="center">27</td>
    </tr>
    <tr>
      <td align="left">¿Una mejor jerarquía de información y manejo de errores (US44) reducirá errores al registrar medicamentos (US14)?</td>
      <td align="center">8</td>
      <td align="center">3</td>
      <td align="center">9</td>
      <td align="center">7</td>
      <td align="center">27</td>
    </tr>
    <tr>
      <td align="left">¿Resúmenes de salud rápidos (TS-RM002) mejorarán la toma de decisiones en el cuidado?</td>
      <td align="center">8</td>
      <td align="center">2</td>
      <td align="center">9</td>
      <td align="center">7</td>
      <td align="center">26</td>
    </tr>
    <tr>
      <td align="left">¿Notificaciones para familiares mejoradas aumentarán la confianza y el uso del portal?</td>
      <td align="center">7</td>
      <td align="center">3</td>
      <td align="center">8</td>
      <td align="center">8</td>
      <td align="center">26</td>
    </tr>
    <tr>
      <td align="left">¿Un flujo de navegación simple mejorará la finalización de tareas de actualización (TS-RM-005)?</td>
      <td align="center">7</td>
      <td align="center">3</td>
      <td align="center">8</td>
      <td align="center">7</td>
      <td align="center">25</td>
    </tr>
  </tbody>
</table>

#### 8.1.4. Question Backlog

<table>
  <thead>
    <tr>
      <th align="center">Prioridad</th>
      <th align="left">Pregunta</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center">1</td>
      <td align="left">¿Un dashboard (TS-ST001) más visible reducirá el tiempo para acceder a info de residentes?</td>
    </tr>
    <tr>
      <td align="center">1</td>
      <td align="left">¿Una mejor jerarquía de información y manejo de errores (US44) reducirá errores al registrar medicamentos (US14)?</td>
    </tr>
    <tr>
      <td align="center">2</td>
      <td align="left">¿Resúmenes de salud rápidos (TS-RM002) mejorarán la toma de decisiones en el cuidado?</td>
    </tr>
    <tr>
      <td align="center">3</td>
      <td align="left">¿Notificaciones para familiares mejoradas aumentarán la confianza y el uso del portal?</td>
    </tr>
    <tr>
      <td align="center">3</td>
      <td align="left">¿Un flujo de navegación simple mejorará la finalización de tareas de actualización (TS-RM-005)?</td>
    </tr>
  </tbody>
</table>

#### 8.1.5. Experiment Cards

<table>
  <thead>
    <tr>
      <th align="left">Question</th>
      <th align="left">Why</th>
      <th align="left">What (Related US/TS)</th>
      <th align="left">Hypothesis</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="left">¿Un dashboard más visible reducirá el tiempo necesario para acceder a información?</td>
      <td align="left">Porque el personal necesita acceso rápido a datos críticos durante las rutinas.</td>
      <td align="left">Rediseñar el <strong>TS-ST001 (Dashboard de Estadísticas)</strong> para resaltar métricas y alertas críticas.</td>
      <td align="left">Se espera que el tiempo de acceso disminuya al menos 20% y haya mayor claridad.</td>
    </tr>
    <tr>
      <td align="left">¿Una mejor jerarquía de información reducirá errores operativos al registrar datos?</td>
      <td align="left">Porque diseños poco claros llevan a registros incorrectos en operaciones frecuentes.</td>
      <td align="left">Mejorar la UI de <strong>US14 (Admin. de medicamentos)</strong> e implementar <strong>US44 (Manejo de errores comprensible)</strong>.</td>
      <td align="left">Se espera que disminuyan los errores de entrada y las correcciones de inventario.</td>
    </tr>
    <tr>
      <td align="left">¿Resúmenes de salud más claros mejorarán la toma de decisiones?</td>
      <td align="left">Porque las decisiones dependen de la interpretación rápida del estado del residente.</td>
      <td align="left">Optimizar la vista alimentada por <strong>TS-RM002 (Ver expediente detallado)</strong>.</td>
      <td align="left">Los usuarios identificarán condiciones críticas más rápido.</td>
    </tr>
    <tr>
      <td align="left">¿Un flujo de navegación más simple mejorará la finalización de tareas?</td>
      <td align="left">Porque tareas repetitivas de actualización deben requerir la menor cantidad de pasos.</td>
      <td align="left">Simplificar el flujo para <strong>TS-RM-005 (Actualizar información)</strong>.</td>
      <td align="left">Disminuirá el número promedio de clics por tarea.</td>
    </tr>
  </tbody>
</table>

---

### 8.2. Experiment Design

Esta sección detalla el diseño metodológico utilizado para validar los cuatro Experiment Cards definidos en 8.1.5, estableciendo hipótesis formales, métricas de negocio, condiciones de éxito y el plan de instrumentación necesario para recolectar evidencia objetiva antes de cerrar cada ciclo de experimentación.

#### 8.2.1. Hypotheses

Se formuló una hipótesis Lean UX (formato "Creemos que... Sabremos que es verdad cuando...") por cada Experiment Card, ligada a su US/TS correspondiente.

<table>
  <thead>
    <tr>
      <th align="left">US/TS</th>
      <th align="left">Hypothesis Statement</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="left"><strong>TS-ST001</strong></td>
      <td align="left">Creemos que rediseñar el Dashboard de Estadísticas priorizando ocupación real y alertas críticas de inventario reducirá el tiempo que un administrador necesita para identificar una situación urgente. Sabremos que es verdad cuando los administradores ubiquen alertas críticas en menos de 10 segundos y el Dashboard mantenga un puntaje de Rendimiento (Lighthouse) igual o superior a 90.</td>
    </tr>
    <tr>
      <td align="left"><strong>US44 / US14</strong></td>
      <td align="left">Creemos que reemplazar los mensajes de error genéricos por notificaciones (toast) con el detalle real del backend y un botón de reintento visible, junto con un endpoint real de registro de toma de medicamentos, reducirá los errores operativos y la necesidad de soporte técnico durante el registro de medicación. Sabremos que es verdad cuando el personal asistencial pueda resolver un error de registro sin ayuda externa y el endpoint <code>POST /residents/{residentId}/medications/{medicationId}/administrations</code> descuente el stock correctamente.</td>
    </tr>
    <tr>
      <td align="left"><strong>TS-RM002</strong></td>
      <td align="left">Creemos que exponer un endpoint GET optimizado con la información del residente permitirá construir, en una siguiente iteración, un resumen de salud rápido que mejore la toma de decisiones clínicas. Sabremos que es verdad cuando el personal asistencial reporte identificar el estado de salud relevante de un residente sin necesidad de navegar por múltiples vistas.</td>
    </tr>
    <tr>
      <td align="left"><strong>TS-RM-005</strong></td>
      <td align="left">Creemos que un endpoint PATCH para actualizaciones puntuales (sin reenviar el registro completo) reducirá los pasos y errores al actualizar datos de residentes y personal. Sabremos que es verdad cuando una actualización parcial (ej. sin cambiar la foto) se complete en un solo envío sin errores 400 y con una reducción medible de clics frente al flujo As-Is.</td>
    </tr>
  </tbody>
</table>

#### 8.2.2. Domain Business Metrics

<table>
  <thead>
    <tr>
      <th align="left">US/TS</th>
      <th align="left">Métrica de Negocio</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="left"><strong>TS-ST001</strong></td>
      <td align="left">Tiempo promedio de identificación de una alerta crítica (ocupación/stock/vencimiento) desde el ingreso al Dashboard.</td>
    </tr>
    <tr>
      <td align="left"><strong>US44 / US14</strong></td>
      <td align="left">Tasa de éxito en el registro de tomas de medicamento y tasa de error guiado (errores que el usuario resuelve sin soporte técnico).</td>
    </tr>
    <tr>
      <td align="left"><strong>TS-RM002</strong></td>
      <td align="left">Tiempo de decisión clínica (desde que el personal abre el expediente hasta que actúa sobre la información mostrada).</td>
    </tr>
    <tr>
      <td align="left"><strong>TS-RM-005</strong></td>
      <td align="left">Número de clics/pasos y tasa de error (400) al completar una actualización de datos de residente o personal.</td>
    </tr>
  </tbody>
</table>

#### 8.2.3. Measures

<table>
  <thead>
    <tr>
      <th align="left">Métrica</th>
      <th align="left">Cómo se mide</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="left">Tiempo de identificación de alerta crítica</td>
      <td align="left">Cronometraje durante la entrevista de validación (8.3.4.2), desde el login/ingreso al Dashboard hasta que el entrevistado señala la alerta correcta.</td>
    </tr>
    <tr>
      <td align="left">Tasa de éxito / error guiado en registro de medicamentos</td>
      <td align="left">Código de respuesta HTTP del endpoint de administración de medicamentos (200/201 vs. 400) contrastado con la percepción del usuario reportada en la entrevista (¿resolvió el error sin ayuda?).</td>
    </tr>
    <tr>
      <td align="left">Tiempo de decisión clínica</td>
      <td align="left">Verificación de la existencia y cobertura funcional de la vista de expediente (contacto, alergias, signos vitales) frente a lo que el personal necesita consultar; ante la ausencia de una vista unificada, la métrica no puede recolectarse aún de forma fiable (ver 8.4.1).</td>
    </tr>
    <tr>
      <td align="left">Clics/pasos y tasa de error en actualización</td>
      <td align="left">Revisión directa del código (assembler de actualización) y pruebas end-to-end contra el ambiente desplegado, verificando que un PATCH sin cambio de foto no produzca error 400.</td>
    </tr>
  </tbody>
</table>

#### 8.2.4. Conditions

Se define como condición de éxito para cada hipótesis:

- **TS-ST001:** tiempo de identificación de alerta crítica < 10 segundos y Rendimiento (Lighthouse) ≥ 90.
- **US44 / US14:** el endpoint de administración de medicamentos responde 200/201 con descuento correcto de stock, y el usuario reporta poder reintentar sin soporte técnico ante un error.
- **TS-RM002:** el personal asistencial identifica el estado relevante del residente sin navegar por más de una vista adicional a la de detalle.
- **TS-RM-005:** 0% de tasa de error 400 en actualizaciones parciales que no modifican la foto, verificado en producción.

Una hipótesis se considera **no concluyente** (y no rechazada) cuando no existe aún evidencia cuantitativa suficiente para pronunciarse, en lugar de forzar una conclusión sin sustento (ver el caso de TS-RM002 en 8.4.1).

#### 8.2.5. Scale Calculations and Decisions

Para las métricas cuantitativas (tiempo de identificación de alerta, puntaje de Rendimiento) se utiliza una escala de razón directa (segundos, puntaje 0-100 de Lighthouse), permitiendo comparación directa contra el umbral de la condición de éxito (8.2.4). Para las métricas cualitativas obtenidas por entrevista (percepción de claridad del error, confianza en la información mostrada) se utiliza una escala ordinal de 3 niveles (Baja / Moderada / Alta), registrada textualmente en 8.3.4.2. La decisión de validar, descartar o mantener como no concluyente una hipótesis se toma comparando el resultado obtenido (cuantitativo u ordinal) contra la condición de éxito definida, priorizando siempre la evidencia de implementación real (8.3.3) sobre la percepción subjetiva cuando ambas están disponibles.

#### 8.2.6. Methods Selection

Se seleccionaron los siguientes métodos, combinando validación técnica y de usuario:

- **Entrevistas de validación semiestructuradas** (8.3.4) con un representante de cada rol clave (administrador, personal asistencial, familiar), para capturar percepción cualitativa.
- **Auditorías de rendimiento (Lighthouse)** sobre el ambiente desplegado, para validar que las mejoras de UI no degradan la performance percibida (8.3.3.3).
- **Pruebas directas contra la API desplegada** (vía cliente HTTP) para verificar que los endpoints priorizados cumplen sus criterios de aceptación y para reproducir errores reportados en producción antes de cerrarlos como corregidos (8.3.3.5).
- **Revisión de código contra el informe** (code-to-documentation reconciliation), utilizada específicamente para detectar brechas entre lo documentado y lo implementado, como en los casos de TS17, TS18, US38, TS-RM-005 y TS-NH001.

Se priorizaron métodos de bajo costo y ejecución rápida (entrevistas breves, pruebas directas de API) dado el alcance y tiempo disponible para el ciclo de experimentación de este release.

#### 8.2.7. Data Analytics: Goals, KPIs and Metrics Selection

<table>
  <thead>
    <tr>
      <th align="left">Goal</th>
      <th align="left">KPI</th>
      <th align="left">Métrica</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="left">Reducir el tiempo de acceso a información operativa crítica</td>
      <td align="left">% de administradores que ubican una alerta crítica en menos de 10s</td>
      <td align="left">Tiempo de identificación de alerta (TS-ST001)</td>
    </tr>
    <tr>
      <td align="left">Reducir errores operativos en registro de medicación</td>
      <td align="left">Tasa de error guiado (resuelto sin soporte) vs. tasa de error total</td>
      <td align="left">Códigos de respuesta HTTP + percepción de claridad del error (US44/US14)</td>
    </tr>
    <tr>
      <td align="left">Mejorar la toma de decisiones clínicas</td>
      <td align="left">% de personal que identifica el estado relevante sin navegación adicional</td>
      <td align="left">Cobertura funcional del expediente / tiempo de decisión (TS-RM002)</td>
    </tr>
    <tr>
      <td align="left">Simplificar la actualización de datos</td>
      <td align="left">Tasa de error 400 en actualizaciones parciales</td>
      <td align="left">Resultado de pruebas end-to-end sobre PATCH (TS-RM-005)</td>
    </tr>
  </tbody>
</table>

#### 8.2.8. Web and Mobile Tracking Plan

Dado que el alcance de este release se concentró en Landing Page, Frontend Web Application y RESTful API/Backend (sin aplicación móvil nativa, según lo indicado en 8.3.3.4), el tracking plan se limita al canal web. Se definen los siguientes eventos mínimos para instrumentar las hipótesis de 8.2.1 en una siguiente iteración con analítica embebida (ej. Google Analytics 4):

<table>
  <thead>
    <tr>
      <th align="left">Evento</th>
      <th align="left">Disparador</th>
      <th align="left">Propiedades</th>
      <th align="left">US/TS relacionado</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="left"><code>dashboard_alert_viewed</code></td>
      <td align="left">El usuario visualiza el panel de Critical Alerts en <code>/analytics/dashboard</code></td>
      <td align="left">tipo de alerta, tiempo desde login</td>
      <td align="left">TS-ST001</td>
    </tr>
    <tr>
      <td align="left"><code>medication_administration_result</code></td>
      <td align="left">Respuesta del endpoint de administración de medicamentos</td>
      <td align="left">status (success/error), mensaje de error, si hubo reintento</td>
      <td align="left">US14, US44</td>
    </tr>
    <tr>
      <td align="left"><code>resident_record_viewed</code></td>
      <td align="left">El usuario abre el detalle o historial médico de un residente</td>
      <td align="left">sección visitada (contacto, alergias), tiempo en la vista</td>
      <td align="left">TS-RM002</td>
    </tr>
    <tr>
      <td align="left"><code>resident_update_submitted</code></td>
      <td align="left">Envío del formulario PATCH de residente o personal</td>
      <td align="left">campos modificados, resultado (200/400), incluyó foto nueva</td>
      <td align="left">TS-RM-005</td>
    </tr>
  </tbody>
</table>

Esta instrumentación queda registrada como trabajo pendiente para la siguiente iteración (ver 8.4.2), dado que en este release la evidencia se recolectó mediante entrevistas directas y pruebas técnicas en lugar de analítica embebida en producción.

---

### 8.3. Experimentation

#### 8.3.1. To-Be User Stories
A partir de los hallazgos de experimentación, se consolida el backlog de producto con las historias de usuario enfocadas en la versión To-Be de Veyra. Estas historias engloban la experiencia validada de los distintos roles (visitante, familiar, administrador, desarrollador) con una usabilidad y flujos optimizados.

<table>
  <thead>
    <tr>
      <th align="left">ID</th>
      <th align="left">Título</th>
      <th align="left">Descripción (To-Be Validado)</th>
      <th align="left">Criterios de Aceptación</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="left"><strong>US12</strong></td>
      <td align="left">Registro de residentes</td>
      <td align="left">Como administrador, quiero crear y mantener perfiles completos de cada residente con un flujo guiado para centralizar su información.</td>
      <td align="left">Dado que el admin ingresa datos válidos, cuando guarda el perfil, entonces el sistema genera un ID único y confirma el registro sin fricciones.</td>
    </tr>
    <tr>
      <td align="left"><strong>TS-RM002</strong></td>
      <td align="left">Ver expediente detallado</td>
      <td align="left">Como desarrollador, quiero un endpoint GET optimizado que devuelva la información del residente para consulta rápida.</td>
      <td align="left">Dado un ID válido, cuando la API lo encuentra, responde 200 con la data completa en formato listo para resúmenes visuales.</td>
    </tr>
    <tr>
      <td align="left"><strong>TS-RM-005</strong></td>
      <td align="left">Actualizar info. de pacientes</td>
      <td align="left">Como desarrollador, quiero un endpoint PATCH para modificar datos puntuales (ej. contactos) en la interfaz con menos clics.</td>
      <td align="left">Dado un cambio puntual, cuando se envía el PATCH, el sistema actualiza solo ese campo y confirma.</td>
    </tr>
    <tr>
      <td align="left"><strong>US14</strong></td>
      <td align="left">Administración de medicamentos</td>
      <td align="left">Como personal asistencial, quiero registrar la toma de un medicamento del inventario compartido de la casa de reposo, con una acción clara desde el perfil del residente.</td>
      <td align="left">Dado que se registra una toma con stock suficiente, el sistema descuenta la cantidad del inventario compartido (<strong>TS-I002</strong>) y guarda el registro con fecha/hora. Si el stock es insuficiente, muestra un mensaje de error claro con opción de reintento (<strong>US44</strong>).</td>
    </tr>
    <tr>
      <td align="left"><strong>TS-I002</strong></td>
      <td align="left">Inventario compartido de medicamentos</td>
      <td align="left">Como desarrollador, quiero un endpoint POST/GET a nivel de casa de reposo (no por residente) para administrar el catálogo compartido de medicamentos, incluyendo lote.</td>
      <td align="left">Dado POST con nombre, lote, cantidad y fecha de vencimiento, cuando se valida (sin duplicar nombre+lote), retorna 201 y el objeto creado en el inventario de la casa de reposo.</td>
    </tr>
    <tr>
      <td align="left"><strong>TS-EM001</strong></td>
      <td align="left">Agregar empleado</td>
      <td align="left">Como desarrollador, quiero un endpoint POST para registrar nuevos empleados (cuidadores, enfermeros) y que al asignarles un rol vía contrato, el sistema informe los permisos otorgados.</td>
      <td align="left">Dado POST con datos y rol, cuando se crea el contrato del empleado, el sistema calcula y devuelve la lista de permisos asignados según su rol (DOCTOR, NURSE, CAREGIVER, COOK, ADMINISTRATIVE).</td>
    </tr>
    <tr>
      <td align="left"><strong>TS18</strong></td>
      <td align="left">Autenticación y MFA</td>
      <td align="left">Como desarrollador, quiero implementar 2FA (TOTP o SMS, a elección del usuario) para proteger el acceso a información sensible de salud.</td>
      <td align="left">Dado login correcto, cuando MFA está activo, el sistema bloquea el acceso hasta verificar el código recibido por autenticador (TOTP) o por SMS (Twilio), según el método configurado por el usuario.</td>
    </tr>
    <tr>
      <td align="left"><strong>TS17</strong></td>
      <td align="left">Integración con Stripe (pagos)</td>
      <td align="left">Como desarrollador, quiero integrar pagos reales (no simulados) para que las familias paguen la mensualidad desde la app usando su propia tarjeta.</td>
      <td align="left">Dado el ingreso real de los datos de una tarjeta en el checkout (Stripe Elements), cuando se confirma el pago, el sistema crea la suscripción y el estado del pago queda registrado (SUCCEEDED) en el backend.</td>
    </tr>
    <tr>
      <td align="left"><strong>TS-NH001</strong></td>
      <td align="left">Crear Nursing Home</td>
      <td align="left">Como desarrollador, quiero que el administrador registre su casa de reposo (Onboarding fluido).</td>
      <td align="left">Dado POST con RUC y nombre, cuando se valida, vincula la sede al administrador.</td>
    </tr>
    <tr>
      <td align="left"><strong>TS-ST001</strong></td>
      <td align="left">Dashboard de Estadísticas</td>
      <td align="left">Como administrador, quiero un panel priorizado con métricas de ocupación y alertas críticas para tomar decisiones operativas rápidas.</td>
      <td align="left">Dado el acceso al dashboard (<code>/analytics/dashboard</code>), el sistema calcula la ocupación real de habitaciones y muestra alertas críticas de stock bajo/vencimiento próximo de medicamentos en la parte superior de la vista.</td>
    </tr>
    <tr>
      <td align="left"><strong>US02</strong></td>
      <td align="left">Visualización de Planes</td>
      <td align="left">Como visitante, quiero ver los planes en la landing (sitio independiente de la aplicación web) con una comparativa clara para elegir fácilmente.</td>
      <td align="left">Dado ingreso a la landing, muestra comparativa de características y costos de forma destacada, con toggle mensual/anual.</td>
    </tr>
    <tr>
      <td align="left"><strong>US38</strong></td>
      <td align="left">Protección de datos (Cifrado)</td>
      <td align="left">Como administrador, quiero que la información médica sensible del residente (descripción y dosis de medicamentos) esté cifrada para cumplir normativas.</td>
      <td align="left">Dado almacenamiento de datos médicos sensibles (descripción y dosis de medicación), al guardarse en BD, se cifran en reposo (AES-256-GCM) de forma invisible al usuario, sin afectar la validación de duplicados por nombre/lote.</td>
    </tr>
    <tr>
      <td align="left"><strong>US44</strong></td>
      <td align="left">Manejo de errores comprensible</td>
      <td align="left">Como usuario, quiero que el sistema me guíe de forma clara cuando ocurre un error, con una opción visible para reintentar la acción.</td>
      <td align="left">Dado un fallo de red o validación (ej. stock insuficiente), al enviar datos, el sistema muestra una notificación (toast) con el mensaje real del backend y un botón "Retry" que reintenta la misma acción.</td>
    </tr>
  </tbody>
</table>

#### 8.3.2. To-Be Product Backlog
El backlog de producto To-Be ha sido priorizado según el impacto de negocio validado en la fase de experimentación. Las funcionalidades que mostraron reducir la fricción operativa y mejorar la toma de decisiones se han posicionado con la más alta prioridad.

<table>
  <thead>
    <tr>
      <th align="center">Prioridad</th>
      <th align="left">ID</th>
      <th align="left">Elemento To-Be</th>
      <th align="left">Impacto Validado (Post-Experimentos)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center"><strong>1</strong></td>
      <td align="left"><strong>TS-ST001</strong></td>
      <td align="left">Dashboard de Estadísticas</td>
      <td align="left">Esencial para la toma de decisiones diaria; se comprobó que reduce tiempos de búsqueda al destacar métricas críticas.</td>
    </tr>
    <tr>
      <td align="center"><strong>1</strong></td>
      <td align="left"><strong>US44</strong></td>
      <td align="left">Manejo de errores comprensible</td>
      <td align="left">Crítico en el flujo operativo; la validación demostró que mensajes claros evitan el abandono y la pérdida de datos.</td>
    </tr>
    <tr>
      <td align="center"><strong>1</strong></td>
      <td align="left"><strong>US14</strong></td>
      <td align="left">Administración de medicamentos</td>
      <td align="left">Flujo core optimizado para reducir la tasa de error al registrar tomas diarias. Vinculado a <strong>TS-I002</strong>.</td>
    </tr>
    <tr>
      <td align="center"><strong>2</strong></td>
      <td align="left"><strong>US12</strong></td>
      <td align="left">Registro de residentes</td>
      <td align="left">Mejora en la estructuración de la información y la jerarquía visual. Vinculado con <strong>TS-RM002</strong> y <strong>TS-RM-005</strong>.</td>
    </tr>
    <tr>
      <td align="center"><strong>2</strong></td>
      <td align="left"><strong>TS18</strong></td>
      <td align="left">Autenticación y MFA</td>
      <td align="left">Habilitador indispensable para la seguridad y la confianza de las familias y la clínica (<strong>US38</strong> Cifrado).</td>
    </tr>
    <tr>
      <td align="center"><strong>3</strong></td>
      <td align="left"><strong>TS-NH001</strong></td>
      <td align="left">Crear Nursing Home</td>
      <td align="left">Optimización del flujo de Onboarding para nuevos clientes.</td>
    </tr>
    <tr>
      <td align="center"><strong>3</strong></td>
      <td align="left"><strong>TS17</strong></td>
      <td align="left">Integración con Stripe</td>
      <td align="left">Facilitador de recaudación, validado como mejora de conveniencia para familiares.</td>
    </tr>
    <tr>
      <td align="center"><strong>4</strong></td>
      <td align="left"><strong>US02</strong></td>
      <td align="left">Visualización de Planes (Landing)</td>
      <td align="left">Generador de leads para escalar el negocio.</td>
    </tr>
  </tbody>
</table>

#### 8.3.3. Pipeline-supported, Experiment-Driven To-Be Software Platform Lifecycle
El backlog To-Be priorizado en 8.3.2 se ejecutó a través de un pipeline de CI/CD que permitió desplegar cada incremento de forma independiente (landing, frontend web, API/backend) y recolectar evidencia real de funcionamiento antes de cerrar cada hipótesis de experimentación. Cada sprint cerró con una demo funcional y una verificación de rendimiento/calidad sobre el ambiente desplegado (Firebase Hosting / Cloud Run), de modo que la evidencia de esta sección corresponde a artefactos efectivamente implementados y no solo diseñados.

##### 8.3.3.1. To-Be Sprint Backlogs

<table>
  <thead>
    <tr>
      <th align="center">Sprint</th>
      <th align="left">Elementos (US/TS)</th>
      <th align="left">Objetivo del Sprint</th>
      <th align="center">Estado</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center"><strong>Sprint 1</strong></td>
      <td align="left"><strong>TS-ST001</strong>, <strong>US44</strong></td>
      <td align="left">Rediseñar el Dashboard de Estadísticas y estandarizar el manejo de errores comprensible en los flujos críticos.</td>
      <td align="center">Completado</td>
    </tr>
    <tr>
      <td align="center"><strong>Sprint 2</strong></td>
      <td align="left"><strong>US14</strong>, <strong>TS-I002</strong></td>
      <td align="left">Optimizar la UI de administración de medicamentos y el endpoint de inventario asociado.</td>
      <td align="center">Completado</td>
    </tr>
    <tr>
      <td align="center"><strong>Sprint 3</strong></td>
      <td align="left"><strong>US12</strong>, <strong>TS-RM002</strong>, <strong>TS-RM-005</strong></td>
      <td align="left">Consolidar el registro de residentes y la vista de expediente rápido, reduciendo pasos en la actualización de datos.</td>
      <td align="center">Completado</td>
    </tr>
    <tr>
      <td align="center"><strong>Sprint 4</strong></td>
      <td align="left"><strong>TS18</strong>, <strong>US38</strong></td>
      <td align="left">Habilitar autenticación multifactor y cifrado de datos sensibles en reposo.</td>
      <td align="center">Completado</td>
    </tr>
    <tr>
      <td align="center"><strong>Sprint 5</strong></td>
      <td align="left"><strong>TS-NH001</strong>, <strong>TS17</strong>, <strong>US02</strong></td>
      <td align="left">Cerrar el flujo de onboarding de nuevas casas de reposo, integración de pagos y landing comercial.</td>
      <td align="center">Completado</td>
    </tr>
  </tbody>
</table>

##### 8.3.3.2. Implemented To-Be Landing Page Evidence
La landing page de Veyra vive en un repositorio y dominio independiente de la aplicación web (`Veyra-Landing-Page`, desplegada en GitHub Pages), e implementa la comparativa de planes definida en **US02**: hero, sección de características ("What We Offer" y "Features"), beneficios, y una sección de planes con toggle mensual/anual, precios destacados y lista de características por plan (Family Plan y Nursing Home Plan).

![Rendimiento Home](../assets/img/chapter-VIII/Plans.png)

##### 8.3.3.3. Implemented To-Be Frontend-Web Application Evidence
Se ejecutaron auditorías de rendimiento sobre el frontend desplegado (`veyra-frontend-application.web.app`) para validar que las mejoras de jerarquía visual e interacción (relacionadas a **TS-ST001** y **US44**) no degradaran la performance percibida.

**Vista `/home` (Landing/bienvenida de la app, con acceso a inicio de sesión):**

![Rendimiento Home](../assets/img/chapter-VIII/Rendimiento1.png)

Rendimiento: 95 · Accesibilidad: 96 · Recomendaciones: 100 · SEO: 83

**Vista `/iam/sign-in` (Autenticación):**

![Rendimiento Sign-in](../assets/img/chapter-VIII/Rendimiento2.png)

Rendimiento: 95 · Accesibilidad: 96 · Recomendaciones: 100 · SEO: 75

Ambas vistas mantienen un puntaje de Rendimiento y Accesibilidad superior a 95/96, lo que confirma que el flujo de autenticación (ligado a **TS18**) no introdujo regresiones de performance tras la implementación. El Dashboard de Estadísticas (**TS-ST001**) vive en la ruta `/analytics/dashboard` (no en `/home`, que es la página de bienvenida de la app) y ahora incluye, además de los gráficos de RR.HH. ya existentes, una tarjeta de **ocupación** (calculada a partir de las habitaciones reales de la casa de reposo) y un panel de **alertas críticas** (medicamentos con stock bajo o próximos a vencer), cerrando la brecha detectada entre lo documentado y lo implementado en la revisión de esta entrega.

![OcupacionesYAlertas](../assets/img/chapter-VIII/DashboardOcupacionAlertas.png)

La captura anterior corresponde a un ambiente de prueba desplegado (casa de reposo con una habitación de capacidad 2 y un residente asignado, más un medicamento con lote próximo a vencer y stock bajo), y muestra la tarjeta de **Occupancy** (50%, 1/2 ocupado) calculada a partir de habitaciones reales, junto con el panel de **Critical Alerts** listando ambos tipos de alerta definidos en TS-ST001 (`LOW_STOCK` y `EXPIRING_SOON`) en la parte superior de la vista, sin necesidad de scroll.

##### 8.3.3.4. Implemented To-Be Native-Mobile Application Evidence
Para este ciclo de experimentación, el equipo priorizó la validación de las hipótesis del backlog (8.3.2) sobre la landing page, el frontend web y la API/backend, dado que estas plataformas concentran el mayor volumen de interacción de administradores, personal asistencial y familiares durante el As-Is (8.1.1). En consecuencia, **no se desarrolló una aplicación nativa móvil dentro del alcance de este release**; esta queda registrada como parte del roadmap futuro del producto (ver Conclusiones y recomendaciones), donde se plantea extender la experiencia validada en web (Dashboard, manejo de errores y registro de medicamentos) a una plataforma móvil nativa en una siguiente iteración.

##### 8.3.3.5. Implemented To-Be RESTful API and/or Serverless Backend Evidence
Los endpoints priorizados en el backlog (**TS-RM002** GET, **TS-RM-005** PATCH, **TS-I002** POST, **TS-EM001** POST, **TS-NH001** POST) se encuentran desplegados y responden según los criterios de aceptación definidos en 8.3.1. Como parte del cierre de esta entrega (TB2), se corrigieron y completaron los siguientes endpoints, previamente ausentes, simulados, o con defectos detectados en pruebas reales sobre el ambiente desplegado:

<table>
  <thead>
    <tr>
      <th align="left">US/TS</th>
      <th align="left">Endpoint</th>
      <th align="left">Estado al cierre de TB2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="left"><strong>TS-I002</strong></td>
      <td align="left"><code>GET/POST /api/v1/nursing-homes/{nursingHomeId}/medications</code></td>
      <td align="left">Migrado de inventario por residente a inventario compartido por casa de reposo, con campo <code>lot</code>.</td>
    </tr>
    <tr>
      <td align="left"><strong>US14</strong></td>
      <td align="left"><code>POST/GET /api/v1/residents/{residentId}/medications/{medicationId}/administrations</code></td>
      <td align="left">Endpoint implementado desde cero; antes solo existía la lógica de dominio sin ningún controlador que la expusiera.</td>
    </tr>
    <tr>
      <td align="left"><strong>TS-ST001</strong></td>
      <td align="left"><code>GET /api/v1/nursing-homes/{nursingHomeId}/dashboard/occupancy</code> y <code>/dashboard/alerts</code></td>
      <td align="left">Endpoints nuevos: ocupación real de habitaciones y alertas críticas de inventario (stock bajo / vencimiento próximo).</td>
    </tr>
    <tr>
      <td align="left"><strong>TS-EM001</strong></td>
      <td align="left"><code>POST /api/v1/staff/{staffMemberId}/contracts</code></td>
      <td align="left">La respuesta ahora incluye <code>permissions</code>, calculados según el rol asignado (DOCTOR, NURSE, CAREGIVER, COOK, ADMINISTRATIVE).</td>
    </tr>
    <tr>
      <td align="left"><strong>TS17</strong></td>
      <td align="left"><code>POST /api/v1/webhooks/stripe</code></td>
      <td align="left">Webhook de Stripe expuesto (antes era código inalcanzable); el checkout del frontend ahora tokeniza tarjetas reales vía Stripe Elements en vez de un token de prueba fijo.</td>
    </tr>
    <tr>
      <td align="left"><strong>TS18</strong></td>
      <td align="left"><code>POST /authentication/mfa/sms/setup</code>, <code>GET /authentication/mfa/status</code></td>
      <td align="left">Segundo factor por SMS (Twilio) añadido junto al TOTP existente; nuevo endpoint de estado para que el frontend sepa si MFA está activo y con qué método.</td>
    </tr>
    <tr>
      <td align="left"><strong>US38</strong></td>
      <td align="left"><code>Medication.description</code> / <code>Medication.dosage</code></td>
      <td align="left">Campos cifrados en reposo (AES-256-GCM), antes solo se cifraban los mensajes de comunicación familiar.</td>
    </tr>
    <tr>
      <td align="left"><strong>TS-RM-005</strong></td>
      <td align="left"><code>PATCH /api/v1/residents/{residentId}</code>, <code>PATCH /api/v1/staff/{staffMemberId}</code></td>
      <td align="left">Se encontró y corrigió un defecto que bloqueaba la actualización (400 Bad Request) cuando el usuario editaba datos sin cambiar la foto: el ensamblador intentaba decodificar como Base64 la URL de la foto ya almacenada (Cloudinary) en lugar de omitir el campo cuando no hay una imagen nueva (<code>data:</code>). Detectado y corregido durante pruebas reales con cuentas de administrador y personal asistencial.</td>
    </tr>
    <tr>
      <td align="left"><strong>TS-NH001</strong></td>
      <td align="left"><code>GET /api/v1/administrators/by-user/{userId}</code></td>
      <td align="left">Se encontró y corrigió un defecto de identidad: el frontend asumía que el <code>administratorId</code> era igual al <code>userId</code> del IAM, lo cual solo coincide para las primeras cuentas registradas. Se expuso un endpoint nuevo para resolver el <code>administratorId</code> real y se reemplazó un <code>setTimeout</code> fijo (causa de falsos positivos de "éxito" en la creación) por manejo reactivo del resultado real de la petición.</td>
    </tr>
  </tbody>
</table>

![Api](../assets/img/chapter-VIII/API.png)

##### 8.3.3.6. Team Collaboration Insights
Durante la ejecución de los sprints, el equipo sostuvo daily stand-ups cortos y una retrospectiva al cierre de cada sprint para ajustar el pipeline de experimentación. Los principales aprendizajes de colaboración fueron:
- La asignación de historias por rol (frontend, backend, QA) según el mapeo US/TS redujo bloqueos de dependencias entre endpoints y vistas.
- Las retrospectivas evidenciaron que revisar el Question Backlog (8.1.4) antes de cada sprint ayudó a mantener el foco en las hipótesis con mayor puntaje, evitando trabajo especulativo.
- La comunicación asíncrona sobre el estado de los despliegues (pipeline CI/CD) permitió validar evidencia de rendimiento (8.3.3.3) sin necesidad de reuniones adicionales.

#### 8.3.4. To-Be Validation Interviews

##### 8.3.4.1. Diseño de Entrevistas
Las entrevistas de validación buscan confirmar si las hipótesis del backlog re-priorizado (8.3.2) resuelven los problemas identificados en 8.1.1. Se diseñó una guía semiestructurada dirigida a los roles clave del sistema (administrador de casa de reposo, personal asistencial y familiar/visitante).

<table>
  <thead>
    <tr>
      <th align="left">Objetivo</th>
      <th align="left">Perfil del Entrevistado</th>
      <th align="left">Preguntas Guía</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="left">Validar reducción de fricción en el Dashboard (<strong>TS-ST001</strong>)</td>
      <td align="left">Administrador de casa de reposo</td>
      <td align="left">¿Qué tan rápido puede identificar una alerta crítica desde el Dashboard? ¿Qué información le falta a simple vista?</td>
    </tr>
    <tr>
      <td align="left">Validar claridad del manejo de errores (<strong>US44</strong>) y registro de medicamentos (<strong>US14</strong>)</td>
      <td align="left">Personal asistencial (enfermería)</td>
      <td align="left">Cuando ocurre un error al registrar una toma, ¿el mensaje le indica claramente cómo resolverlo? ¿Repetiría el intento sin ayuda externa?</td>
    </tr>
    <tr>
      <td align="left">Validar confianza en notificaciones y portal de familiares</td>
      <td align="left">Familiar/visitante</td>
      <td align="left">¿Qué tan confiable percibe la información mostrada sobre el estado de su familiar? ¿Qué le generaría más confianza en el portal?</td>
    </tr>
  </tbody>
</table>

##### 8.3.4.2. Registro de Entrevistas

<table>
  <thead>
    <tr>
      <th align="center">#</th>
      <th align="left">Perfil</th>
      <th align="left">Hallazgo Principal</th>
      <th align="left">US/TS Relacionado</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center">1</td>
      <td align="left">Administrador</td>
      <td align="left">El administrador entrevistado identifica alertas críticas de ocupación y stock bajo de medicamentos en menos de 10 segundos desde que ingresa al Dashboard, frente a los más de 30 segundos que le tomaba ubicar la misma información en la versión As-Is navegando por distintas secciones. Valora que las alertas se muestren en la parte superior de la vista sin necesidad de scroll, aunque sugiere incorporar un filtro por tipo de alerta (ocupación, stock, vencimientos) para casas de reposo con mayor volumen de residentes.</td>
      <td align="left">TS-ST001</td>
    </tr>
    <tr>
      <td align="center">2</td>
      <td align="left">Personal asistencial</td>
      <td align="left">El personal de enfermería confirma que los mensajes de error mostrados al registrar una toma de medicamento (p. ej., ante pérdida de conexión o intento de descuento sin stock disponible) indican con claridad qué ocurrió y qué acción tomar, permitiendo reintentar el registro sin soporte técnico. Sin embargo, señala que la confirmación visual tras un registro exitoso es breve y puede pasar desapercibida durante turnos con alta carga de trabajo, por lo que recomienda un mensaje de confirmación más persistente o un indicador adicional en la lista de medicamentos administrados.</td>
      <td align="left">US44, US14</td>
    </tr>
    <tr>
      <td align="center">3</td>
      <td align="left">Familiar/visitante</td>
      <td align="left">El familiar entrevistado manifiesta una confianza moderada respecto a la información mostrada sobre el estado de su familiar y valora la claridad del portal, pero señala que las actualizaciones no siempre se perciben "en tiempo real", generando incertidumbre ante cambios repentinos en la condición de salud. Indica que una notificación push inmediata ante eventos relevantes (nueva toma de medicamento, alerta médica) aumentaría significativamente su confianza en la plataforma, hallazgo que sustenta por qué esta hipótesis se mantiene priorizada para el siguiente ciclo de experimentación (ver 8.4.2).</td>
      <td align="left">US02</td>
    </tr>
  </tbody>
</table>

---

### 8.4. Experiment Aftermath & Analysis

#### 8.4.1. Analysis and Interpretation of Results
Contrastando las hipótesis planteadas en los Experiment Cards (8.1.5) con la evidencia de implementación (8.3.3) y las entrevistas de validación (8.3.4.2), se observa lo siguiente:

- **Dashboard más visible (TS-ST001):** la hipótesis de reducir el tiempo de acceso a información crítica se sostiene; el rediseño mantuvo un puntaje de Rendimiento de 95 (8.3.3.3) y, según el registro de entrevistas, los administradores ubican alertas críticas más rápido que en la versión As-Is. Al cierre de esta entrega, la ocupación y las alertas críticas dejaron de ser una aspiración de diseño y pasaron a calcularse en tiempo real a partir de datos de habitaciones e inventario (8.3.3.5), confirmando la hipótesis con evidencia funcional, no solo de rendimiento.
- **Jerarquía de información y manejo de errores (US44/US14):** la hipótesis de disminución de errores operativos se confirma; el personal asistencial reporta mayor claridad en los mensajes de error, y la observación sobre la "confirmación visual breve" quedó resuelta al reemplazar los banners inline por notificaciones (toast) persistentes con botón de reintento visible, además de habilitarse por primera vez el endpoint real de registro de toma de medicamentos (US14), que hasta esta entrega era lógica de dominio sin ningún endpoint que la invocara.
- **Resúmenes de salud (TS-RM002):** al no contarse aún con evidencia cuantitativa de tiempos de decisión clínica, esta hipótesis permanece **no concluyente** y se traslada al backlog re-priorizado (8.4.2) para una siguiente ronda de experimentación. La verificación de código realizada al cierre de esta entrega confirma que el endpoint `GET /residents/{residentId}` (TS-RM002) está implementado y responde según lo diseñado, pero la vista de "expediente detallado" en el frontend está **fragmentada**: la pantalla de detalle del residente solo muestra datos de contacto y representante legal, la sección llamada "Historial médico" únicamente lista alergias, y los signos vitales (`VitalSign`) cuentan con API pero **no tienen todavía una vista propia**. En consecuencia, el "resumen de salud rápido" que plantea la hipótesis no existe hoy como una vista unificada, lo cual es una causa adicional (más allá de la falta de métricas) de por qué esta hipótesis se mantiene no concluyente.
- **Navegación simplificada (TS-RM-005):** la reducción de pasos se implementó según lo diseñado a nivel de flujo, pero la verificación de código encontró que el endpoint `PATCH /residents/{residentId}` (y su equivalente `PATCH /staff/{staffMemberId}`) devolvía **400 Bad Request** al editar un residente o un empleado sin reemplazar su foto, porque el ensamblador intentaba decodificar como Base64 la URL de la foto ya almacenada. Este defecto fue corregido durante el cierre de esta entrega (8.3.3.5) y confirmado en producción; con la corrección aplicada, la hipótesis puede evaluarse de forma confiable, aunque aún falta validar con métricas de clics reales.

En conjunto, los resultados sugieren que las mejoras de mayor confianza e impacto (Dashboard y manejo de errores) fueron validadas con evidencia de implementación, mientras que las hipótesis ligadas a decisiones clínicas y navegación requieren un ciclo adicional de medición. Adicionalmente, el cierre de esta entrega permitió corregir brechas entre lo documentado y lo realmente implementado en TS17 (pagos antes simulados con un token de prueba fijo, ahora tokenización real vía Stripe Elements), TS18 (verificación por SMS agregada junto al TOTP existente), US38 (cifrado extendido de mensajes de comunicación a datos de medicación), TS-RM-005 (defecto de actualización de residentes/personal por manejo incorrecto de la foto ya almacenada) y TS-NH001 (defecto de identidad entre `userId` y `administratorId` que impedía completar el onboarding de nuevas casas de reposo), reforzando la responsabilidad profesional de documentar únicamente lo que el sistema efectivamente hace.

#### 8.4.2. Re-scored and Re-prioritized Question Backlog

<table>
  <thead>
    <tr>
      <th align="left">Pregunta</th>
      <th align="center">Confianza</th>
      <th align="center">Riesgo</th>
      <th align="center">Impacto</th>
      <th align="center">Interés</th>
      <th align="center">Puntaje Total</th>
      <th align="left">Estado</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="left">¿Un dashboard (TS-ST001) más visible reducirá el tiempo para acceder a info de residentes?</td>
      <td align="center">9</td>
      <td align="center">1</td>
      <td align="center">9</td>
      <td align="center">7</td>
      <td align="center">26</td>
      <td align="left">Validada</td>
    </tr>
    <tr>
      <td align="left">¿Una mejor jerarquía de información y manejo de errores (US44) reducirá errores al registrar medicamentos (US14)?</td>
      <td align="center">8</td>
      <td align="center">2</td>
      <td align="center">9</td>
      <td align="center">7</td>
      <td align="center">26</td>
      <td align="left">Validada parcialmente</td>
    </tr>
    <tr>
      <td align="left">¿Un flujo de navegación simple mejorará la finalización de tareas de actualización (TS-RM-005)?</td>
      <td align="center">9</td>
      <td align="center">1</td>
      <td align="center">8</td>
      <td align="center">8</td>
      <td align="center">26</td>
      <td align="left">Validada (defecto de reenvío de foto corregido y confirmado en producción; falta métrica de clics)</td>
    </tr>
    <tr>
      <td align="left">¿Resúmenes de salud rápidos (TS-RM002) mejorarán la toma de decisiones en el cuidado?</td>
      <td align="center">6</td>
      <td align="center">4</td>
      <td align="center">9</td>
      <td align="center">7</td>
      <td align="center">26</td>
      <td align="left">No concluyente</td>
    </tr>
    <tr>
      <td align="left">¿Notificaciones para familiares mejoradas aumentarán la confianza y el uso del portal?</td>
      <td align="center">6</td>
      <td align="center">4</td>
      <td align="center">8</td>
      <td align="center">8</td>
      <td align="center">26</td>
      <td align="left">Próximo ciclo</td>
    </tr>
    <tr>
      <td align="left">¿Resolver el desajuste entre <code>userId</code> y <code>administratorId</code> (TS-NH001) permitirá completar el onboarding de una nueva casa de reposo sin fricción?</td>
      <td align="center">9</td>
      <td align="center">1</td>
      <td align="center">8</td>
      <td align="center">6</td>
      <td align="center">24</td>
      <td align="left">Validada (endpoint <code>GET /administrators/by-user/{userId}</code> agregado; onboarding confirmado en producción)</td>
    </tr>
    <tr>
      <td align="left">¿Corregir el flujo de inicio de sesión con MFA (TS18) evitará el bucle de error 401 al no completarse la verificación antes de consultar la suscripción?</td>
      <td align="center">9</td>
      <td align="center">2</td>
      <td align="center">9</td>
      <td align="center">7</td>
      <td align="center">27</td>
      <td align="left">Validada (el ensamblador de sign-in omitía el campo <code>mfaRequired</code>; corregido y confirmado con un flujo TOTP end-to-end)</td>
    </tr>
  </tbody>
</table>

Los dos últimos ítems no formaban parte del Question Backlog original (8.1.4): surgieron como defectos operativos críticos detectados durante las pruebas de cierre de esta entrega directamente sobre el ambiente desplegado, y se incorporan aquí siguiendo la misma lógica de re-priorización basada en evidencia real que rige el resto de esta sección.

---

### 8.5. Continuous Learning

#### 8.5.1. Shareback Session Artifacts: Learning Workflow
Al cierre del ciclo de experimentación, el equipo realizó una sesión de shareback en vivo a través de una llamada de Discord, transfiriendo los aprendizajes de 8.4.1 al resto del equipo y demostrando la evidencia funcional recolectada directamente sobre el ambiente desplegado. El flujo de aprendizaje seguido fue:

1. **Recolección:** consolidación de la evidencia de implementación (8.3.3) y hallazgos de entrevistas (8.3.4.2) en un solo repositorio de aprendizajes.
2. **Síntesis:** priorización de aprendizajes accionables vs. aprendizajes que requieren más evidencia (ligados al backlog re-priorizado de 8.4.2).
3. **Shareback:** sesión en vivo por Discord con el equipo completo, donde se compartió pantalla para demostrar en producción el Dashboard de Estadísticas (**TS-ST001**) con datos reales (Occupancy 50%, alerta crítica de stock bajo para "Aspirina"), exponiendo qué hipótesis se validaron, cuáles quedaron pendientes (TS-RM002) y qué se hará en el siguiente ciclo (8.4.2).
4. **Registro:** captura de la sesión en vivo como artefacto reutilizable para futuros ciclos de experimentación (ver imagen a continuación).

![Shareback](../assets/img/chapter-VIII/shareback.jpeg)

*Captura de la sesión de shareback en vivo por Discord, con el equipo presente en la llamada mientras se demuestra el Dashboard de Estadísticas desplegado en producción (`veyra-frontend-application.web.app/analytics/dashboard`), evidenciando en tiempo real la tarjeta de Occupancy y el panel de Critical Alerts validados en 8.3.3.3 y 8.4.1.*

---

### 8.6. To-Be Software Platform Pre-launch

#### 8.6.1. About-the-Product Intro Video
Como parte del pre-lanzamiento de la plataforma To-Be, se preparó un video introductorio que resume el valor de negocio de Veyra para casas de reposo, personal asistencial y familiares, apoyado en la evidencia de implementación reunida en este capítulo.

![Entrevista](../assets/img/chapter-VIII/AboutThe.png)

[Link AbouTheProduct](https://youtu.be/-tL0iSsyfU0)
