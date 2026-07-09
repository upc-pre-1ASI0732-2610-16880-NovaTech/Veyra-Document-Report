# Matriz de Evaluación Ética y de Impacto

La siguiente matriz consolida los juicios informados del equipo Veyra sobre las decisiones de ingeniería de software adoptadas a lo largo del ciclo de vida del proyecto, considerando su impacto ético, profesional, social, ambiental, económico y global, en cumplimiento del **ABET - EAC - Student Outcome 4**. Cada fila sintetiza una decisión concreta tomada durante el desarrollo (vinculada a las US/TS y capítulos correspondientes), el dilema o riesgo que la motivó, y la conclusión razonada del equipo sobre su impacto.

<table>
  <thead>
    <tr>
      <th align="left">Dimensión</th>
      <th align="left">Dilema / Riesgo Identificado</th>
      <th align="left">Decisión de Ingeniería Adoptada</th>
      <th align="left">Juicio Informado (Impacto)</th>
      <th align="left">Evidencia (US/TS - Capítulo)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="left"><strong>Ética y Responsabilidad Profesional</strong></td>
      <td align="left">Veyra almacena información médica sensible de adultos mayores (diagnósticos, medicación, contactos de emergencia), un grupo considerado vulnerable, por lo que un manejo negligente de estos datos constituye una falta ética y profesional grave.</td>
      <td align="left">Se implementó cifrado de datos en reposo (<strong>US38</strong>) y autenticación multifactor (<strong>TS18</strong>) para restringir el acceso a expedientes clínicos únicamente a personal autorizado.</td>
      <td align="left">El equipo concluye que la responsabilidad profesional del ingeniero de software no termina en la funcionalidad, sino que exige anticipar el uso indebido de datos sensibles; priorizar seguridad sobre velocidad de entrega fue una decisión ética deliberada, no una obligación regulatoria externa.</td>
      <td align="left">US38, TS18 - Cap. VI y VIII (8.3.3.3)</td>
    </tr>
    <tr>
      <td align="left"><strong>Ética y Responsabilidad Profesional</strong></td>
      <td align="left">Un manejo de errores poco claro durante el registro de medicamentos (<strong>US14</strong>) puede inducir a un cuidador a asumir que una toma fue registrada cuando en realidad falló, generando un riesgo directo para la salud del residente.</td>
      <td align="left">Se diseñó un manejo de errores comprensible (<strong>US44</strong>) que informa explícitamente al usuario cuándo una acción no se completó y ofrece una vía clara de reintento.</td>
      <td align="left">Se concluye que la transparencia del sistema ante sus propios fallos es una obligación ética cuando la información gestionada tiene consecuencias sobre la salud de terceros, no solo un criterio de usabilidad.</td>
      <td align="left">US44, US14 - Cap. VIII (8.1, 8.3.4)</td>
    </tr>
    <tr>
      <td align="left"><strong>Impacto Social</strong></td>
      <td align="left">Las familias de residentes suelen enfrentar ansiedad e incertidumbre sobre el estado de sus adultos mayores, y el personal asistencial de casas de reposo pequeñas suele estar sobrecargado con procesos manuales.</td>
      <td align="left">Se priorizó el Dashboard de Estadísticas (<strong>TS-ST001</strong>) y el portal de notificaciones para familiares, validados en las entrevistas de la sección 8.3.4 como mejoras que reducen la carga operativa y la incertidumbre.</td>
      <td align="left">El equipo juzga que la solución tiene un impacto social positivo al reducir la fricción entre cuidadores, familiares y residentes, aunque reconoce que su alcance actual depende de que las instituciones cuenten con conectividad y equipos digitales, lo que limita su adopción en zonas con menor infraestructura.</td>
      <td align="left">TS-ST001, US02 - Cap. VIII (8.3.3.3, 8.4.1)</td>
    </tr>
    <tr>
      <td align="left"><strong>Impacto Económico</strong></td>
      <td align="left">Muchas casas de reposo en el segmento objetivo son pequeñas o medianas empresas con presupuestos limitados para tecnología, por lo que una solución costosa o de integración compleja podría excluirlas del mercado.</td>
      <td align="left">Se optó por una arquitectura desplegada sobre servicios administrados (Firebase Hosting / Cloud Run) y un modelo de onboarding ágil (<strong>TS-NH001</strong>) con integración de pagos (<strong>TS17</strong>) que evita infraestructura propia costosa.</td>
      <td align="left">Se concluye que las decisiones de arquitectura tienen un efecto económico directo sobre la viabilidad del negocio y su accesibilidad para instituciones con menos recursos, por lo que minimizar el costo operativo fue tratado como un criterio de diseño, no solo una preferencia técnica.</td>
      <td align="left">TS-NH001, TS17 - Cap. VIII (8.3.3.1)</td>
    </tr>
    <tr>
      <td align="left"><strong>Impacto Ambiental</strong></td>
      <td align="left">La gestión tradicional de historiales médicos y de inventario de medicamentos en casas de reposo suele depender de registros físicos en papel, con el consecuente consumo de recursos e ineficiencia en su conservación.</td>
      <td align="left">La digitalización del expediente del residente (<strong>TS-RM002</strong>), el inventario de medicamentos (<strong>TS-I002</strong>) y los registros de personal (<strong>TS-EM001</strong>) elimina la dependencia de archivos físicos para estos procesos.</td>
      <td align="left">El equipo reconoce que, si bien el impacto ambiental no fue un objetivo primario del proyecto, la digitalización de procesos administrativos es una consecuencia positiva medible en la reducción de consumo de papel e insumos físicos en las instituciones adoptantes.</td>
      <td align="left">TS-RM002, TS-I002, TS-EM001 - Cap. VIII (8.3.1)</td>
    </tr>
    <tr>
      <td align="left"><strong>Impacto Global</strong></td>
      <td align="left">El cuidado de adultos mayores y la normativa de protección de datos de salud varían entre países y regiones, por lo que una solución diseñada únicamente para el contexto local podría no ser extensible ni responsable fuera de él.</td>
      <td align="left">Se adoptaron prácticas alineadas a estándares reconocidos internacionalmente (cifrado de datos en reposo, autenticación multifactor, arquitectura basada en DDD) en lugar de soluciones ad-hoc específicas de un solo mercado.</td>
      <td align="left">Se concluye que diseñar sobre estándares de seguridad y calidad reconocidos globalmente (en vez de mínimos locales) prepara a Veyra para escalar de forma responsable a otros mercados, aunque el equipo identifica como pendiente validar el cumplimiento normativo específico de cada país antes de una expansión real.</td>
      <td align="left">US38, TS18 - Cap. V y VIII</td>
    </tr>
  </tbody>
</table>

## Síntesis del Juicio Ético Final

El equipo concluye que las decisiones de ingeniería adoptadas durante el desarrollo de Veyra no se limitaron a criterios técnicos o de negocio, sino que integraron de forma consciente la responsabilidad ética y profesional exigida por el **ABET - EAC - Student Outcome 4**. En particular, se priorizó la protección de un grupo vulnerable (adultos mayores) por encima de la velocidad de entrega, se favoreció la transparencia del sistema ante sus propios errores, y se buscó un equilibrio entre la sostenibilidad económica de las instituciones clientes y la calidad de la solución entregada. El equipo reconoce, no obstante, que persisten oportunidades de mejora en la validación normativa internacional y en la evaluación de accesibilidad tecnológica para instituciones con menor infraestructura digital, aspectos que quedan documentados como recomendaciones para una siguiente iteración del producto.