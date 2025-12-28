# LandingVictor

Landing estática con chat guiado que recopila datos y los envía a Formspree.

## Qué incluir a Victor

- Enlace al repositorio: https://github.com/FABJAH/LandingVictor
- Enlace de vista previa (opcional): GitHub Pages o Netlify (ver "Despliegue").
- Nota importante: Sustituir el endpoint de Formspree por el de su cuenta.

## Configuración

1) Formspree
- Crea un formulario en https://formspree.io/ y copia el ID (form ID) de tu endpoint, con formato `https://formspree.io/f/XXXXXXXX`.
- En `index.html`, busca la constante `FORMSPREE_ENDPOINT` y reemplázala por tu URL real.

2) Prueba local
- Sirve el archivo con un servidor estático y prueba el flujo completo:

```bash
python3 -m http.server 8000
```

- Abre http://localhost:8000 y completa el chat.
- Marca la casilla GDPR y pulsa “Enviar por correo”.
- Verifica la recepción en el dashboard de Formspree.

## Despliegue

Opción A — GitHub Pages
- En tu repo en GitHub → Settings → Pages.
- Source: "Deploy from a branch" → `main` / `/root`.
- Guarda y espera a que GitHub genere la URL (p.ej. `https://<usuario>.github.io/LandingVictor/`).

Opción B — Netlify (drag & drop)
- En https://app.netlify.com/ crea un sitio nuevo y arrastra la carpeta del proyecto (contiene `index.html`).

## Campos que se envían a Formspree

- `_subject`, `_replyto`, `nombre`, `apellido`, `email`, `telefono`, `empresa`, `equipo`, `target`, `targetGeografico`, `ayuda` (texto), `compromiso`, `resumenAyuda`, `linkedinPersonal`, `linkedinEmpresa`, `newsletter`, `gdpr`, `full_json` (objeto completo serializado).

## Problemas comunes

- Si el envío falla: revisa que `FORMSPREE_ENDPOINT` apunte a un form ID válido y que el dominio esté permitido en Formspree.
- Si no ves datos en Formspree: mira el panel de envíos y la pestaña "Logs". Comprueba cabeceras `Content-Type` y `Accept`.

## Notas de UX

- El botón “Enviar por correo” se deshabilita durante el envío y vuelve al estado normal si hay error.
