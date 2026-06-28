# Publicar fénixbipolar.es en GitHub + Vercel

La web es **estática** (HTML + imágenes, sin build). Vercel solo tiene que servir la carpeta `web/`.

## 0. Antes de nada
- **Dominio:** confirma la forma exacta registrada (con o sin tilde). Si no es `www.fenixbipolar.es`, edita la constante `BASE` en `web/robots.txt` y `web/sitemap.xml`.
- **Estado actual:** es una **maqueta**. Todas las páginas llevan `noindex` y `robots.txt` bloquea Google. Se puede publicar en Vercel sin que Google la indexe (perfecto para enseñarla al Dr.).

## 1. GitHub
Recomendado: un repo limpio solo con la web.

```bash
cd "RUTA/PORTAL BIPOLAR/web"
git init
git add .
git commit -m "fénixbipolar.es — maqueta inicial"
git branch -M main
git remote add origin https://github.com/TU-USUARIO/fenixbipolar.git
git push -u origin main
```

> Si prefieres subir todo el proyecto (con manuscritos y demás), hazlo desde la raíz `PORTAL BIPOLAR/`; luego en Vercel pon **Root Directory = `web`**.

## 2. Vercel
1. vercel.com → **Add New → Project** → importa el repo.
2. **Framework Preset:** Other.
3. **Root Directory:** `./` si el repo es solo la web · `web` si subiste todo el proyecto.
4. **Build & Output:** sin Build Command, sin Output Directory (déjalo vacío, es estático).
5. **Deploy.** En segundos tienes una URL `…vercel.app` para enseñarla.

`vercel.json` ya incluye cache de assets y cabeceras de seguridad básicas.

## 3. Dominio propio
Vercel → proyecto → **Settings → Domains** → añade `fenixbipolar.es` y sigue las instrucciones DNS (registro A / CNAME) en tu registrador.

## 4. Checklist de LANZAMIENTO (cuando el Dr. dé el aval)
- [ ] Quitar `<meta name="robots" content="noindex">` de las 27 páginas + del `404.html`.
- [ ] En `robots.txt`: borrar `Disallow: /` y dejar `Allow: /`.
- [ ] Quitar de los pies "Maqueta de concepto (noindex…)".
- [ ] Conectar el botón **"Quiero recibirlo"** (newsletter) a un servicio real (ahora apunta a `#`).
- [ ] Confirmar `BASE` correcta en `sitemap.xml` y `robots.txt`.
- [ ] Subir el `sitemap.xml` a Google Search Console.
- [ ] (Opcional) Colocar la foto del Dr. (`assets/img/01-dr-rafael.webp`) en "Sobre el portal".

## Archivos de publicación creados
`web/robots.txt` · `web/sitemap.xml` · `web/404.html` · `web/vercel.json`

## Símbolos de marca
`web/assets/marca/YOELFENIX.png` (logo + favicon) · `web/assets/marca/INFINITO-INTERROGACION.png` (+ versión `-blanco` para fondo oscuro, en el pie). Originales también en `assets/marca/`.
