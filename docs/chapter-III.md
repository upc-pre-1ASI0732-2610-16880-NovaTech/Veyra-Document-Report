## 3.1. User Stories. 
<p>Para la especificación de requisitos de los usuarios, se desarrollaron las historias de usuario que describen cada requisito y funcionalidad que debe estar implementado en el desarrollo del producto final para satisfacer las necesidades del público objetivo. A continuación se presentan las historias de usuario relacionadas con la plataforma "Veyra". Esta sección reúne historias de usuario centradas en la experiencia de los distintos roles: el visitante, el familiar del adulto mayor y el administrador de la casa de reposo. Aquí se definen las necesidades clave para cada uno, desde la navegación inicial y contacto, hasta la gestión detallada de residentes, personal y medicamentos.</p>

<table>
        <thead>
            <tr>
                <th>Story ID</th>
                <th>Título</th>
                <th>Descripción</th>
                <th>Criterios de Aceptación (Gherkin)</th>
            </tr>
        </thead>
        <tbody>
                <tr>
                <td>EP01</td>
                <td>Navegación en la Landing Page</td>
                <td>Como visitante quiero tener una experiencia fluida y completa en el sitio web para conocer los servicios y tomar decisiones informadas.</td>
                <td></td>
            </tr>
            <tr>
            <tr>
                <td>US01</td>
                <td>Menú de navegación</td>
                <td>Como visitante de la Landing Page, quiero poder acceder a un menú de navegación en la parte superior de la página, para explorar fácilmente las secciones como "Login", "Sign up", "Planes", "Contacto",etc.</td>
                <td>
                    <strong>Escenario 1: Navegación exitosa a través del menú</strong><br>
                    <strong>Dado que</strong> el visitante está en la landing page<br>
                    <strong>Cuando</strong> el menú de navegación está disponible<br>
                    <strong>Entonces</strong> el usuario puede ver los enlaces principales y navegar a las secciones correspondientes.<br><br>
                    <strong>Escenario 2: Menú no disponible</strong><br>
                    <strong>Dado que</strong> el visitante está en la landing page<br>
                    <strong>Cuando</strong> el menú de navegación no se carga correctamente<br>
                    <strong>Entonces</strong> el usuario recibe un mensaje de error y tiene opciones alternativas de navegación.
                </td>
            </tr>
            <tr>
              <td>US02</td>
                <td>Visualización de Planes</td>
                <td>Como visitante de la Landing Page, quiero ver los planes de suscripción junto a su precio y características, para poder elegir el que mejor se adapte a mis necesidades.</td>
                <td>
                    <strong>Escenario 1: Visualización de planes disponibles</strong><br>
                    <strong>Dado que</strong> el visitante navega a la sección de planes<br>
                    <strong>Cuando</strong> los planes están disponibles en el sistema<br>
                    <strong>Entonces</strong> el usuario puede ver la lista de planes con sus precios y características para compararlos.<br><br>
                    <strong>Escenario 2: Planes no disponibles</strong><br>
                    <strong>Dado que</strong> el visitante navega a la sección de planes<br>
                    <strong>Cuando</strong> no hay planes disponibles o ocurre un error de carga<br>
                    <strong>Entonces</strong> el usuario recibe un mensaje informativo sobre la indisponibilidad.
                </td>
            </tr>
            <tr>
                <td>US03</td>
                <td>Selección de Plan en Landing Page</td>
                <td>Como visitante de la landing page, quiero seleccionar un plan y finalizar la confirmación en la misma pantalla, para agilizar y simplificar el registro.</td>
                <td>
                    <strong>Escenario 1: Selección exitosa de plan</strong><br>
                    <strong>Dado que</strong> el visitante ha seleccionado un plan disponible<br>
                    <strong>Cuando</strong> confirma la selección<br>
                    <strong>Entonces</strong> el sistema muestra el formulario de registro con el plan pre-seleccionado.<br><br>
                    <strong>Escenario 2: Datos de registro incompletos</strong><br>
                    <strong>Dado que</strong> el visitante está completando el formulario de registro<br>
                    <strong>Cuando</strong> faltan datos obligatorios<br>
                    <strong>Entonces</strong> el sistema muestra mensajes de validación específicos para los campos requeridos.
                </td>
            </tr>
            <tr>
                <td>US04</td>
                <td>Visualización de creadores</td>
                <td>Como visitante de la Landing Page, quiero ver a los creadores de la aplicación, para conocer al equipo detrás del producto y generar confianza en el servicio.</td>
                <td>
                    <strong>Escenario 1: Acceso a información del equipo</strong><br>
                    <strong>Dado que</strong> el visitante navega a la sección "Equipo"<br>
                    <strong>Cuando</strong> la información del equipo está disponible<br>
                    <strong>Entonces</strong> el usuario puede ver los detalles de los creadores incluyendo nombres, roles e información de contacto.<br><br>
                    <strong>Escenario 2: Información del equipo no disponible</strong><br>
                    <strong>Dado que</strong> el visitante navega a la sección "Equipo"<br>
                    <strong>Cuando</strong> la información no está disponible<br>
                    <strong>Entonces</strong> el usuario recibe un mensaje informativo sobre la indisponibilidad temporal.
                </td>
            </tr>
            <tr>
                <td>US07</td>
                <td>Cambio de idioma</td>
                <td>Como visitante de la Landing Page quiero en el menú un botón para cambiar de idioma entre español e inglés para entender mejor de que trata Veyra.</td>
                <td>
                    <strong>Escenario 1: Cambio exitoso de idioma</strong><br>
                    <strong>Dado que</strong> el visitante selecciona un idioma disponible<br>
                    <strong>Cuando</strong> confirma el cambio de idioma<br>
                    <strong>Entonces</strong> la interfaz se actualiza al idioma seleccionado y mantiene la preferencia.<br><br>
                    <strong>Escenario 2: Idioma no disponible</strong><br>
                    <strong>Dado que</strong> el visitante intenta cambiar a un idioma<br>
                    <strong>Cuando</strong> el idioma seleccionado no está disponible<br>
                    <strong>Entonces</strong> el sistema mantiene el idioma actual y muestra un mensaje informativo.
                </td>
            </tr>
            <tr>
                <td>US39</td>
                <td>Términos y condiciones</td>
                <td>Como visitante de la landing page quiero poder acceder a los términos y condiciones de uso para conocer las políticas legales antes de contratar los servicios.</td>
                <td>
                    <strong>Escenario 1: Acceso a términos y condiciones</strong><br>
                    <strong>Dado que</strong> el visitante solicita ver los términos y condiciones<br>
                    <strong>Cuando</strong> el documento está disponible<br>
                    <strong>Entonces</strong> el usuario puede acceder al documento completo y actualizado.<br><br>
                    <strong>Escenario 2: Términos actualizados requieren aceptación</strong><br>
                    <strong>Dado que</strong> existen términos y condiciones actualizados<br>
                    <strong>Cuando</strong> un usuario existente accede al sistema<br>
                    <strong>Entonces</strong> el sistema requiere la revisión y aceptación de los nuevos términos antes de continuar.
                </td>
            </tr>
           <tr>
                   <td>EP02</td>
                <td>Soporte y contacto</td>
                <td>Como visitante de la Landing Page, quiero poder contactar a Veyra fácilmente, para resolver dudas o interactuar.</td>
                <td></td>
            </tr>
            <tr>
                <td>US05</td>
                <td>Redes sociales</td>
                <td>Como visitante de la landing page quiero poder acceder fácilmente a sus redes sociales de Veyra para conocer más sobre la empresa y tener canales adicionales de contacto.</td>
                <td>
                    <strong>Escenario 1: Acceso a redes sociales</strong><br>
                    <strong>Dado que</strong> el visitante busca los enlaces de redes sociales<br>
                    <strong>Cuando</strong> los enlaces están disponibles<br>
                    <strong>Entonces</strong> el usuario puede acceder a las páginas oficiales de las redes sociales.<br><br>
                    <strong>Escenario 2: Enlaces no funcionales</strong><br>
                    <strong>Dado que</strong> el visitante intenta acceder a una red social<br>
                    <strong>Cuando</strong> el enlace no está funcionando<br>
                    <strong>Entonces</strong> el usuario recibe un mensaje informativo sobre el problema.
                </td>
            </tr>
            <tr>
                <td>US06</td>
                <td>Formulario de contacto</td>
                <td>Como visitante de la landing page quiero completar un formulario de contacto para enviar consultas específicas y recibir una respuesta personalizada de Veyra.</td>
                <td>
                    <strong>Escenario 1: Envío exitoso de consulta</strong><br>
                    <strong>Dado que</strong> el visitante completa el formulario de contacto<br>
                    <strong>Cuando</strong> todos los campos requeridos están completos y válidos<br>
                    <strong>Entonces</strong> la consulta se envía exitosamente y el usuario recibe confirmación.<br><br>
                    <strong>Escenario 2: Datos de contacto inválidos</strong><br>
                    <strong>Dado que</strong> el visitante completa el formulario de contacto<br>
                    <strong>Cuando</strong> existen campos inválidos o incompletos<br>
                    <strong>Entonces</strong> el sistema muestra mensajes de validación específicos para los campos problemáticos.
                </td>
            </tr>
        </tbody>
          <tr>
                <td>EP03</td>
                <td>Acceso a Información</td>
                <td>Como familiar del adulto mayor quiero poder tener acceso a toda la información de mi familiar para estar informado de su estado.</td>
                <td></td>
            </tr>
            <tr>
                <td>US08</td>
                <td>Historial médico</td>
                <td>Como familiar de un adulto mayor quiero acceder al historial médico completo de mi familiar para conocer su evolución de salud y diagnósticos actuales.</td>
                <td>
                    <strong>Escenario 1: Acceso al historial médico</strong><br>
                    <strong>Dado que</strong> el familiar está autenticado y tiene permisos<br>
                    <strong>Cuando</strong> solicita ver el historial médico<br>
                    <strong>Entonces</strong> el sistema muestra el historial médico completo organizado cronológicamente.<br><br>
                    <strong>Escenario 2: Sin permisos para acceder al historial</strong><br>
                    <strong>Dado que</strong> el usuario intenta acceder al historial médico<br>
                    <strong>Cuando</strong> no tiene los permisos necesarios<br>
                    <strong>Entonces</strong> el sistema muestra un mensaje de restricción de acceso.
                </td>
            </tr>
            <tr>
                <td>US09</td>
                <td>Agenda de citas Medicas</td>
                <td>Como familiar de un adulto mayor quiero consultar la agenda de citas médicas de mi familiar para estar informado sobre sus próximos tratamientos.</td>
                <td>
                    <strong>Escenario 1: Visualización de citas programadas</strong><br>
                    <strong>Dado que</strong> el familiar está autenticado<br>
                    <strong>Cuando</strong> accede a la agenda de citas<br>
                    <strong>Entonces</strong> el sistema muestra la lista de citas médicas programadas con sus detalles.<br><br>
                    <strong>Escenario 2: No hay citas programadas</strong><br>
                    <strong>Dado que</strong> el familiar consulta la agenda de citas<br>
                    <strong>Cuando</strong> no existen citas programadas<br>
                    <strong>Entonces</strong> el sistema muestra un mensaje informativo sobre la ausencia de citas.
                </td>
            </tr>
            <tr>
                <td>US10</td>
                <td>Consulta de información personal</td>
                <td>Como familiar de un adulto mayor quiero ver la información de mi familiar para estar seguro de que esté correcto o actualizado.</td>
                <td>
                    <strong>Escenario 1: Visualización de información personal</strong><br>
                    <strong>Dado que</strong> el familiar está autenticado<br>
                    <strong>Cuando</strong> accede al perfil de información personal<br>
                    <strong>Entonces</strong> el sistema muestra la información personal actualizada del adulto mayor.<br><br>
                    <strong>Escenario 2: Solicitud de actualización de información</strong><br>
                    <strong>Dado que</strong> el familiar identifica información desactualizada<br>
                    <strong>Cuando</strong> solicita una actualización<br>
                    <strong>Entonces</strong> el sistema registra la solicitud de cambio con la justificación proporcionada.
                </td>
            </tr>
            <tr>
## 3.2. Product Backlog. 
## 3.3. Impact Mapping. 
