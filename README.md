# LOMEN — Landing Page

> Clásicos católicos reimpresos. Edición minimalista. Precio justo.

Landing de captura de leads para la primera colección: tres títulos en dominio público reimpresos bajo la estética LOMEN.

---

## Estructura del proyecto

```
lomen-landing/
├── index.html              ← toda la landing en un solo archivo
├── assets/
│   ├── portada-kempis.png  ← portada Imitación de Cristo (Canva)
│   ├── portada-juan.png    ← portada Noche Oscura (Canva)
│   └── portada-teresa.png  ← portada Camino de Perfección (Canva)
├── README.md               ← este archivo
└── CLAUDE.md               ← contexto del proyecto para Claude
```

Todo el código vive en `index.html`. No hay frameworks, no hay build step, no hay node_modules. Un solo archivo que cualquier persona puede abrir en el navegador y editar en VS Code.

---

## Tokens de diseño

Edita estas variables CSS al inicio de `index.html` para cambiar toda la paleta sin tocar el HTML:

```css
:root {
  --ink:         #1A1410;   /* texto principal */
  --paper:       #F6F1E9;   /* fondo general */
  --paper-dark:  #EDE5D6;   /* fondo de tarjetas y campos */
  --border:      #C9B89A;   /* líneas y bordes */
  --rust:        #7B3020;   /* color primario: botones y acentos */
  --rust-light:  #9B4030;   /* hover del color primario */
  --muted:       #8C7A65;   /* texto secundario y labels */
  --text-body:   #4A3A28;   /* texto de párrafos */
}
```

Fuentes: `EB Garamond` (display, serif) + `Jost` (cuerpo, sans). Ambas vienen de Google Fonts, ya incluidas en el `<head>`.

---

## Dónde editar cada sección

| Qué cambiar | Qué buscar en index.html |
|---|---|
| Título hero | `<h1 class="hero-title">` |
| Subtítulo hero | `<p class="hero-author">` |
| Descripción hero | `<p class="hero-desc">` |
| Datos de cada libro | Bloques `<!-- LIBRO 01 -->`, `<!-- LIBRO 02 -->`, `<!-- LIBRO 03 -->` |
| Bullets de propuesta de valor | Bloques dentro de `<div class="props">` |
| Texto de la sección de reserva | `<p class="reserve-copy">` |
| Mensaje de éxito tras submit | `<div class="success" id="success">` |
| Colores | Variables CSS `:root` al inicio del `<style>` |

---

## Cómo conectar Formspree (captura de emails)

1. Ve a [formspree.io](https://formspree.io) → crea cuenta gratis → nuevo formulario
2. Copia el endpoint. Formato: `https://formspree.io/f/xabc1234`
3. En `index.html`, busca:

```html
<form id="form" class="form-row" action="TU_ENDPOINT_FORMSPREE" method="POST">
```

4. Reemplaza `TU_ENDPOINT_FORMSPREE` con tu endpoint
5. Los emails de reserva llegan directo a tu bandeja. Listo.

Los leads llegan con dos campos: `email` y `interes` (valor `coleccion-1`). Útil para segmentar cuando agregues más colecciones.

---

## Cómo reemplazar los mockups por portadas reales

Cuando tengas los PNGs de Canva (uno por libro):

**Portada del hero (libro grande):**
1. Guarda como `assets/portada-kempis.png`
2. En `index.html`, busca el comentario `<!-- MOCKUP HERO -->`
3. Borra el `<div class="book">` y el `<div class="book-shadow">`
4. Pon en su lugar: `<img src="assets/portada-kempis.png" alt="Imitación de Cristo" class="book-img">`

**Portadas de las tarjetas (los 3 libros):**
1. Guarda como `assets/portada-kempis.png`, `assets/portada-juan.png`, `assets/portada-teresa.png`
2. Busca el comentario `<!-- LIBRO 01 -->` (y 02, 03)
3. Borra el `<div class="libro-cover">` completo
4. Pon en su lugar: `<img src="assets/portada-X.png" alt="…" class="libro-cover-img">`
5. Agrega este CSS en el `<style>`: `.libro-cover-img { width: 100%; aspect-ratio: 2/3; display: block; border-bottom: 1px solid var(--border); }`

---

## Deploy en Vercel

**Desde GitHub (recomendado):**

```bash
git init
git add .
git commit -m "feat: landing MVP LOMEN"
git remote add origin https://github.com/TU_USUARIO/lomen-landing.git
git push -u origin main
```

Luego: [vercel.com](https://vercel.com) → Add New Project → importa el repo → Deploy. URL pública en 2 minutos.

**Desde Vercel CLI:**

```bash
npm install -g vercel
cd lomen-landing
vercel
```

**Dominio personalizado:** Vercel → Settings → Domains → agrega tu dominio → configura los DNS según las instrucciones.

---

## Git — flujo de trabajo

```bash
# Para cualquier cambio:
git add index.html
git commit -m "feat: descripción del cambio"
git push
# Vercel despliega automáticamente tras cada push a main
```

Convenciones de commit: `feat:` para nuevo contenido, `fix:` para correcciones, `style:` para cambios visuales.

---

## Migración a Supabase (Fase 2)

Cuando quieras guardar leads en base de datos:

1. Crea proyecto en [supabase.com](https://supabase.com)
2. Crea tabla `leads`:
   ```sql
   create table leads (
     id uuid default gen_random_uuid() primary key,
     email text not null,
     interes text,
     created_at timestamptz default now()
   );
   ```
3. En el script del formulario, reemplaza el `fetch(form.action, ...)` por la llamada al SDK de Supabase
4. Agrega las variables de entorno `SUPABASE_URL` y `SUPABASE_ANON_KEY` en Vercel

---

*LOMEN — Lima, Perú*
