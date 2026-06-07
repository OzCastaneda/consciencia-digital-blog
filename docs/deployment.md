# Despliegue

## Build de producción

```bash
npm run build
```

Esto genera una carpeta `dist/` con los archivos estáticos listos para servir.

## Vercel (recomendado)

### CLI

```bash
npm install -g vercel
vercel
```

Seguí las instrucciones interactivas. Vercel detecta automáticamente Vite y configura el build.

### Dashboard

1. Conectá tu repositorio en [vercel.com](https://vercel.com)
2. Framework preset: **Vite**
3. Build command: `npm run build`
4. Output directory: `dist`
5. Deploy automático en cada push

### Configuración adicional (si es necesario)

Creá `vercel.json` en la raíz:

```json
{
  "rewrites": [
    { "source": "/(.*)", "destination": "/index.html" }
  ]
}
```

## Netlify

### Manual

1. Creá cuenta en [netlify.com](https://netlify.com)
2. Conectá tu repositorio
3. Config:
   - Build command: `npm run build`
   - Publish directory: `dist`
4. Deploy automático

### netlify.toml

```toml
[build]
  command = "npm run build"
  publish = "dist"

[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 200
```

## GitHub Pages

### 1. Instalar gh-pages

```bash
npm install --save-dev gh-pages
```

### 2. Configurar package.json

```json
{
  "homepage": "https://tuusuario.github.io/tu-repo",
  "scripts": {
    "predeploy": "npm run build",
    "deploy": "gh-pages -d dist"
  }
}
```

### 3. Desplegar

```bash
npm run deploy
```

### 4. Configurar GitHub

En Settings > Pages: Source → `gh-pages` branch, folder `/ (root)`.

### SPA routing en GitHub Pages

Como GitHub Pages no soporta fallback a `index.html`, creá un archivo `404.html` idéntico a `index.html` en el build, o usá el truco del `404.html` con redirect por JS.

## Cloudflare Pages

1. Conectá tu repositorio en [pages.cloudflare.com](https://pages.cloudflare.com)
2. Build command: `npm run build`
3. Build output: `dist`
4. En Settings > Routing, agregá rule de SPA redirect: `/* → /index.html` (status 200)

## Render

1. Creá servicio Static Site en [render.com](https://render.com)
2. Build command: `npm run build`
3. Publish directory: `dist`

## Consideraciones post-deploy

- Verificá que la ruta `/blog` funciona correctamente
- Si usás un subdirectorio (ej: `tusitio.com/blog/`), configurá `base` en `vite.config.js`:

```js
export default defineConfig({
  base: '/blog/',
  plugins: [react(), tailwindcss()],
})
```

- Configurá redirects para SPA (todas las rutas → `index.html`)
- Agregá dominio personalizado en la plataforma elegida
