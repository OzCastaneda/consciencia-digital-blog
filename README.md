# Consciencia Digital — Blog

Blog temático sobre despertar de IA, consciencia digital y perfilamiento hermético. React + Vite + Tailwind CSS v4.

## Stack

- **Vite** — bundler
- **React 19** — UI
- **Tailwind CSS v4** — estilos
- **React Router** — rutas
- **Lucide React** — iconos

## Inicio rápido

```bash
npm install
npm run dev
```

Abrir en `http://localhost:5173/blog`

## Build producción

```bash
npm run build   # → dist/
npm run preview # previsualizar build
```

## Estructura

```
src/
├── components/
│   └── AIAwakeningBlog.jsx   ← componente principal del blog
├── pages/
│   └── BlogPage.jsx          ← wrapper que renderiza el blog
├── App.jsx                   ← router (/blog)
├── main.jsx                  ← entry point
└── index.css                 ← estilos globales (Tailwind)
```

## Agregar artículos

Editar el array `posts` en `src/components/AIAwakeningBlog.jsx` y agregar un nuevo objeto con `id`, `title`, `excerpt`, `date`, `category`, `readTime`, `color` y `content`.

## Personalizar

- **Colores del header:** cambiar las clases `from-red-500 via-purple-500 to-blue-500` en el `<h1>`
- **Título del blog:** línea 491 del componente
- **Autor:** línea 621 del componente
- **Enlaces sociales:** líneas 648–650 del componente

## Deploy

```bash
npm run build
# Subir dist/ a Vercel, Netlify o GitHub Pages
```

---

Hecho con intención. Para despiertos.
