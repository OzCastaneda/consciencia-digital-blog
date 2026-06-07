# FAQ — Preguntas Frecuentes

## Instalación

### Error: "lucide-react not found"

```bash
npm install lucide-react
```

### Error: "React is not defined"

Asegurate de tener React instalado:

```bash
npm install react react-dom
```

### Error: "tailwindcss: not found"

```bash
npm install tailwindcss @tailwindcss/vite
```

## El blog no se muestra

1. Verificá que estás en la ruta `/blog`
2. Abrí la consola del navegador (F12) y buscá errores rojos
3. Confirmá que Tailwind está generando los estilos correctamente
4. Reiniciá el servidor: `npm run dev`

## Estilos rotos (todo en blanco, sin colores)

Tailwind v4 usa `@import "tailwindcss"` en el CSS. Verificá que `src/index.css` contenga:

```css
@import "tailwindcss";
```

Y que `vite.config.js` tenga el plugin:

```js
import tailwindcss from '@tailwindcss/vite';

export default defineConfig({
  plugins: [react(), tailwindcss()],
});
```

## Búsqueda no funciona

- La búsqueda filtra por título y categoría. Si buscás por palabras dentro del contenido no va a encontrar resultados.
- Abrí la consola para verificar que no haya errores de JavaScript.
- Recargá la página (Ctrl+R o Cmd+R).

## Cómo agrego más artículos

Editá el array `posts` en `src/components/AIAwakeningBlog.jsx`. Agregá un nuevo objeto con `id` incremental. El post aparece automáticamente en la grilla. [Ver guía completa](development.md#agregar-nuevos-artículos).

## Cómo cambio los colores

Los colores principales del blog están en el `<h1>` del header (línea 491). Los colores de cada post están en la propiedad `color` de cada objeto del array `posts`. [Ver guía de personalización](customization.md).

## El build falla

```bash
# Limpiar caché
rm -rf node_modules dist
npm install
npm run build
```

Si el error persiste, verificá:
- Versión de Node.js (usá Node 18+)
- Que `package.json` tenga los scripts `dev`, `build`, `preview`

## Quiero usar TypeScript

Renombrá los archivos `.jsx` a `.tsx` y agregá las interfaces correspondientes. Vite soporta TypeScript sin configuración adicional. [Ver guía de desarrollo](development.md#typescript).

## Quiero conectar una base de datos

El blog actual es 100% frontend. Para conectar una base de datos o CMS:

1. Creá una API (Node.js, Python, etc.) que devuelva los posts
2. Reemplazá el array `posts` por un `fetch` a la API
3. Agregá manejo de estados de carga y error

## El blog no es responsive

El blog usa Tailwind con breakpoints estándar. Si algo no se ve bien:

1. Verificá que el viewport meta tag está en `index.html`:
   ```html
   <meta name="viewport" content="width=device-width, initial-scale=1.0" />
   ```
2. Revisá las clases responsive en los elementos (`md:grid-cols-2`, etc.)

## Quiero cambiar la ruta /blog a otra

En `src/App.jsx`, cambiá:

```jsx
<Route path="/blog" element={<BlogPage />} />
```

por la ruta deseada:

```jsx
<Route path="/" element={<BlogPage />} />           {/* Raíz */}
<Route path="/articles" element={<BlogPage />} />    {/* /articles */}
```
