# Aplicación Node.js + Express con Gestión de Cookies

Este proyecto es una aplicación Node.js utilizando Express que implementa la creación y lectura de cookies para acceder a contenido oculto. La autenticación se realiza a través del endpoint `/login` y la validación de cookies permite el acceso al endpoint `/contenido-oculto`.

## Requisitos

- Node.js
- Express
- dotenv
- cookie-parser
- Thunder Client (extensión de Visual Studio Code)

## Instalación

1. Clona el repositorio:

```bash
git clone <URL_DEL_REPOSITORIO>
```

2. Navega al directorio del proyecto:

```bash
cd <NOMBRE_DEL_PROYECTO>
```

3. Instala las dependencias:

```bash
npm install
```

4. Crea un archivo `.env` en la raíz del proyecto y define el puerto:

```env
PORT=3000
```

5. Inicia la aplicación:

```bash
npm start
```

## Endpoints

### GET /

Endpoint de bienvenida. Proporciona instrucciones iniciales para el usuario.

**Ruta**: `/`

**Respuesta**:
```html
<p>Si ingresas por primera vez, dirígete a <strong>'/login'</strong> e identifícate.</p>
```

### POST /login

Autentica al usuario y crea una cookie `cookieLogin` si las credenciales son válidas.

**Ruta**: `/login`

**Parámetros del cuerpo**:
```json
{
  "email": "user@example.com",
  "password": "password123"
}
```

**Respuesta exitosa**:
```json
{
  "mensaje": "Bienvenid@ NombreDelUsuario"
}
```

**Respuesta de error**:
```json
{
  "error": "Usuario no autorizado. Valide sus credenciales."
}
```

### GET /contenido-oculto

Verifica la existencia de la cookie `cookieLogin` y, si es válida, muestra el contenido oculto.

**Ruta**: `/contenido-oculto`

**Respuesta exitosa**:
```html
<!-- Contenido HTML oculto -->
```

**Respuesta de error**:
```json
{
  "error": "Usuario no autorizado. Valide sus credenciales."
}
```

### GET /eliminarcookie

Elimina la cookie `cookieLogin`.

**Ruta**: `/eliminarcookie`

**Respuesta**:
```html
Cookie eliminada.
```
