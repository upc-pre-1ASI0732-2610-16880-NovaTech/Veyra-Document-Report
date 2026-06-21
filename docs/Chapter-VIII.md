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

*(Las subsecciones 8.2.1 a 8.2.8 se mantienen con su enfoque metodológico, añadiendo métricas de éxito directamente vinculadas a las US/TS seleccionadas. Por ejemplo, en 8.2.2 Domain Business Metrics, la "Tasa de éxito en registros" validará la **US14**, y la "Tasa de error guiado" validará la **US44**).*

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
      <td align="left">Como administrador, quiero controlar la toma de medicamentos con una UI clara que prevenga errores operativos.</td>
      <td align="left">Dado que se registra una toma, cuando hay stock, el sistema descuenta una unidad y guarda fecha/hora visualmente.</td>
    </tr>
    <tr>
      <td align="left"><strong>TS-I002</strong></td>
      <td align="left">Agregar medicamentos al inventario</td>
      <td align="left">Como desarrollador, quiero un endpoint POST para que el administrador alimente el catálogo de forma ágil.</td>
      <td align="left">Dado POST con nombre, lote y fecha, cuando se valida, retorna 201 y el objeto creado.</td>
    </tr>
    <tr>
      <td align="left"><strong>TS-EM001</strong></td>
      <td align="left">Agregar empleado</td>
      <td align="left">Como desarrollador, quiero un endpoint POST para registrar nuevos empleados (cuidadores, enfermeros) con roles.</td>
      <td align="left">Dado POST con datos y rol, cuando se crea el perfil, el sistema asigna los permisos correspondientes.</td>
    </tr>
    <tr>
      <td align="left"><strong>TS18</strong></td>
      <td align="left">Autenticación y MFA</td>
      <td align="left">Como desarrollador, quiero implementar 2FA para proteger el acceso a información sensible de salud.</td>
      <td align="left">Dado login correcto, cuando 2FA está activo, el sistema bloquea el acceso hasta verificar el código SMS/TOTP.</td>
    </tr>
    <tr>
      <td align="left"><strong>TS17</strong></td>
      <td align="left">Integración con Stripe (pagos)</td>
      <td align="left">Como desarrollador, quiero integrar pagos para que las familias paguen la mensualidad desde la app.</td>
      <td align="left">Dado el pago de una cuota, cuando Stripe confirma, el sistema actualiza el estado a "Pagado".</td>
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
      <td align="left">Como administrador, quiero un panel priorizado con métricas para tomar decisiones operativas rápidas.</td>
      <td align="left">Dado el acceso al dashboard, cuando el sistema calcula datos, muestra gráficos de ocupación y alertas críticas en la vista superior.</td>
    </tr>
    <tr>
      <td align="left"><strong>US02</strong></td>
      <td align="left">Visualización de Planes</td>
      <td align="left">Como visitante, quiero ver los planes en la landing con una comparativa clara para elegir fácilmente.</td>
      <td align="left">Dado ingreso a la landing, muestra comparativa de características y costos de forma destacada.</td>
    </tr>
    <tr>
      <td align="left"><strong>US38</strong></td>
      <td align="left">Protección de datos (Cifrado)</td>
      <td align="left">Como administrador, quiero que toda la información médica esté cifrada para cumplir normativas.</td>
      <td align="left">Dado almacenamiento sensible, al guardarse en BD, se cifran en reposo de forma invisible al usuario.</td>
    </tr>
    <tr>
      <td align="left"><strong>US44</strong></td>
      <td align="left">Manejo de errores comprensible</td>
      <td align="left">Como usuario, quiero que el sistema me guíe de forma clara cuando ocurre un error (validado en experimentos).</td>
      <td align="left">Dado un fallo de red o validación, al enviar datos, el sistema muestra un mensaje claro y opción de reintento.</td>
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
