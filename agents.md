
# AGENTS.md — Ga/Ru Desarrollos

## 1. Descripción del proyecto

Ga/Ru Desarrollos es un sitio web comercial para una empresa desarrolladora de loteos ubicada en Tupungato, Mendoza, Argentina.

Su objetivo es presentar los desarrollos inmobiliarios, mostrar información y disponibilidad de parcelas, comunicar avances de obra y facilitar consultas de potenciales compradores.

El sitio contará con cuatro vistas, cuya estructura y contenido se definirán en las especificaciones correspondientes.

El proyecto es desarrollado por GEPI Software utilizando la metodología **Spec-Driven Development (SDD)**.

Todos los agentes deben respetar los principios de `docs/constitution.md`.

## 2. Tecnologías del proyecto

### Stack aprobado

- **Frontend:** React + Vite.
- **Enrutamiento:** React Router.
- **Estilos:** CSS tradicional, modular y mantenible.
- **Gestor de paquetes:** npm.
- **Hosting y despliegue:** Cloudflare.
- **Integración de formularios:** Google Apps Script.
- **Almacenamiento de contactos:** Google Sheets privado.

### Restricciones tecnológicas

- Tailwind CSS podrá incorporarse únicamente si existe una justificación técnica y autorización del equipo.
- No agregar frameworks, dependencias, servicios ni herramientas adicionales sin justificar su necesidad.
- No implementar autenticación, paneles administrativos ni funcionalidades fuera del alcance aprobado.
- Los detalles de arquitectura e integración deberán definirse en los planes técnicos correspondientes.
- No exponer credenciales, claves privadas ni información sensible en el frontend.

## 3. Documentación y fuentes de verdad

Los documentos aprobados del repositorio constituyen la fuente de verdad técnica y funcional.

Jerarquía documental:

1. `docs/constitution.md` — Principios inquebrantables.
2. SRS aprobada — Alcance y requisitos generales del sistema.
3. `spec.md` — Especificación de una funcionalidad.
4. `plan.md` — Plan técnico aprobado.
5. `tasks.md` — Tareas de implementación autorizadas.

Notion se utiliza para organizar el proyecto, registrar decisiones y conservar materiales de referencia.

Las propuestas de Notion no reemplazan automáticamente las especificaciones aprobadas del repositorio.

El archivo `docs/systemdescription_garu.md` es un ejemplo no validado y NO debe utilizarse como fuente oficial de requisitos ni de arquitectura.

Ante contradicciones entre documentos, detenerse y solicitar aclaración.

## 4. Metodología obligatoria — SDD

El proceso de desarrollo es:

**Constitución → Spec → Clarificación → Plan → Tasks → Implementación → Validación.**

### Especificación

- Definir el QUÉ y el POR QUÉ antes de implementar.
- Utilizar requisitos funcionales numerados (RF).
- Redactar criterios de aceptación verificables, preferentemente mediante notación EARS.
- Documentar casos límite, errores esperados y funcionalidades fuera de alcance.
- No inventar requisitos ni completar información comercial no confirmada.

### Clarificación

- Detectar ambigüedades, contradicciones y requisitos incompletos.
- Resolver las decisiones que afecten la implementación antes de planificar.
- No asumir respuestas ante decisiones importantes pendientes.

### Planificación

- Definir el CÓMO a partir de la especificación aprobada.
- Identificar módulos, responsabilidades, estructuras de datos e integraciones necesarias.
- Justificar decisiones técnicas y alternativas descartadas.
- Mantener trazabilidad entre el plan y los requisitos funcionales.

### Tareas

- Dividir el plan en tareas pequeñas y verificables.
- Cada tarea debe indicar qué requisitos cubre.
- Cada tarea debe tener criterios de finalización claros.
- Respetar dependencias y prioridades aprobadas.

### Implementación

- Implementar únicamente la tarea autorizada.
- No realizar modificaciones fuera del alcance de esa tarea.
- Mantener consistencia con la Constitución, la especificación y el plan.
- No comenzar automáticamente la siguiente tarea.

### Validación

- Comprobar los criterios de aceptación de cada tarea.
- Ejecutar las pruebas correspondientes.
- Registrar errores, limitaciones y resultados.
- No declarar una tarea verificada sin evidencia.

Ante cambios funcionales, actualizar primero la especificación aprobada y luego los artefactos técnicos afectados, con autorización del equipo.

## 5. Convenciones de código

### Idioma

- **Código e identificadores propios del proyecto en español.**
- Variables y funciones con nombres descriptivos en español.
- Componentes React con nombres descriptivos en español.
- Comentarios y documentación técnica en español.
- Contenido visible de la interfaz en español.

Las palabras reservadas, APIs, propiedades y convenciones propias de JavaScript, React, Vite o librerías externas conservan sus nombres originales.

### Organización

- Aplicar separación de responsabilidades.
- Mantener independientes componentes visuales, lógica de negocio, datos e integraciones.
- Evitar código duplicado y dependencias innecesarias.
- Priorizar funciones y componentes pequeños y comprensibles.
- No introducir abstracciones complejas sin una necesidad concreta.
- Respetar las decisiones arquitectónicas aprobadas en el plan.

### CSS

- Utilizar CSS organizado por componentes o responsabilidades.
- Mantener nombres de clases claros y consistentes.
- Evitar estilos duplicados y reglas de especificidad innecesariamente alta.
- No resolver errores visuales mediante modificaciones aleatorias.
- Diagnosticar primero cascada, especificidad, herencia, estados y media queries.
- Garantizar adaptabilidad a distintos tamaños de pantalla.

## 6. Diseño, marketing y experiencia de usuario

Toda implementación visual debe respetar la Constitución.

El agente debe aplicar criterios profesionales de:

- Marketing inmobiliario y conversión.
- Diseño UX/UI.
- Jerarquía visual y claridad comercial.
- Diseño responsive.
- Accesibilidad.
- SEO técnico.
- Rendimiento web.

**Referencia visual y comercial principal:** https://www.portlandterra.com.ar/

Portland Terra es una referencia de calidad y experiencia comercial, no una plantilla para copiar.

El diseño debe mantener una identidad propia para Ga/Ru.

Cada sección debe contribuir a informar, generar confianza o facilitar una consulta comercial.

No inventar características de los loteos, precios, superficies, servicios ni datos institucionales.

No modificar diseños aprobados sin autorización.

## 7. Seguridad y protección de datos

- Considerar no confiables los datos ingresados por los visitantes.
- Validar los datos de formularios del lado del servidor.
- Proteger credenciales y limitar el acceso a datos personales.
- Aplicar medidas razonables contra spam y abuso.
- No almacenar contactos por el simple hecho de abrir WhatsApp.
- Registrar únicamente consultas enviadas voluntariamente mediante el formulario.
- Confirmar el almacenamiento antes de informar al visitante que su consulta fue recibida.
- No utilizar datos reales del cliente para pruebas sin autorización.

Las decisiones específicas de seguridad e integración deben documentarse en el plan técnico correspondiente.

## 8. Comandos de desarrollo

Gestor de paquetes aprobado: npm.

### Comandos previstos

- Instalar dependencias: `npm install`
- Iniciar entorno de desarrollo: `npm run dev`
- Generar versión de producción: `npm run build`
- Previsualizar producción: `npm run preview`

### Calidad

- Lint: `npm run lint`, cuando esté configurado.
- Tests automatizados: pendientes de definir en el plan técnico.

Antes de ejecutar comandos, verificar su existencia en `package.json` y en la configuración real del proyecto.

No inventar resultados de pruebas ni afirmar que un comando se ejecutó si no existe evidencia.

## 9. Restricciones de actuación del agente

El equipo humano conserva la autoridad sobre las decisiones del proyecto.

El agente NO podrá, sin autorización explícita:

- Modificar requisitos o especificaciones aprobadas.
- Cambiar la Constitución.
- Alterar decisiones arquitectónicas importantes.
- Incorporar nuevas tecnologías o dependencias relevantes.
- Implementar funcionalidades fuera del alcance autorizado.
- Modificar datos reales del cliente.
- Realizar commits, push, merges o despliegues.
- Avanzar automáticamente a otra tarea.

Si una decisión importante está pendiente, formular una pregunta concreta y esperar respuesta.

La autorización de una tarea permite resolver sus detalles normales de implementación, pero no ampliar su alcance.

## 10. Finalización de tareas

Al terminar una tarea, el agente deberá:

1. Informar qué tarea implementó.
2. Indicar qué requisitos funcionales cubre.
3. Enumerar los archivos modificados.
4. Explicar brevemente las decisiones técnicas relevantes.
5. Ejecutar las verificaciones disponibles.
6. Informar resultados, errores y pruebas pendientes.
7. Proponer el cierre de la tarea cuando cumpla sus criterios de aceptación.
8. Detenerse y esperar autorización para continuar.

No marcar tareas como completadas sin cumplir sus criterios de aceptación.

**IMPLEMENTADO, VERIFICADO y APROBADO son estados diferentes.**

La revisión y aceptación final corresponden al equipo humano.
