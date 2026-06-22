# La Once — Agenda de Shows

Sitio oficial de **La Once**, banda uruguaya de cumbia. Servido con GitHub Pages en [la-once.com](https://la-once.com).

## Backoffice

El sitio incluye un panel de administración muy básico para modificar fechas, teléfono, textos y otros datos sin tener que editar código.

### Acceder

Andá a: `https://la-once.com/morosho`

- **Usuario:** no requiere.
- **Contraseña por defecto:** `morosho`.

### Cambiar la contraseña

Como GitHub Pages es 100% estático, la contraseña se valida con JavaScript en el navegador. Para cambiarla:

1. Abrí `morosho/index.html`.
2. Buscá la constante `ADMIN_PASSWORD_HASH`.
3. Reemplazá el hash por el SHA-256 de tu nueva contraseña. Podés generarlo con este snippet en la consola del navegador:

```js
crypto.subtle.digest('SHA-256', new TextEncoder().encode('tu-nueva-pass'))
  .then(b => console.log(Array.from(new Uint8Array(b)).map(x => x.toString(16).padStart(2, '0')).join('')))
```

> ⚠️ **Seguridad:** al ser un sitio estático, la contraseña (o su hash) está visible en el código fuente. Esto detiene a usuarios comunes, pero no a alguien con conocimientos técnicos. Si necesitás autenticación real, hace falta migrar a un hosting con backend (Netlify, Vercel, etc.).

### Guardar cambios en el sitio

El backoffice puede guardar directamente en GitHub usando un *Personal Access Token*:

1. Andá a GitHub → Settings → Developer settings → Personal access tokens.
2. Generá un token con permiso de escritura sobre el repositorio `astorlucas/la-once`.
   - Token clásico: marcá el scope `repo`.
   - Fine-grained: dale acceso de lectura/escritura a `Contents`.
3. En el backoffice, pegá el token en el campo inferior y hacé clic en **Guardar en GitHub**.
4. En unos segundos los cambios se verán reflejados en la web.

Si preferís no usar un token, podés usar **Descargar JSON** y subir manualmente el archivo `data.json` a la raíz del repositorio.

### Qué se puede editar

- Teléfono de contrataciones.
- Usuario de YouTube.
- Año y subtítulo de la agenda.
- Frases del hero.
- Fechas de las columnas laterales.
- Agenda completa de shows.
- Lista de imágenes de la galería (solo las rutas; las imágenes se suben a `assets/`).

## Estructura

- `index.html` — sitio público. Renderiza todo desde `data.json`.
- `data.json` — contenido editable (fechas, textos, teléfono, etc.).
- `morosho/index.html` — panel de administración.
- `assets/` — imágenes, logos y fotos de la banda.
- `CNAME` — dominio personalizado `la-once.com`.

## Desarrollo local

Simplemente abrí `index.html` en un navegador. Para probar el backoffice, un servidor local simple ayuda a que `fetch('data.json')` funcione correctamente:

```bash
python3 -m http.server 8000
```

Luego abrí:

- Sitio: `http://localhost:8000`
- Backoffice: `http://localhost:8000/morosho`
