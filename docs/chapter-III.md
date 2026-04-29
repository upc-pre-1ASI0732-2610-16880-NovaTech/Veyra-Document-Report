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
## 3.2. Product Backlog. 
## 3.3. Impact Mapping. 
