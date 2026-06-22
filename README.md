# La Once — Agenda de Shows

Sitio oficial de **La Once**, banda uruguaya de cumbia. Servido con GitHub Pages en [la-once.com](https://la-once.com).

## Backoffice

El sitio incluye un panel de administración para modificar fechas, teléfono, colores, el video de YouTube en autoplay y otros datos sin tener que editar código.

### Acceder

Andá a: `https://la-once.com/morosho`

Para entrar usá tu **GitHub Personal Access Token** con permiso de escritura sobre el repositorio `astorlucas/la-once`. El mismo token se usa para guardar los cambios.

### Crear el token

1. Andá a GitHub → Settings → Developer settings → Personal access tokens.
2. Generá un token con permiso de escritura sobre el repositorio `astorlucas/la-once`.
   - Token clásico: marcá el scope `repo`.
   - Fine-grained: dale acceso de lectura/escritura a `Contents`.
3. Copiá el token y usalo como contraseña en `/morosho`.

### Qué se puede editar

- Teléfono de contrataciones.
- Usuario de YouTube.
- **Video de YouTube para autoplay** (si ponés una URL de video específica, se usa ese; si no, se usa el canal).
- Año y subtítulo de la agenda.
- Frases del hero.
- **Colores del sitio** con color picker.
- Fechas de las columnas laterales.
- Agenda completa de shows.
- Lista de imágenes de la galería (solo las rutas; las imágenes se suben a `assets/`).

### Estructura

- `index.html` — sitio público. Renderiza todo desde `data.json`.
- `data.json` — contenido editable (fechas, textos, teléfono, colores, etc.).
- `morosho/index.html` — panel de administración.
- `assets/` — imágenes, logos y fotos de la banda.
- `CNAME` — dominio personalizado `la-once.com`.

### Desarrollo local

Simplemente abrí `index.html` en un navegador. Para probar el backoffice, un servidor local simple ayuda a que `fetch('data.json')` funcione correctamente:

```bash
python3 -m http.server 8000
```

Luego abrí:

- Sitio: `http://localhost:8000`
- Backoffice: `http://localhost:8000/morosho`
