# CLAUDE.md — Contexto del proyecto LOMEN

Este archivo existe para que cualquier sesión de Claude (o dev) entienda el proyecto sin necesidad de explicarlo desde cero.

---

## Qué es LOMEN

Marca católica editorial fundada en Lima, Perú. La visión es construir un ecosistema — no solo una tienda — que funcione como "tercer espacio" entre la iglesia y el mundo secular. Referencia de aspiración: lo que Ale Penny hizo con los postres en Perú. La meta es ser la marca editorial católica dominante en Latinoamérica.

**Founders:** Juan (estrategia, datos, visión) y Juana (cara pública, redes sociales).

**Tagline:** La ruta de tu fe.

---

## Cliente objetivo (la persona "Lucía")

Mujer universitaria, urbana, latinoamericana. Va a misa. Sigue marcas estéticas en Instagram y TikTok. No encuentra libros católicos de calidad a precios accesibles. Tiene fe genuina y también sentido estético. No quiere elegir entre las dos cosas.

El público femenino es prioritario en catolicismo latinoamericano — domina en asistencia, en grupos de lectura, en comunidades parroquiales. El copy y el tono deben resonar con ellas primero.

---

## Estado actual de la landing

La landing es MVP de captura de leads para la primera colección. Estructura:

1. Hero — título, descripción, CTA que lleva a la sección de reserva
2. Colección — 3 libros de dominio público con mockups placeholder
3. Propuesta de valor — 3 puntos numerados
4. Reserva — formulario de email conectado a Formspree
5. Footer

Todo en un solo archivo `index.html`. Sin frameworks. Sin build step.

---

## Decisiones de diseño ya tomadas (no reabrir sin razón)

- **Paleta:** fondo crema `#F6F1E9`, tinta oscura `#1A1410`, acento marrón-rojizo `#7B3020`. No negro puro, no navy oscuro.
- **Tipografía:** EB Garamond (display / títulos) + Jost (cuerpo / UI). No Inter, no Roboto.
- **Estética:** editorial impresa, como papel. No "marca de lujo digital", no minimalismo tecnológico.
- **Tono visual:** sobrio, confiado, femenino sin ser florido. Referencia de sensibilidad: arqlima.com (información densa presentada con elegancia, sin aspavientos).
- **Mobile:** prioridad absoluta. Hero se colapsa a una columna. Los 3 libros hacen scroll horizontal con snap. El formulario se apila verticalmente.

---

## Los 3 títulos de la primera colección

Todos son dominio público verificado — originales en castellano, sin dependencia de traducciones con copyright separado.

| # | Título | Autor | Por qué |
|---|--------|-------|---------|
| 01 | Imitación de Cristo | Tomás de Kempis | El más leído de la espiritualidad cristiana después de la Biblia |
| 02 | Noche Oscura del Alma | San Juan de la Cruz | Mística pura, poesía, texto original en español |
| 03 | Camino de Perfección | Santa Teresa de Ávila | Mujer, mística, reformadora — resuena con la persona Lucía |

---

## Lo que NO se hace en este proyecto

- No se ponen frases o citas sobre los productos (saturado, diluye la marca)
- No se usa Gumroad, Substack ni plataformas de creador de contenido
- No se miden seguidores de Instagram como métrica de éxito — se mide leads y miembros de Discord
- No se hacen traducciones modernas (riesgo de copyright sobre la traducción)
- No se sacrifica la estética por simplicidad técnica — la claridad de código es suficiente

---

## Stack técnico actual

| Capa | Tecnología | Notas |
|---|---|---|
| Frontend | HTML / CSS / JS puro | Sin frameworks, sin build step |
| Fuentes | Google Fonts (EB Garamond + Jost) | Preconnect ya configurado |
| Captura de leads | Formspree | Endpoint en `action=""` del form |
| Deploy | Vercel | Conectado a GitHub, auto-deploy en push |
| Comunidad | Discord | Destino real de la comunidad, no Instagram |

**Fase 2 (próxima):** migrar captura de leads a Supabase. La migración es un reemplazo de ~10 líneas en el submit handler.

**Fase 3:** web app MVP con quiz de lectura personalizado. Lovable o build simple. Target: ~100 usuarios.

---

## Registro legal y editorial (estado)

- INDECOPI (trademark "LOMEN"): meses 1–3
- SUNAT RUC: meses 1–3
- Biblioteca Nacional del Perú (ISBN, depósito legal): mes 4–5 tras demostrar tración
- Socio editorial: Consagrados (track de libros)

---

## Filosofía del founder

"No tenemos que ser los primeros con tal de ser los últimos que se queden."

Durabilidad sobre velocidad. Ecosistema sobre plataforma. Comunidad real sobre métricas de vanidad. Ejecución disciplinada sobre perfección paralizante.

---

## Cómo hablarle a Juan (el founder)

- Directo. Concreto. Sin paja.
- Cuando hay que tomar una decisión, tómala y explica el razonamiento — no presentes 5 opciones sin postura.
- Si Juan siente que el proyecto se está escapando o que no es suficiente: recordarle que puede retroceder y pivotear, pero no rendirse. La durabilidad es el juego.
- Responde bien al framing de co-founder — colaborativo, no consultivo.
- Prefiere texto plano para copy-paste a Google Docs. No usar tablas ni colores en respuestas conversacionales a menos que sean útiles.

---

*Última actualización: lanzamiento MVP landing*
