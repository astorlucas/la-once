# La Once — Agenda de Shows

Sitio oficial de **La Once**, banda uruguaya de cumbia. Servido con GitHub Pages en [la-once.com](https://la-once.com).

## Backoffice

El sitio incluye un panel de administración para modificar fechas, teléfono, colores, el video de YouTube y otros datos sin tener que editar código.

### Para el dueño de la banda

Andá a: `https://la-once.com/morosho`

Usá la **contraseña de administración** que te dieron. Desde ahí podés:

- Cambiar el teléfono de contrataciones.
- Cambiar el usuario y video de YouTube.
- Modificar los colores del sitio.
- Agregar, editar o eliminar fechas de shows.
- Subir imágenes directamente a la galería.

Cuando termines de editar, hacé clic en **Guardar cambios**.

### Configuración técnica (solo desarrollador)

La contraseña del backoffice es un **GitHub Personal Access Token** con permiso de escritura sobre el repositorio `astorlucas/la-once`.

1. Andá a GitHub → Settings → Developer settings → Personal access tokens.
2. Generá un token con permiso de escritura sobre el repositorio.
   - Token clásico: marcá el scope `repo`.
   - Fine-grained: dale acceso de lectura/escritura a `Contents`.
3. Ese token es la contraseña que se le entrega al usuario del backoffice.

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
