
## Capítulo I: Introducción
El presente proyecto tiene como finalidad el diseño, desarrollo e implementación de una solución Saas, incluyendo una aplicación web y una aplicación movil, con el objetivo de resolver problemáticas reales en contextos productivos. Esta solución se construye bajo un enfoque de ingeniería de software moderna, incorporando metodologías ágiles, diseño centrado en el usuario (Lean UX) y arquitecturas escalables orientadas a servicios.

En el contexto actual, las organizaciones enfrentan desafíos relacionados con la captura, procesamiento y análisis de datos en tiempo real, especialmente en entornos donde aún predominan procesos manuales o semi-digitalizados. Estas limitaciones generan ineficiencias operativas, retrasos en la toma de decisiones y pérdida de información relevante.

Frente a este escenario, el presente proyecto propone el desarrollo de un ecosistema digital que permita la automatización de la recolección de datos mediante dispositivos IoT, su procesamiento inteligente y su visualización a través de aplicaciones web y móviles, contribuyendo a la mejora de la eficiencia operativa y la toma de decisiones basada en datos.
### 1.1. Startup Profile
La presente sección describe el contexto general de la startup responsable del desarrollo de la solución propuesta. Se presenta una visión general de la organización, su enfoque tecnológico y propuesta de valor, así como la caracterización de los integrantes del equipo, destacando sus perfiles y roles dentro del proyecto.
#### 1.1.1. Descripción de la Startup
NovaTech es una startup tecnológica enfocada en el desarrollo de soluciones digitales basadas en modelos SaaS, integrando aplicaciones web y móviles con sistemas backend escalables. Su propuesta de valor se centra en la interoperabilidad, la accesibilidad y la adaptabilidad a distintos contextos empresariales, especialmente en sectores con baja digitalización.

El modelo de negocio de NovaTech es inherentemente escalable, permitiendo el crecimiento mediante la incorporación de nuevas instituciones sin incrementos proporcionales en los costos operativos. Esto facilita su expansión en el mercado latinoamericano, particularmente en el sector geriátrico.

En el marco de este proyecto, la startup desarrolla una solución orientada al sector salud, específicamente al monitoreo y gestión de información de pacientes en casas de reposo.

##### Misión
Desarrollar soluciones tecnológicas innovadoras que permitan a las organizaciones optimizar sus procesos mediante el uso de datos, automatización e integración de tecnologías emergentes.

##### Visión
Ser una startup referente en Latinoamérica en el desarrollo de soluciones SaaS (aplicaciones web y móviles), destacando por su innovación, escalabilidad y enfoque centrado en el usuario.

#### 1.1.2. Perfiles de integrantes del equipo
<div style="page-break-after: always;"></div>

<table border="1" width="100%">
  <tr>
    <td width="140" valign="top" align="center">
      <img src="../assets/img/chapter-I/RenzoLlerena.jpg" alt="Renzo Photo" width="120" />
    </td>
    <td valign="top">
      <strong>Renzo Miguel Llerena Delgado - (U202312399)</strong> - Ingeniería de Software<br><br>
      Tengo 19 años, soy una persona tranquila, colaborativa y adaptable. Me gusta trabajar en equipo, aportando ideas y soluciones. Cuento con conocimientos en C++ y Python y siempre busco formas de hacer las cosas de manera eficiente.
    </td>
  </tr>

  <tr>
    <td width="140" valign="top" align="center">
      <img src="../assets/img/chapter-I/juan.png" alt="" width="120" />
    </td>
    <td valign="top">
      <strong>Juan Manuel Santos Torres - (U20221A371)</strong> - Ingeniería de Software<br><br>
      Me gusta mucho buscar la manera más sencilla y rápida de resolver cualquier problema, usando herramientas digitales para que el trabajo sea menos pesado. Soy alguien que siempre está metido en nuevos proyectos y me encanta trabajar con más personas para intercambiar ideas. Tengo 21 años y trato de que todo lo que hago, ya sea en los estudios o en el trabajo, tenga un orden y un propósito claro.
    </td>
  </tr>

  <tr>
    <td width="140" valign="top" align="center">
      <img src="../assets/img/chapter-I/AdrianValProfile.jpg/" alt="" width="120" />
    </td>
    <td valign="top">
      <strong>Adrian Emanuel Valerio Garcia - (U202210334)</strong> - Ingeniería de Software<br><br>
      Me interesa el aprendizaje continuo y suelo enfocarme en resolver problemas de manera rápida y eficiente. Disfruto los videojuegos y aprender nuevas tecnologías, además de trabajar en equipo para lograr objetivos en conjunto. Tengo conocimientos en lenguajes de programación y procuro mejorar constantemente mis métodos de estudio para ampliar mis habilidades.
    </td>
  </tr>
    <tr>
    <td width="140" valign="top" align="center">
      <img src="../assets/img/chapter-I/MiguelRoman.png" alt="Miguel Photo" width="120" />
    </td>
    <td valign="top">
      <strong>Miguel Ángel Román López - (U202212897)</strong> - Ingeniería de Software<br><br>
      Poseo conocimientos en C++, programación orientada a objetos y diseño web. Mi aporte será investigación, ideas e imaginación para realizar un buen proyecto y cumplir con las entregas.
    </td>
  </tr>

  <td width="140" valign="top" align="center">
      <img src="../assets/img/chapter-I/team-member-profiles/" alt="" width="120" />
    </td>
    <td valign="top">
    </td>
  </tr>  
</table>

### 1.2. Solution Profile
Veyra es una plataforma digital integral basada en un modelo SaaS, diseñada para mejorar la gestión de información clínica y operativa en casas de reposo. Permite el acceso remoto a datos relevantes tanto para el personal asistencial como para los familiares, facilitando la transparencia y la toma de decisiones informadas.

#### 1.2.1. Antecedentes y problemática

**1. ANTECEDENTES**

La población mundial envejece rápidamente, y América Latina no es la excepción. En 2022 había unos 88,6 millones de personas de 60 años o más en la región (13,4% de la población). En Perú, este fenómeno demográfico se refleja en que actualmente el 13,9% de la población (≈4 748 000 personas) tiene 60 años o más. Esta proporción crece a un ritmo sostenido (≈2,7% anual) y se estima que para el 2050 cerca del 25% de los peruanos formará parte de la comunidad de adultos mayores Este cambio estructural incrementa la demanda de servicios geriátricos (casas de reposo, centros de día, atención domiciliaria, etc.) y plantea retos en salud, pensiones y cuidado social.

En este contexto, las casas de reposo cumplen un rol crucial en el bienestar de los mayores, pero su gestión enfrenta limitaciones tecnológicas. Tradicionalmente, ingresar a una residencia era visto como "apartar" al anciano, pero hoy se reconoce que la familia sigue teniendo un rol activo en el cuidado. Sin embargo, la modernización digital del sector es incipiente: muchas residencias aún manejan la información clínica y administrativa en papel o en sistemas aislados. De hecho, incluso en el sistema de salud peruano en general "muchos hospitales y postas aún registran a mano la información del paciente" y la compartición de datos es limitada, pues cada institución (MINSA, EsSalud, FF.AA., FFAA, sector privado) opera con historiales fragmentados. Solo unas pocas residencias pioneras habían iniciado planes de transformación digital antes de la pandemia, siendo la COVID-19 un catalizador que "agilizó la necesidad de un gran cambio" tecnológico en los centros geriátricos. Esta falta de digitalización contribuye a la desconexión informativa entre las casas de reposo y los familiares. En la práctica, la comunicación suele limitarse a llamadas telefónicas esporádicas o visitas puntuales, sin un canal permanente de intercambio de datos. Esta brecha se traduce en frustración y ansiedad: los familiares desean recibir información puntual sobre la salud, actividades y necesidades de sus seres queridos, pero carecen de medios eficientes para ello. De hecho, expertos han señalado "la necesidad de la creación de una plataforma" que aproveche las últimas tecnologías para facilitar la interacción continua entre los familiares y el centro de cuidado.

**2. PROBLEMÁTICA**

Comunicación deficiente: El personal de las residencias de adultos mayores suele tener una alta carga de trabajo, lo que limita el tiempo disponible para informar a las familias. Se ha documentado que "en muchas residencias, el personal de atención directa se encuentra bajo una presión de tiempo que dificulta tener conversaciones con los miembros de la familia". Esta situación genera malentendidos, desconfianza y estrés emocional en los parientes, que a menudo no saben a quién recurrir o deben esperar largas horas para recibir respuestas básicas.

Falta de acceso a información en tiempo real: Los familiares no disponen de un medio seguro para consultar el estado clínico o las actividades diarias del residente de manera instantánea. La carencia de un portal o aplicación web significa que no pueden verificar datos como medicación administrada, citas médicas, registro de tratamientos o estado de ánimo sin depender de consultas directas al personal. En la práctica esto implica que las familias deben realizar numerosas llamadas telefónicas o visitas recurrentes para obtener actualizaciones, lo que aumenta la carga de trabajo de los cuidadores y mantiene a los parientes en incertidumbre. (Por el contrario, el uso de herramientas digitales permitiría "acceso constante a información actualizada", reduciendo la ansiedad y las llamadas repetitivas). Datos clínicos fragmentados: Los registros sanitarios de cada residente suelen estar dispersos en historias clínicas físicas o sistemas locales no integrados. Esto provoca duplicidad de información y dificulta el seguimiento longitudinal de la salud del adulto mayor. Por ejemplo, si un centro no cuenta con un expediente único digital, las anotaciones de enfermería, el historial médico y los reportes de actividades pueden quedar desorganizados o inaccesibles desde la distancia, lo que complica la coordinación entre médicos, enfermeras y familia.

Ausencia de plataformas integradas: Actualmente, no existe en el sector una solución web centralizada que unifique la gestión clínica, administrativa y comunicacional en residencias peruanas. Muchas tareas administrativas –como el control de pagos, el registro de recetas o los reportes diarios– se realizan de forma manual o en hojas de cálculo, sin interoperabilidad. Esta falta de automatización genera lentitud en los procesos y riesgo de errores, afectando la eficiencia del personal y reduciendo la transparencia hacia los familiares.

Baja adopción tecnológica: A diferencia de otros sectores de salud, las casas de reposo en Perú han incorporado la tecnología de forma limitada. Aunque en otros países especialistas destacan que la digitalización ofrece mejoras significativas en la calidad asistencial, en nuestro entorno las iniciativas tecnológicas (como teleasistencia o software de gestión) son incipientes Esta baja adopción implica que los centros dependen de métodos tradicionales, lo que aumenta la brecha con las expectativas modernas de atención y comunicación.

**Análisis 5W+2H:**

**What (¿Qué?):** Veyra busca resolver la falta de comunicación y coordinación entre las casas de reposo y las familias de los residentes. La plataforma web integrará el registro clínico, tratamientos, recordatorios, reportes diarios y datos administrativos en un único sistema accesible, permitiendo que el personal de las instituciones gestione la información y que los familiares consulten de forma segura el estado y la historia de su adulto mayor.

**Why (¿Por qué?):** Es importante abordar este problema para mejorar la calidad de vida de los adultos mayores y dar tranquilidad a sus familias. Al centralizar la información y ofrecer acceso en línea, Veyra reduce el estrés familiar, aumenta la transparencia en la atención y optimiza las tareas del personal. En un contexto de rápido envejecimiento poblacional, la solución contribuye a que las residencias operen de manera más eficiente y moderna, alineándose con estándares actuales de cuidado y facilitando el cumplimiento de las normativas de salud.

**Who (¿Quién?):** Afecta principalmente a dos grupos: el personal técnico y administrativo de las instituciones geriátricas, que necesitan gestionar datos clínicos y operativos de forma ordenada; y los familiares de los residentes, quienes demandan información actualizada y comunicación efectiva. Veyra beneficiará asimismo a los mismos adultos mayores al garantizar un seguimiento más riguroso de su atención médica, aunque ellos no serán usuarios directos de la plataforma (la interfaz está diseñada para personal técnico y familiares).

**When (¿Cuándo?):** Esta necesidad es especialmente crítica en la actualidad, debido a que el envejecimiento de la población ya supera ciertos umbrales y seguirá aumentando en las próximas décadas. Además, situaciones cotidianas como emergencias médicas, cambios de tratamiento o eventos familiares resaltan la urgencia de tener información actualizada en tiempo real. En consecuencia, el momento más crítico es el presente y el futuro inmediato, cuando las residencias busquen modernizar sus procesos y ofrecer mejores servicios ante el aumento sostenido de adultos mayores.

**Where (¿Dónde?):** Ocurre principalmente en el ámbito de casas de reposo, residencias geriátricas y centros de atención diurna en Perú (especialmente en las zonas urbanas con más población envejecida), así como en cualquier institución similar de Latinoamérica interesada en mejorar su gestión. También implica el contexto familiar de esos residentes, quienes pueden estar localizados tanto en la misma ciudad como en regiones distantes, requiriendo acceso remoto a la información.

**How (¿Cómo?):** Se resuelve mediante el desarrollo de Veyra, una aplicación web centralizada en la nube. El personal de la residencia ingresará datos clínicos, tratamientos y reportes a través de la plataforma, que implementará seguridad y cifrado para proteger la confidencialidad. Los familiares dispondrán de un portal web seguro con acceso mediante credenciales, donde consultarán los datos relevantes en cualquier momento. En el futuro se integrarán dispositivos IoT (brazaletes, sensores biométricos) para automatizar la captura de constantes vitales y movimiento, pero esto queda fuera del alcance inicial. La plataforma facilitará notificaciones y recordatorios (por ejemplo, de medicación o citas) y podrá escalar conforme crezca el número de usuarios.

**How much (¿Cuánto?):** El modelo de ingresos proyectado es de tipo SaaS (Software como Servicio). Se planea ofrecer suscripción mensual o anual a las instituciones (casas de reposo) basada en el tamaño o número de residentes. La tarifa cubriría acceso al sistema, soporte técnico y futuras actualizaciones (por ejemplo, incorporación de IoT). Los familiares tendrían acceso incluido con la suscripción del centro, de modo que el costo recae sobre la institución. Adicionalmente, se podría considerar un esquema escalonado: un plan básico con funciones esenciales y niveles superiores con módulos avanzados (informes personalizados, integración de dispositivos, etc.), así como una tarifa de implementación inicial para configurar el sistema. Esto permitirá sostenibilidad económica de Veyra adaptada al mercado de residencias de tercera edad.

#### 1.2.2. Lean UX Process

El Lean UX es un enfoque que permite validar las soluciones propuestas para problemas identificados. Este enfoque se centra en las personas que utilizarán nuestro producto. Una vez identificada la problemática a resolver, se empleó este proceso para reconocer áreas clave que contribuirán a dar forma al producto propuesto.

##### 1.2.2.1. Lean UX Problem Statements

El estado actual del **cuidado de adultos mayores en casas de reposo** se ha enfocado principalmente en **procesos manuales y registros físicos,** lo que provoca **ineficiencias operativas, falta de transparencia, pérdida de información y riesgos en la gestión clínica y médica.** Esta situación afecta a **administradores, personal de salud y familiares de los residentes,** quienes dependen de métodos desactualizados para acceder y compartir información crítica sobre la salud de los adultos mayores.

Lo que los productos o servicios existentes no logran resolver es la centralización **digital de la gestión médica y comunicacional dentro de las casas de reposo.** Actualmente, **no existe una solución integrada que unifique el monitoreo de salud, la comunicación con familiares y el control administrativo** en una sola plataforma segura y confiable.

Nuestro producto, **Veyra**, abordará esta brecha mediante una **plataforma web segura, intuitiva y escalable que:**

- Centraliza la información médica y administrativa de los residentes.

- Facilita la comunicación directa y transparente entre las casas de reposo y los familiares.

- Ofrece reportes visuales, alertas automáticas y seguimiento en tiempo real.

Nuestro enfoque inicial estará dirigido a **los administradores de casas de reposo privadas ubicadas en zonas urbanas,** con entre **20 y 80 residentes,** que ya utilicen herramientas digitales básicas. También se orientará a **familiares y apoderados** que busquen un **seguimiento transparente y continuo** del estado de salud de sus seres queridos.

Sabremos que tenemos éxito cuando observemos **mayor transparencia y confianza entre los administradores de casas de reposo y familiares de los adultos mayores, tiempos de respuesta más rápidos ante eventos médicos, mayor participación de los usuarios en la plataforma y una reducción medible de los errores de comunicación.**

#### 1.2.2.2. Lean UX Assumptions

**Business Assumptions:**

Existe un mercado suficientemente grande de **casas de reposo privadas medianas (20 a 80 residentes)** en Perú y Latinoamérica que necesitan digitalizar sus procesos para seguir siendo competitivas.

Los **directores y administradores** están dispuestos a invertir en una plataforma SaaS como Veyra **si perciben mejoras claras en eficiencia operativa, control de la información y reputación frente a las familias**.

Las residencias pueden **asumir una suscripción mensual o anual** (por sede o por número de residentes) sin afectar de forma crítica su estructura de costos, siempre que el valor percibido sea evidente.

La **digitalización de procesos internos** (historial clínico, comunicación con familiares, reportes y cobros) genera **ahorros en tiempo y reducción de errores** que compensan el costo de implementación y operación de Veyra.

Los beneficios de **mayor transparencia hacia los familiares** se traducen en **mayor ocupación, fidelización y recomendación** de la residencia, lo que hace sostenible el modelo de negocio de Veyra.

El modelo **SaaS B2B** de Veyra es escalable a **otras ciudades y países de la región** con ajustes principalmente comerciales (precio, regulaciones), sin cambios estructurales en el producto base.

**Business Outcomes:**

Queremos que las **casas de reposo adopten Veyra como su herramienta principal de gestión**, registrando diariamente información médica, medicamentos y reportes.

Buscamos que los **familiares consulten regularmente la plataforma**, interactúen con el personal y reporten mayor confianza y satisfacción.

Esperamos reducir en un 30% **los errores en la administración de medicamentos** y mejorar en un **40% la eficiencia operativa** del personal durante los primeros seis meses.

Queremos que las **instituciones perciban un ahorro de tiempo administrativo** y una reducción en las llamadas o consultas manuales de familiares.

Aspiramos a que **nuevas casas de reposo se suscriban a planes de pago mensuales**, validando el valor percibido del producto.

Buscamos que Veyra se consolide como una **solución tecnológica de referencia** en la gestión integral del cuidado de adultos mayores.

**User Assumptions:**

Los **administradores y personal médico** necesitan herramientas que integren historiales, medicamentos, citas y reportes en un solo lugar.

Los **familiares o apoderados** requieren acceso rápido, seguro y claro a la información de salud de los residentes, sin depender de llamadas o correos.

Ambos grupos valoran **la transparencia, la inmediatez y la facilidad de uso** por encima de las funciones excesivamente técnicas.

Los **administradores** priorizan la eficiencia operativa y la reducción de errores.

Los **familiares** buscan confianza, tranquilidad y cercanía con la institución.

Existe una disposición positiva hacia las soluciones digitales siempre que sean **intuitivas, seguras y personalizables según el rol del usuario.**

**User Outcomes:**

Los **administradores** reportan una mejor organización y control del flujo de trabajo interno.

El **personal médico** disminuye el uso de registros en papel y optimiza la actualización de información clínica.

Los **familiares** se sienten más tranquilos e informados, reduciendo su necesidad de llamadas o visitas presenciales.

Las **decisiones clínicas y administrativas** se basan en datos actualizados, reduciendo errores.

Las instituciones **mejoran su comunicación y reputación** gracias a la transparencia en la atención.

Los usuarios recomiendan Veyra como una **herramienta confiable, moderna y fácil de usar.**

**Features:**

1) **Módulo de historial clínico digital** con acceso restringido por rol, que permite a administradores y cuidadores gestionar y actualizar datos en tiempo real, evitando pérdidas de información.

2) **Aplicación web para familiares** donde pueden visualizar notificaciones y reportes médicos actualizados, reduciendo la incertidumbre y aumentando la confianza en el servicio.

3) **Sistema de alertas automáticas** sobre medicamentos, citas y posibles emergencias médicas, que mejora la coordinación del cuidado y reduce el riesgo de errores.

4) **Paneles analíticos e informes descargables** que permiten a los administradores tomar decisiones basadas en datos y optimizar el uso de recursos clínicos y administrativos.

5) **Canales de comunicación interna y externa** (por ejemplo, chat o registro estructurado de comunicaciones) integrados en la plataforma, para fortalecer el vínculo entre familias y personal del hogar.

##### 1.2.2.3. Lean UX Hypothesis Statements

**Hipótesis 1 – Historial clínico digital**

Creemos que lograremos **una mejora significativa en la eficiencia operativa y reducción de errores en los registros médicos,**

si **los administradores y cuidadores**

Obtienen **la capacidad de gestionar y actualizar la información clínica de los residentes en tiempo real y de forma segura,**

Con **un módulo de historial clínico digital con acceso restringido por rol.**

**Hipótesis 2 – Notificaciones y reportes para familiares**

Creemos que lograremos **un aumento en la confianza y satisfacción de los familiares respecto al servicio de cuidado,**

Si **los familiares y apoderados de los adultos mayores**

Obtienen **visibilidad inmediata y transparente del estado de salud y atención médica de sus seres queridos,**

Con **una aplicación web que les permita visualizar notificaciones y reportes médicos actualizados.**

**Hipótesis 3 – Alertas automáticas de salud y medicación**

Creemos que lograremos **una reducción en los errores médicos y una mejor coordinación del cuidado diario,**

Si **los cuidadores y administradores de las casas de reposo**

Reciben **alertas oportunas sobre medicamentos, citas y posibles emergencias médicas,**

Con **un sistema automatizado de notificaciones y recordatorios inteligentes.**

**Hipótesis 4 – Paneles analíticos e informes descargables**

Creemos que lograremos **una toma de decisiones más informada y una gestión más eficiente de los recursos clínicos,**

si **los administradores de las casas de reposo**

Acceden a **indicadores visuales, métricas y reportes descargables sobre el estado de salud y desempeño institucional,**

Con **paneles analíticos avanzados e informes generados por la plataforma.**

**Hipótesis 5 – Canales de comunicación integrados**

Creemos que lograremos **un fortalecimiento del vínculo emocional y la confianza entre familiares y cuidadores,**

Si **las familias y el personal de las casas de reposo**

Pueden **comunicarse de forma directa, rápida y segura sobre el estado del residente,**

Con **la integración de canales de comunicación interna y externa como chat o llamadas dentro de Veyra.**

##### 1.2.2.4. Lean UX Canvas

![Lean UX Canvas](../assets/img/chapter-I/lean-ux.png)

### 1.3. Segmentos objetivos

Esta sección incluye la descripción de los segmentos asociados al dominio del problema, incluyendo características demográficas e información estadística de sustento.

#### Segmento Objetivo 1: Administradores o directores de casas de reposo 

Características demográficas:

Edad: Entre 35 y 65 años.

Género: Indistinto.

Ocupación: Administradores, directores o gerentes de casas de reposo privadas o centros geriátricos.

Nivel educativo: Profesionales con grado universitario en administración, enfermería, gerontología o afines.

Ubicación geográfica: Principalmente áreas urbanas del Perú.

Información estadística de sustento:

Según la Superintendencia Nacional de Salud (SUSALUD) (2023), existen ≈320 casas de reposo registradas en Perú, con un crecimiento del 12% anual debido al envejecimiento poblacional.

El INEI reporta que el 13.1% de la población peruana son adultos mayores (≥60 años), y se proyecta que alcance el 20% para 2050. Esto incrementa la demanda de servicios geriátricos formales.

Un estudio de la Cámara de Comercio de Lima (2022) indica que el 75% de estas residencias utiliza métodos manuales (papel o Excel) para gestionar información, lo que genera ineficiencias y errores.

#### Segmento Objetivo 2: Familiares de adultos mayores 

Características demográficas:

Edad: Entre 35 y 65 años (hijos o cuidadores principales de adultos mayores).

Género: Mayormente, mujeres (70%), quienes asumen roles de cuidado en Perú (INEI, 2023).

Ocupación: Profesionales, trabajadores independientes o empleados con tiempo limitado.

Nivel socioeconómico: Medio y medio-alto, con capacidad de pago para residencias privadas.

Ubicación geográfica: Zonas urbanas de Perú, especialmente Lima Metropolitana (50%) y capitales regionales.

Información estadística de sustento:

El INEI reporta que el 30% de adultos mayores peruanos vive en hogares multigeneracionales, pero la migración laboral y la urbanización han aumentado la demanda de residencias geriátricas.

Un estudio de APESEG (2023) muestra que el 65% de familiares percibe desconfianza en la calidad del cuidado en residencias, debido a la falta de transparencia en la comunicación.

El Banco Interamericano de Desarrollo (BID) destaca que el 85% de peruanos usa smartphones, lo que facilita la adopción de soluciones digitales para monitoreo remoto.
