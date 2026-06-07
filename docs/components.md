# API de Componentes

## AIAwakeningBlog

Componente principal del blog. Es autocontenido: no requiere props, contexto ni proveedores externos.

```jsx
import AIAwakeningBlog from '../components/AIAwakeningBlog';

// Uso mínimo
<AIAwakeningBlog />
```

### Props

Ninguna. El componente no recibe props.

### Estados internos

| Estado | Tipo | Default | Descripción |
|---|---|---|---|
| `selectedPost` | `object \| null` | `null` | Post activo en vista detalle. `null` = vista lista. |
| `searchTerm` | `string` | `''` | Texto de búsqueda. Filtra posts por título y categoría. |

### Datos derivados

| Variable | Descripción |
|---|---|
| `filteredPosts` | `posts.filter(p => p.title.includes(searchTerm) \|\| p.category.includes(searchTerm))` |

### Subcomponentes internos

#### BlogCard (`<BlogCard post={post} />`)

Renderiza una tarjeta de artículo en la grilla.

| Prop | Tipo | Descripción |
|---|---|---|
| `post` | `object` | Objeto de post (ver estructura abajo) |

Comportamiento: `onClick` → `setSelectedPost(post)`

Renderiza:
- Barra superior con gradient (`post.color`)
- Categoría y tiempo de lectura
- Título y extracto
- Fecha formateada en español
- Icono de flecha

### Estructura de un post

```typescript
interface Post {
  id: number;           // Único, incremental
  title: string;        // Título del artículo
  excerpt: string;      // Resumen (1-2 líneas)
  date: string;         // Fecha ISO: "YYYY-MM-DD"
  category: string;     // Nombre de categoría
  readTime: string;     // Ej: "8 min"
  color: string;        // Clases gradient: "from-red-900 via-purple-900 to-blue-900"
  content: string;      // Markdown simplificado (##, -, **, párrafos)
}
```

### Formato de `content`

El contenido se parsea línea por línea:

| Patrón | Elemento HTML |
|---|---|
| `## texto` | `<h2>` |
| `# texto` | `<h3>` |
| `- texto` | `<li>` |
| `**texto**` | `<p>` con `font-semibold` |
| Línea vacía | Omitida |
| Cualquier otra línea | `<p>` |

### Vistas

#### Vista lista (`selectedPost === null`)

- Stats dashboard (4 cards: artículos, categorías, tiempo lectura, estado)
- SearchBar
- Grilla de `BlogCard` (1 col mobile, 2 cols tablet+)
- Sección "Sobre Este Blog" y "Próximamente"

#### Vista detalle (`selectedPost !== null`)

- Botón "← Volver"
- Header gradient (64rem de alto)
- Categoría, fecha, tiempo de lectura
- Título
- Contenido parseado
- Footer de autor y copyright

### Estilos

- Tema oscuro (`bg-gray-950`, `text-white`)
- Acento púrpura (`text-purple-400`, `hover:border-purple-500`)
- Gradientes en cards y headers
- Responsive via Tailwind breakpoints
- Header sticky con backdrop blur

### Dependencias externas

- `lucide-react`: `Calendar`, `ArrowRight`, `Search`
- `React.useState`: manejo de estado interno

## BlogPage

Wrapper de página. Renderiza `AIAwakeningBlog`.

```jsx
import AIAwakeningBlog from '../components/AIAwakeningBlog';

export default function BlogPage() {
  return <AIAwakeningBlog />;
}
```

## App (Router)

Define la ruta `/blog` que renderiza `BlogPage`.

```jsx
<BrowserRouter>
  <Routes>
    <Route path="/blog" element={<BlogPage />} />
  </Routes>
</BrowserRouter>
```
