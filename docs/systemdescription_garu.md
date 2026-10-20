# System Description: Registro de Contactos Ga/Ru Desarrollos

## 1. Visión General del Sistema
El sistema gestiona la recepción y almacenamiento seguro de los datos de contacto enviados voluntariamente por los interesados a través del sitio web de Ga/Ru Desarrollos. Se utiliza una arquitectura basada en un endpoint seguro y Google Sheets como base de datos y tablero de seguimiento comercial, evitando la necesidad de un CRM complejo en esta Fase 1.

## 2. Arquitectura de Integración
El flujo de datos se estructura mediante la siguiente cadena de comunicación:
`Navegador (HTML+CSS+JS) -> POST HTTPS (/api/contactos) -> Endpoint (Serverless / Apps Script) -> Google Sheets Privada`

- **Frontend:** Formulario HTML público. El JavaScript captura los datos y realiza un `fetch` (POST) al endpoint. No contiene credenciales ni lógica de base de datos directa.
- **Backend (Endpoint/Apps Script):** Recibe la petición, aplica límites de tamaño, filtra automatismos (spam), registra la fecha del servidor, asigna el estado inicial ("Pendiente") y escribe la nueva fila en Google Sheets. Solo devuelve un código de éxito (`2xx`) si la escritura fue confirmada.
- **Almacenamiento (Google Sheets):** Hoja de cálculo configurada en modo "Restringido", accesible exclusivamente por el personal autorizado de Ga/Ru.

## 3. Modelo de Datos (Esquema de la Hoja)
La estructura de la hoja de cálculo separa de forma estricta los datos capturados por el sistema de las columnas de seguimiento manual para evitar sobrescrituras:

| Campo | Origen | Descripción |
| :--- | :--- | :--- |
| `idConsulta` | Servidor | Identificador único de la consulta. |
| `fechaAlta` | Servidor | Fecha y hora de recepción registrada por el servidor. |
| `nombre`, `telefono`, `localidad`, `emailOpcional` | Usuario | Datos de contacto proporcionados voluntariamente. |
| `tipoConsulta`, `proyectoId`, `loteId`, `mensaje` | Usuario / Contexto | Contexto de la solicitud (lote y proyecto opcionales según el tipo). |
| `consentimiento`, `versionAviso` | Usuario / Frontend | Evidencia de aceptación del aviso de privacidad. |
| `estadoSeguimiento` | Manual (Ga/Ru) | Lista desplegable para gestión: Pendiente / Contactado. |
| `fechaContacto`, `notasInternas` | Manual (Ga/Ru) | Edición manual por parte de la inmobiliaria al dar respuesta. |

## 4. Reglas de Negocio y Operación
- **Exclusión de WhatsApp:** El botón "Consultar por WhatsApp" abre un chat directo con un mensaje precargado y **no** registra automáticamente un contacto en la base de datos. Solo el envío del formulario genera una fila.
- **Gestión de Estados:** Los usuarios autorizados de Ga/Ru pueden modificar el `estadoSeguimiento` desde Sheets sin utilizar un panel de administración web, garantizando que los datos originales enviados queden inalterados.
- **Resiliencia y Errores:** Si el guardado en la hoja falla, la web informa el error al usuario y no muestra el mensaje engañoso de "Consulta recibida".

## 5. Seguridad y Privacidad
- **Cumplimiento Normativo:** Adecuación a la Ley 25.326 (Argentina) con separación clara entre el consentimiento para seguimiento de la consulta y el permiso opcional para recibir promociones.
- **Prevención de Inyección de Fórmulas:** Sanitización estricta en el servidor para forzar que todos los valores ingresados por el usuario sean tratados como texto, bloqueando caracteres iniciales como `=`, `+`, `-` o `@`.
- **Protección Anti-Spam:** Implementación de rate limiting, honeypot y/o CAPTCHA en el endpoint.
- **Concurrencia:** Uso de bloqueos de concurrencia (ej. `LockService` si se usa Apps Script) para procesar correctamente envíos simultáneos y deduplicación.

## 6. Criterios de Aceptación (SDD)
- [ ] Al completar el formulario con datos válidos, se crea exactamente una fila nueva con estado "Pendiente" e IDs/Fechas generadas por el servidor.
- [ ] Ante una falla técnica en la conexión con Sheets, el frontend muestra un error explícito.
- [ ] El acceso a los registros es privado; visitantes anónimos no pueden leer los contactos ni alterar el estado.
- [ ] El sistema sanitiza las entradas maliciosas y resiste automatismos básicos (spam).
