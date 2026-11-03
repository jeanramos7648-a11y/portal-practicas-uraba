# Portal de Prácticas Profesionales — Urabá

Aplicación web responsive inspirada en la referencia visual adjunta y en el Documento Integral del Caso de Estudio #6. Incluye frontend, servidor HTTP con API REST, persistencia local en JSON y almacenamiento separado para hojas de vida PDF.

## Requisitos
- Node.js 18 o superior.
- Visual Studio Code (opcional, recomendado).
- No necesita instalar paquetes externos.

## Ejecutar
1. Descomprime el ZIP.
2. Abre la carpeta `portal-practicas-uraba` en Visual Studio Code.
3. Abre Terminal → Nueva terminal.
4. Ejecuta `npm start` (o `node server.js`).
5. Abre `http://localhost:3000` en el navegador.

## Cuentas de demostración
Todas usan la contraseña `123456`.

| Rol | Correo |
|---|---|
| Estudiante | `samuel@correo.com` |
| Empresa | `empresa@uraba.com` |
| Departamento de prácticas | `practicas@uniremington.edu.co` |

## Funciones implementadas
- Inicio público con vacantes destacadas y diseño adaptable.
- Inicio de sesión con selección de rol.
- Dashboard con indicadores.
- Búsqueda y filtros de vacantes por texto, facultad, perfil y ciudad.
- Detalle de vacante y postulación de estudiante (evita duplicados).
- Perfil editable y carga/reemplazo de hoja de vida PDF (máximo 4 MB).
- Restricción de descarga de CV según rol y postulaciones.
- Publicación de vacantes para empresa/departamento.
- Listado de postulaciones, con aceptación/rechazo por parte de la empresa y estado sincronizado en los tres roles.
- Descripción «Sobre mí» del estudiante, visible para empresas (de sus postulados) y prácticas.
- Motivo obligatorio (10 a 500 caracteres) al rechazar una postulación; lo ven estudiante, empresa y prácticas.
- Foto de perfil del estudiante (JPG/PNG/WEBP, se recorta a cuadrado).
- Perfil del candidato desplegable al pulsar su nombre en las postulaciones (empresa y prácticas), con descarga de hoja de vida.
- Chat entre empresa y departamento de prácticas.
- API REST con validaciones y respuestas de error.
- Datos persistidos en `data/db.json`; archivos PDF en `uploads/`.
- Imagen de referencia incluida en `public/assets/referencia-portal.png`.

## API principal
- `GET /api/health`
- `POST /api/login`, `POST /api/logout`, `GET /api/me`
- `GET /api/jobs`, `GET /api/jobs/:id`, `POST /api/jobs`
- `GET /api/applications`, `POST /api/applications`, `PUT /api/applications/:id` (empresa: Aceptada, o Rechazada con `reason` obligatorio)
- `GET /api/avatar`, `POST /api/avatar`, `DELETE /api/avatar`
- `PUT /api/profile`, `POST /api/cv`, `GET /api/cv`
- `GET /api/messages`, `POST /api/messages`
- `GET /api/dashboard`

## Importante sobre el alcance
Este proyecto es una aplicación demostrativa funcional para ejecución local. Los datos se guardan en JSON y las contraseñas de las cuentas de demostración son deliberadamente sencillas: antes de publicar en internet deben sustituirse por autenticación de producción, contraseñas con hash, HTTPS, base de datos real, protección CSRF/rate limiting, gestión de sesiones robusta, política de privacidad y copias de seguridad. La integración con LinkedIn no se activa automáticamente: requiere credenciales y permisos oficiales aprobados; el portal informa esta limitación y continúa funcionando sin ella.

## Reiniciar datos de demostración
Detén el servidor y elimina `data/db.json`; al volver a iniciar, el sistema lo crea de nuevo con los datos de ejemplo. Los archivos PDF de `uploads/` deben eliminarse manualmente si también quieres borrarlos.
