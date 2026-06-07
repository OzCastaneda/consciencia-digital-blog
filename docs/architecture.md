# Arquitectura

## Vista general

El blog es una **SPA** (Single Page Application) construida con Vite + React. El componente `AIAwakeningBlog` maneja todo el estado interno (artículo seleccionado, búsqueda) sin necesidad de un estado global o backend.

```
┌─────────────┐     ┌──────────────────┐     ┌──────────────────┐
│  index.html │ ──> │   src/main.jsx   │ ──> │    src/App.jsx   │
└─────────────┘     └──────────────────┘     └──────────────────┘
                                                    │
                                                    ▼
                                          ┌──────────────────┐
                                          │  pages/BlogPage  │
                                          └──────────────────┘
                                                    │
                                                    ▼
                                          ┌──────────────────┐
                                          │ components/      │
                                          │ AIAwakeningBlog  │
                                          └──────────────────┘
```

## Flujo de datos

```
AIAwakeningBlog (stateful component)
├── state: selectedPost (null | Post)
├── state: searchTerm (string)
├── derived: filteredPosts (posts filtrados por searchTerm)
│
├── Vista lista (selectedPost === null)
│   ├── Stats Dashboard (cálculo sobre posts[])
│   ├── SearchBar → setSearchTerm
│   └── BlogCard[] → setSelectedPost(post)
│
└── Vista detalle (selectedPost !== null)
    ├── Header con gradient
    ├── Metadata (fecha, categoría, tiempo)
    ├── Contenido formateado (parser inline)
    └── Botón volver → setSelectedPost(null)
```

## Estructura de archivos

```
proyecto/
├── index.html                     # Entry point HTML
├── vite.config.js                 # Config Vite + plugins
├── tailwind.config.js             # Config Tailwind (referencia)
├── package.json                   # Dependencias y scripts
├── postcss.config.js              # PostCSS (si aplica)
├── public/
│   └── favicon.ico
├── src/
│   ├── main.jsx                   # Monta React en #root
│   ├── App.jsx                    # Router con ruta /blog
│   ├── index.css                  # @import "tailwindcss"
│   ├── components/
│   │   └── AIAwakeningBlog.jsx    # Componente principal
│   └── pages/
│       └── BlogPage.jsx           # Página wrapper
└── docs/                          # Documentación
    ├── index.md
    ├── architecture.md
    ├── components.md
    ├── usage.md
    ├── customization.md
    ├── development.md
    ├── deployment.md
    └── faq.md
```

## Decisiones técnicas

### Por qué un solo componente

`AIAwakeningBlog` es autocontenido: maneja su propio estado, renderizado condicional (lista/detalle) y estilos. No necesita props externas. Esto permite copiar el archivo a cualquier proyecto y usarlo de inmediato.

### Tailwind CSS v4

Tailwind v4 usa `@import "tailwindcss"` en vez de las directivas `@tailwind`. La configuración se declara en CSS con `@theme` en lugar de `tailwind.config.js`. Se integra con Vite mediante el plugin `@tailwindcss/vite`.

### Sin backend

Los artículos se definen como objetos en un array dentro del componente. No hay base de datos, API ni CMS. Para escalar, se podría migrar a MDX, Contentlayer o un headless CMS.

### Enrutamiento

Se usa React Router DOM con una sola ruta (`/blog`). El enrutamiento interno (lista vs. detalle) se maneja con estado local de React, no con rutas del router.

## Dependencias clave

| Paquete | Versión | Propósito |
|---|---|---|
| `react` | ^19.2.7 | UI library |
| `react-dom` | ^19.2.7 | Renderizado DOM |
| `react-router-dom` | ^7.17.0 | Enrutamiento |
| `lucide-react` | ^1.17.0 | Iconos |
| `vite` | ^8.0.16 | Bundler |
| `@vitejs/plugin-react` | ^6.0.2 | Plugin Vite para React |
| `@tailwindcss/vite` | — | Plugin Vite para Tailwind v4 |
| `tailwindcss` | ^4.3.0 | Framework CSS |
