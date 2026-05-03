## 3.1. User Stories. 
<p>Para la especificación de requisitos de los usuarios, se desarrollaron las historias de usuario que describen cada requisito y funcionalidad que debe estar implementado en el desarrollo del producto final para satisfacer las necesidades del público objetivo. A continuación se presentan las historias de usuario relacionadas con la plataforma "Veyra". Esta sección reúne historias de usuario centradas en la experiencia de los distintos roles: el visitante, el familiar del adulto mayor y el administrador de la casa de reposo. Aquí se definen las necesidades clave para cada uno, desde la navegación inicial y contacto, hasta la gestión detallada de residentes, personal y medicamentos.</p>

  <table>
    <thead>
        <tr>
            <th>ID</th>
            <th>Título</th>
            <th>Descripción</th>
            <th>Criterios de Aceptación</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>US12</td>
            <td>Registro de residentes</td>
            <td>Como administrador, quiero crear y mantener perfiles completos de cada residente para centralizar toda su información personal y médica.</td>
            <td>Dado que el admin ingresa datos válidos, cuando guarda el perfil, entonces el sistema genera un ID único y confirma el registro.</td>
        </tr>
        <tr>
            <td>TS-RM002</td>
            <td>Ver expediente detallado</td>
            <td>Como desarrollador, quiero un endpoint GET que devuelva la información completa del residente para consulta del personal autorizado.</td>
            <td>Dado un ID de residente válido, cuando la API lo encuentra, entonces responde 200 con la data personal y médica completa.</td>
        </tr>
        <tr>
            <td>TS-RM-005</td>
            <td>Actualizar información de pacientes</td>
            <td>Como desarrollador, quiero un endpoint PATCH para modificar datos del perfil del residente (contactos de emergencia, condiciones nuevas).</td>
            <td>Dado un cambio en el contacto de emergencia, cuando se envía el PATCH, entonces el sistema actualiza solo ese campo y confirma.</td>
        </tr>
        <tr>
            <td>US14</td>
            <td>Administración de medicamentos</td>
            <td>Como administrador, quiero controlar la toma de medicamentos de los residentes para garantizar cumplimiento de tratamientos.</td>
            <td>Dado que se registra una toma, cuando el medicamento tiene stock, entonces el sistema descuenta una unidad y guarda fecha/hora.</td>
        </tr>
        <tr>
            <td>TS-I002</td>
            <td>Agregar medicamentos al inventario</td>
            <td>Como desarrollador, quiero un endpoint POST para que el administrador pueda alimentar el catálogo de medicinas de la casa de reposo.</td>
            <td>Dado POST con nombre, lote y fecha de vencimiento, cuando se valida, entonces retorna 201 y el objeto creado.</td>
        </tr>
        <tr>
            <td>TS-EM001</td>
            <td>Agregar empleado</td>
            <td>Como desarrollador, quiero implementar un endpoint POST para registrar nuevos empleados (cuidadores, enfermeros) con roles.</td>
            <td>Dado POST con datos personales y rol, cuando se crea el perfil, entonces el sistema asigna los permisos correspondientes.</td>
        </tr>
        <tr>
            <td>TS18</td>
            <td>Autenticación y MFA</td>
            <td>Como desarrollador, quiero implementar 2FA para proteger el acceso a información sensible de salud de los adultos mayores.</td>
            <td>Dado login correcto, cuando el 2FA está activo, entonces el sistema bloquea el acceso hasta verificar el código SMS/TOTP.</td>
        </tr>
        <tr>
            <td>TS17</td>
            <td>Integración con Stripe (pagos)</td>
            <td>Como desarrollador, quiero integrar pagos para que las familias paguen la mensualidad de la casa de reposo desde la app.</td>
            <td>Dado el pago de una cuota, cuando Stripe confirma el cargo, entonces el sistema actualiza el estado de la cuenta a "Pagado".</td>
        </tr>
        <tr>
            <td>TS-NH001</td>
            <td>Crear Nursing Home (Onboarding)</td>
            <td>Como desarrollador, quiero que el administrador registre su casa de reposo tras crear su cuenta para habilitar las funciones de gestión.</td>
            <td>Dado POST con RUC y nombre legal, cuando se valida la empresa, entonces vincula la sede al administrador.</td>
        </tr>
        <tr>
            <td>TS-ST001</td>
            <td>Dashboard de Estadísticas</td>
            <td>Como administrador, quiero un panel con métricas (ocupación, residentes activos) para tomar decisiones operativas.</td>
            <td>Dado el acceso al dashboard, cuando el sistema calcula datos, entonces muestra gráficos de ocupación y alertas críticas.</td>
        </tr>
        <tr>
            <td>US02</td>
            <td>Visualización de Planes en Landing</td>
            <td>Como visitante, quiero ver los planes de suscripción y sus precios para elegir el que mejor se adapte a mi presupuesto.</td>
            <td>Dado ingreso a la landing, cuando se visualiza la sección planes, entonces muestra comparativa de características y costos.</td>
        </tr>
        <tr>
            <td>US38</td>
            <td>Protección de datos mediante cifrado</td>
            <td>Como administrador, quiero que toda la información médica esté cifrada para cumplir con las normativas de protección de datos personales.</td>
            <td>Dado almacenamiento de datos sensibles, cuando se guardan en DB, entonces deben estar cifrados en reposo.</td>
        </tr>
        <tr>
            <td>US44</td>
            <td>Manejo de errores comprensible</td>
            <td>Como usuario, quiero que el sistema me guíe cuando ocurre un error (ej. falta de internet) para no perder la información ingresada.</td>
            <td>Dado un fallo de red al guardar, cuando el usuario pulsa enviar, entonces el sistema muestra mensaje claro y opción de reintento.</td>
        </tr>
    </tbody>
</table>

## 3.2. Product Backlog. 

En esta sección se presenta el Product Backlog priorizado, el cual contiene las Historias de Usuario y Technical Stories estimadas en Story Points. El orden de los elementos ha sido determinado por el valor que aportan al negocio, priorizando en las primeras iteraciones los elementos de la Landing Page y las funcionalidades core del sistema.

<table>
    <thead>
        <tr>
            <th>#</th>
            <th>ID</th>
            <th>Título</th>
            <th>Descripción</th>
            <th>Estimación (SP)</th>
        </tr>
    </thead>
    <tbody>
        <tr><td>1</td><td>TS-NH001</td><td>Crear Nursing Home (Onboarding)</td><td>Como desarrollador quiero que el administrador registre su casa de reposo tras crear su cuenta para habilitar las funciones de gestión.</td><td>5</td></tr>
        <tr><td>2</td><td>US12</td><td>Registro de residentes</td><td>Como administrador quiero crear y mantener perfiles completos de cada residente para centralizar toda su información personal y médica.</td><td>5</td></tr>
        <tr><td>3</td><td>TS-RM002</td><td>Ver expediente detallado</td><td>Como desarrollador quiero un endpoint GET que devuelva la información completa del residente para consulta del personal autorizado.</td><td>2</td></tr>
        <tr><td>4</td><td>TS-RM-005</td><td>Actualizar información de pacientes</td><td>Como desarrollador quiero un endpoint PATCH para modificar datos del perfil del residente (contactos de emergencia, condiciones nuevas).</td><td>3</td></tr>
        <tr><td>5</td><td>TS-EM001</td><td>Agregar empleado</td><td>Como desarrollador quiero implementar un endpoint POST para registrar nuevos empleados (cuidadores, enfermeros) con roles.</td><td>3</td></tr>
        <tr><td>6</td><td>US14</td><td>Administración de medicamentos</td><td>Como administrador quiero controlar la toma de medicamentos de los residentes para garantizar cumplimiento de tratamientos.</td><td>3</td></tr>
        <tr><td>7</td><td>TS-I002</td><td>Agregar medicamentos al inventario</td><td>Como desarrollador quiero un endpoint POST para que el administrador pueda alimentar el catálogo de medicinas de la casa de reposo.</td><td>2</td></tr>
        <tr><td>8</td><td>US20</td><td>Preguntas sobre rutina diaria</td><td>Como familiar quiero enviar preguntas directas al personal sobre el día a día de mi familiar para resolver dudas puntuales.</td><td>3</td></tr>
        <tr><td>9</td><td>TS18</td><td>Autenticación y MFA</td><td>Como desarrollador quiero implementar 2FA para proteger el acceso a información sensible de salud de los adultos mayores.</td><td>8</td></tr>
        <tr><td>10</td><td>US38</td><td>Protección de datos mediante cifrado</td><td>Como administrador quiero que toda la información médica esté cifrada para cumplir con las normativas de protección de datos personales.</td><td>5</td></tr>
        <tr><td>11</td><td>TS17</td><td>Integración con Stripe (pagos)</td><td>Como desarrollador quiero integrar pagos para que las familias paguen la mensualidad de la casa de reposo desde la app.</td><td>8</td></tr>
        <tr><td>12</td><td>TS-ST001</td><td>Dashboard de Estadísticas</td><td>Como administrador quiero un panel con métricas (ocupación, residentes activos) para tomar decisiones operativas.</td><td>5</td></tr>
        <tr><td>13</td><td>US02</td><td>Visualización de Planes en Landing</td><td>Como visitante quiero ver los planes de suscripción y sus precios para elegir el que mejor se adapte a mi presupuesto.</td><td>2</td></tr>
        <tr><td>14</td><td>US44</td><td>Manejo de errores comprensible</td><td>Como usuario quiero que el sistema me guíe cuando ocurre un error para no perder la información ingresada.</td><td>3</td></tr>
    </tbody>
</table>

**Evidencia de Product Backlog en Jira:**

A continuación, se muestra la gestión del backlog en la herramienta Jira Software, evidenciando la priorización y estimación de las historias.

<div align="center">
  <img src="../assets/img/chapter-I/Product Backlog screenshot.jpg" alt="Evidence Product Backlog Jira" width="90%">
  <p><em>Figura: Captura del Product Backlog en Jira Software.</em></p>
</div>

## 3.3. Impact Mapping. 

<p>
  En el Impact Mapping del modelo de negocio digital para la gestión de casas de reposo, el equipo elaboró el mapa en UXPressia partiendo de un Business Goal principal que cumple los criterios SMART: “Mejorar la transparencia, eficiencia y confianza en la gestión de casas de reposo, alcanzando 500 residencias afiliadas y 10,000 familiares activos en el primer año de operación”. A partir de esta meta se incorporaron como Actors/Personas a los User Personas previamente definidos: Mauricio Sánchez (administrador de la residencia) y Carmen Morales (familiar cuidadora). Para cada uno se identificaron los Impacts esperados, es decir, cómo queremos que cambien su comportamiento para ayudar a lograr el objetivo: en el caso de Mauricio, la optimización de la gestión de residentes, personal y medicamentos, el mayor control de horarios, servicios y visitas y el cumplimiento de normas de seguridad y privacidad de datos de salud; en el caso de Carmen, el acceso en tiempo real al estado de salud e historial médico, la mayor confianza mediante comunicaciones y notificaciones y la tranquilidad por recibir recordatorios automáticos de citas y visitas.
</p>

<p>
  A partir de estos impactos se definieron los Deliverables que el negocio digital debe ofrecer para provocar dichos cambios en el comportamiento de los actores. Entre ellos se encuentran el módulo de gestión de residentes y personal (tratamientos, recetas y roles), el inventario digital de medicamentos con alertas de stock bajo, la agenda centralizada de citas y visitas, el panel de control en tiempo real, la gestión de roles y permisos, la auditoría y encriptación de datos clínicos y los reportes de cumplimiento normativo. Para la familia se definieron el portal y app familiar con dashboard simplificado, el sistema de notificaciones push, SMS y correo, el módulo de mensajería segura, el calendario con recordatorios automáticos y las alertas configurables. Finalmente, en la columna de User Stories se detallaron historias en formato “Como [persona] deseo [acción] para [beneficio]” (por ejemplo, historias para registro de residentes, gestión de medicamentos, agenda de citas, notificaciones y seguimiento del bienestar emocional), que permiten trazar la ruta desde los objetivos de negocio hasta los features concretos del producto, asegurando la alineación entre Business Goals, Impacts, Deliverables y desarrollo de la solución.
</p>

<img src="../assets/img/chapter-III/Impact_map.png" alt="Impact map 1" style="width: 90%; height: auto;">

<div style="page-break-after: always;"></div>
