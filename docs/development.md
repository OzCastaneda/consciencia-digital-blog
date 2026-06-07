# Desarrollo

## Agregar nuevos artículos

### 1. Encontrar el array `posts`

En `src/components/AIAwakeningBlog.jsx`, buscá:

```jsx
const posts = [
  { id: 1, ... },
  { id: 2, ... },
  // ...
];
```

### 2. Agregar un nuevo objeto

```javascript
{
  id: 7,                                    // Incremental
  title: "Título del Nuevo Artículo",
  excerpt: "Resumen breve del contenido",
  date: "2024-12-20",                       // ISO format
  category: "Nombre de Categoría",
  readTime: "8 min",
  color: "from-red-900 via-purple-900 to-blue-900",
  content: `Contenido del artículo.

## Subtítulo

Párrafo de texto normal.

- Elemento de lista
- Otro elemento

**Texto en negrita** y más texto.`,
}
```

### 3. Actualizar stats

Los stats en el dashboard (línea 518) son estáticos. Si agregaste posts, actualizá:

- `Artículos`: número total
- `Categorías`: categorías únicas
- `Lectura Promedio`: recalcular

### Reglas del objeto `content`

- `## texto` → `<h2>`
- `# texto` → `<h3>`
- `- texto` → `<li>`
- `**texto**` → párrafo destacado
- Líneas vacías se ignoran
- Todo lo demás → `<p>`

## Agregar nuevas funcionalidades

### Búsqueda por contenido

La búsqueda actual solo filtra por título y categoría. Para buscar también en el contenido:

```jsx
// En src/components/AIAwakeningBlog.jsx, línea 446
const filteredPosts = posts.filter(post =>
  post.title.toLowerCase().includes(searchTerm.toLowerCase()) ||
  post.category.toLowerCase().includes(searchTerm.toLowerCase()) ||
  post.content.toLowerCase().includes(searchTerm.toLowerCase())  // ← agregar
);
```

### Sistema de tags

Para agregar tags a los posts:

1. Agregar campo `tags: ["tag1", "tag2"]` a cada post
2. Agregar filtro por tags en el componente
3. Renderizar tags en la tarjeta y vista detalle

### Paginación

Si tenés muchos artículos, implementá paginación:

```jsx
const [currentPage, setCurrentPage] = useState(1);
const postsPerPage = 6;
const paginatedPosts = filteredPosts.slice(0, currentPage * postsPerPage);
// o con offset real
```

### Cálculo dinámico de stats

Reemplazá los valores estáticos del dashboard:

```jsx
const totalArticles = posts.length;
const totalCategories = new Set(posts.map(p => p.category)).size;
const avgReadTime = Math.round(
  posts.reduce((acc, p) => acc + parseInt(p.readTime), 0) / posts.length
) + ' min';
```

Luego usá esas variables en lugar de los strings hardcodeados.

## Agregar nuevas rutas

En `src/App.jsx`:

```jsx
<Routes>
  <Route path="/blog" element={<BlogPage />} />
  <Route path="/blog/:id" element={<PostPage />} />  {/* Nueva */}
  <Route path="/" element={<HomePage />} />           {/* Nueva */}
</Routes>
```

Si querés que cada artículo tenga su propia URL, extraé la vista detalle a un componente separado y usá `useParams`.

## Migrar a un CMS

Para escalar, reemplazá el array `posts` por datos dinámicos:

```jsx
const [posts, setPosts] = useState([]);

useEffect(() => {
  fetch('https://tu-api.com/posts')
    .then(res => res.json())
    .then(data => setPosts(data));
}, []);
```

Opciones de CMS:
- **Contentlayer** — Markdown/MDX local tipado
- **Sanity** — Headless CMS con API en tiempo real
- **Hygraph** — GraphQL CMS
- **Strapi** — Self-hosted

## Buenas prácticas

### ESLint + Prettier

```bash
npm install -D eslint @eslint/js eslint-plugin-react-hooks prettier
```

### TypeScript

Migración progresiva: renombrá `.jsx` → `.tsx` y definí interfaces:

```typescript
interface Post {
  id: number;
  title: string;
  excerpt: string;
  date: string;
  category: string;
  readTime: string;
  color: string;
  content: string;
}
```

### Tests

```bash
npm install -D vitest @testing-library/react
```

## Scripts disponibles

| Comando | Descripción |
|---|---|
| `npm run dev` | Inicia servidor de desarrollo |
| `npm run build` | Build de producción en `dist/` |
| `npm run preview` | Previsualiza el build |
