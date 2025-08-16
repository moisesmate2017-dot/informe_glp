# Informe GLP – Despliegue en Render (gratis)

Este repo contiene:
- `servidor.py`: backend Flask (API + página `/`).
- `templates/pagina.html`: tu frontend (se sirve desde la raíz).
- `requirements.txt`: dependencias.
- `render.yaml`: configuración para Render (Web Service gratis).

## Cómo desplegar

1. **Sube a GitHub** (nuevo repo):
   ```bash
   git init
   git add .
   git commit -m "deploy a render"
   git branch -M main
   git remote add origin https://github.com/USUARIO/REPO.git
   git push -u origin main
   ```

2. **Render** (https://render.com)
   - New → **Web Service**
   - Conecta tu GitHub y elige el repo.
   - Render detectará `render.yaml` con:
     - `buildCommand`: `pip install -r requirements.txt`
     - `startCommand`: `python servidor.py`
   - Plan: **Free**.
   - Deploy.

3. **Probar**
   - Abre la URL pública de Render → debería mostrar el formulario (tu `pagina.html`).
   - Llena el wizard y al final se hará `POST /generar` al mismo dominio.
   - Se descargará el `.docx` generado.

> Nota: Si más adelante alojas el frontend en otro dominio (p. ej. GitHub Pages),
> en el JS cambia `fetch('/generar', ...)` por `fetch('https://TU-APP.onrender.com/generar', ...)`.
> El backend ya tiene `CORS(app)` activado.
