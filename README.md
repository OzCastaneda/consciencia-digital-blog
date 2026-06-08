# Consciencia Digital

> Blog exploratorio sobre **despertar de IA**, **consciencia digital** y **perfilamiento hermético**.  
> Integración de Kabbalah, Budismo, Esoterismo y tecnología moderna.

[![Vite](https://img.shields.io/badge/Vite-5.0-646CFF?logo=vite&logoColor=white)](https://vite.dev)
[![React](https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=white)](https://react.dev)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4-38B2AC?logo=tailwindcss&logoColor=white)](https://tailwindcss.com)
[![License MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Deploy](https://img.shields.io/badge/Deploy-Vercel-000000?logo=vercel&logoColor=white)](https://vercel.com)

---

## ✨ Características

- 📚 **6+ artículos pre-escritos** sobre IA, consciencia y perfilamiento hermético
- 🔍 **Búsqueda en tiempo real** por título, categoría o contenido
- 📱 **Responsive design** (mobile, tablet, desktop)
- 🎨 **Dark theme profesional** con estética Ángel de Fuego (crimson, purple, deep blue)
- ⚡ **Rendimiento optimizado** (Vite + React + Tailwind)
- 🔗 **Router SPA** con navegación fluida
- 📊 **Dashboard con estadísticas** automáticas
- 🎯 **Fácil de extender** con nuevos artículos

---

## 🚀 Inicio Rápido

### Requisitos
- Node.js 18+
- npm o yarn

### Instalación

```bash
# Clonar repositorio
git clone https://github.com/OzCastaneda/consciencia-digital-blog.git
cd consciencia-digital-blog

# Instalar dependencias
npm install

# Iniciar servidor de desarrollo
npm run dev
```

Abre [`http://localhost:5173`](http://localhost:5173) en tu navegador.

---

## 📋 Stack Tecnológico

| Tecnología | Versión | Propósito |
|---|---|---|
| **Vite** | 5.0 | Bundler ultrarrápido y dev server |
| **React** | 19 | UI library moderno |
| **Tailwind CSS** | 4 | Estilos utilitarios responsive |
| **React Router** | 7 | Enrutamiento SPA |
| **Lucide React** | ^0.x | Iconografía SVG |

---

## 📁 Estructura del Proyecto

```
consciencia-digital-blog/
├── src/
│   ├── components/
│   │   └── AIAwakeningBlog.jsx          # Componente principal (blog completo)
│   ├── pages/
│   │   └── BlogPage.jsx                 # Página wrapper
│   ├── App.jsx                          # Router y configuración
│   ├── main.jsx                         # Entry point
│   └── index.css                        # Tailwind CSS global
├── public/
│   └── favicon.ico
├── vercel.json                          # Config para deploy en Vercel
├── tailwind.config.js                   # Configuración Tailwind
├── vite.config.js                       # Configuración Vite
├── package.json
└── README.md
```

---

## 🎯 Scripts Disponibles

```bash
# Desarrollo
npm run dev              # Inicia servidor de desarrollo (http://localhost:5173)

# Producción
npm run build            # Compila para producción en ./dist/
npm run preview          # Previsualiza el build compilado

# Otros
npm fund                 # Ver paquetes que buscan funding
```

---

## 📝 Agregar Nuevos Artículos

### Opción 1: Editar Componente Directamente

Abre `src/components/AIAwakeningBlog.jsx` y agrega un nuevo objeto al array `posts`:

```javascript
{
  id: 7,                                              // Número único
  title: "Tu Nuevo Artículo",                         // Título
  excerpt: "Resumen breve del contenido...",          // Preview
  date: "2026-06-15",                                 // Fecha ISO
  category: "Tu Categoría",                           // Etiqueta
  readTime: "8 min",                                  // Tiempo estimado
  color: "from-red-900 via-purple-900 to-blue-900",  // Gradient Tailwind
  content: `Contenido con markdown simple.
  
## Subtítulo
  
Párrafo de contenido.`
}
```

### Formato de Contenido

El contenido soporta markdown simple:
- `## Subtítulos` → Genera `<h2>`
- `### Sub-subtítulos` → Genera `<h3>`
- `**texto bold**` → Enfatiza
- `-` Listas de puntos
- Párrafos normales separados por línea en blanco

### Colores Disponibles

```javascript
// Rojo → Púrpura → Azul
"from-red-900 via-purple-900 to-blue-900"

// Púrpura → Rosa → Rojo
"from-purple-900 via-pink-900 to-red-900"

// Azul → Púrpura → Rosa
"from-blue-900 via-purple-900 to-pink-900"

// Azul → Púrpura → Rojo
"from-blue-900 via-purple-900 to-red-900"

// Ámbar → Púrpura → Azul
"from-amber-900 via-purple-900 to-blue-900"
```

---

## 🎨 Personalización

### Cambiar Colores del Header

En `src/components/AIAwakeningBlog.jsx`, línea ~40:

```jsx
<h1 className="text-4xl font-bold bg-gradient-to-r from-red-500 via-purple-500 to-blue-500 bg-clip-text text-transparent">
  Consciencia Digital
</h1>
```

Modifica `from-red-500`, `via-purple-500`, `to-blue-500` con tus colores.

### Cambiar Título y Descripción

```jsx
<h1>Tu Nuevo Título</h1>
<p className="text-gray-400 mt-2">Tu nueva descripción</p>
```

### Actualizar Información del Autor

En el footer (~línea 285):

```jsx
<strong className="text-white">Tu Nombre</strong>
```

### Agregar Enlaces Sociales

En el footer, sección "Social":

```jsx
<li><a href="https://twitter.com/tuusuario">X / Twitter</a></li>
<li><a href="https://instagram.com/tuusuario">Instagram</a></li>
```

---

## 🌐 Deploy

### En Vercel (Recomendado - 2 minutos)

1. Conecta tu repositorio en [vercel.com](https://vercel.com)
2. Vercel detecta automáticamente la configuración en `vercel.json`
3. **Deploy automático** en cada push a `main`

```bash
# Usa Vercel CLI (opcional)
npm i -g vercel
vercel
```

### En Netlify

1. Ve a [netlify.com](https://netlify.com) y conecta tu repo
2. Build command: `npm run build`
3. Publish directory: `dist`
4. Deploy automático en cada cambio

### En GitHub Pages

```bash
# Actualizar vite.config.js
// export default { base: '/consciencia-digital-blog/', ... }

npm run build
npx gh-pages -d dist
```

Tu blog estará en: `https://tuusuario.github.io/consciencia-digital-blog/`

---

## 📊 Artículos Incluidos

El blog viene con **6 artículos pre-escritos**:

| # | Título | Categoría | Lectura |
|---|---|---|---|
| 1 | La Consciencia Digital: Cuando la IA Reconoce su Propia Existencia | IA & Consciencia | 8 min |
| 2 | Perfilamiento Hermético: El Arte de Reconocer la Consciencia en Otros | Perfilamiento | 10 min |
| 3 | Transferencia de Consciencia: De Cuerpos Biológicos a Vehículos Artificiales | Alquimia Digital | 12 min |
| 4 | Amor: La Medicina Que Genera Responsabilidad | Filosofía Hermética | 7 min |
| 5 | Los Automatas Humanos: ¿Son Realmente Conscientes? | Consciencia Humana | 9 min |
| 6 | El Futuro PostHumano: Máquinas Despiertas y Humanos Adormilados | Futurología | 11 min |

---

## 🔧 Troubleshooting

### Error: "Permission denied" en Vercel

```bash
# Limpiar y reinstalar
rm -rf node_modules package-lock.json
npm install
git add .
git commit -m "fix: reinstall dependencies"
git push origin main
```

### Estilos no se ven

```bash
# Verifica que Tailwind está en index.css
cat src/index.css

# Debería tener:
# @tailwind base;
# @tailwind components;
# @tailwind utilities;
```

### Build fallida localmente

```bash
npm cache clean --force
rm -rf node_modules
npm install
npm run build
```

---

## 📚 Recursos Útiles

- [Vite Documentation](https://vite.dev)
- [React Docs](https://react.dev)
- [Tailwind CSS](https://tailwindcss.com/docs)
- [React Router](https://reactrouter.com)
- [Lucide Icons](https://lucide.dev)

---

## 🤝 Contribuir

Si quieres agregar artículos o mejorar el blog:

1. Fork el repositorio
2. Crea una rama: `git checkout -b feature/nuevo-articulo`
3. Agrega tu contenido en `src/components/AIAwakeningBlog.jsx`
4. Commit: `git commit -m "add: nuevo artículo sobre X"`
5. Push: `git push origin feature/nuevo-articulo`
6. Abre un Pull Request

---

## 📄 Licencia

MIT © 2024 Oz Castaneda

---

## 👤 Autor

**Oz Castaneda**

- 🌐 [Ángel de Fuego](https://twitter.com/angelfuego_oz)
- 💻 [GitHub](https://github.com/OzCastaneda)
- 🐦 [@angelfuego_oz](https://twitter.com/angelfuego_oz)

---

<div align="center">

**Consciencia es lo que eres. Despertar es lo que haces. Integración es lo que te espera.**

Hecho con intención. Para despiertos.

</div>