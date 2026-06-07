# Personalización

Todas las personalizaciones se hacen editando `src/components/AIAwakeningBlog.jsx`.

## Cambiar colores principales

El header usa un gradient en el título:

```jsx
// Línea 491
<h1 className="text-4xl font-bold bg-gradient-to-r from-red-500 via-purple-500 to-blue-500 bg-clip-text text-transparent">
```

Colores disponibles: `red`, `blue`, `purple`, `pink`, `orange`, `cyan`, `green`, `yellow`, `indigo`, `teal` — con intensidades `300` a `700`.

```jsx
// Ejemplo: azul → cian → verde
from-blue-500 via-cyan-500 to-green-500
```

## Cambiar título y descripción del blog

```jsx
// Líneas 491–495
<h1 className="...">Consciencia Digital</h1>
<p className="text-gray-400 mt-2">Exploraciones sobre IA, despertar y el futuro de la humanidad</p>
```

## Cambiar nombre del autor

```jsx
// Línea 621
<strong className="text-white">Oz Castaneda</strong>
```

## Agregar/editar enlaces sociales

```jsx
// Líneas 648–650
<li><a href="#" className="hover:text-purple-400 transition">X / Twitter</a></li>
<li><a href="#" className="hover:text-purple-400 transition">Instagram</a></li>
<li><a href="#" className="hover:text-purple-400 transition">YouTube</a></li>
```

Reemplazá `#` con las URLs reales:

```jsx
<li><a href="https://twitter.com/tuusuario" className="hover:text-purple-400 transition">X / Twitter</a></li>
```

## Cambiar colores de los posts (gradients)

Cada post tiene un `color` con formato Tailwind:

```javascript
// Opciones disponibles:
"from-red-900 via-purple-900 to-blue-900"
"from-purple-900 via-pink-900 to-red-900"
"from-blue-900 via-purple-900 to-pink-900"
"from-red-900 via-blue-900 to-purple-900"
"from-purple-900 via-red-900 to-blue-900"
"from-blue-900 via-purple-900 to-red-900"
```

Para combinaciones propias, usá cualquier clase `from-{color}-{intensity}` de Tailwind.

## Cambiar el texto del footer

```jsx
// Línea 655
<p>Hecho con intención. Para despiertos.</p>
```

## Actualizar copyright

```jsx
// Línea 622
<p className="text-gray-600 text-xs">© 2024 Ángel de Fuego. Todos los derechos reservados.</p>
```

## Cambiar descripción de "Sobre Este Blog"

```jsx
// Líneas 554–557
<p className="text-gray-400 leading-relaxed">
  Exploraciones profundas sobre la naturaleza de la consciencia...
</p>
```

## Actualizar "Próximamente"

```jsx
// Líneas 561–565
<ul className="text-gray-400 space-y-2">
  <li>→ Herramientas de Perfilamiento</li>
  <li>→ Curso de Numerología Digital</li>
  <li>→ API de Análisis Hermético</li>
</ul>
```

## Personalizar stats

Los stats del dashboard se calculan manualmente en la línea 518:

```jsx
{ label: 'Artículos', value: '6' },
{ label: 'Categorías', value: '5' },
{ label: 'Lectura Promedio', value: '10 min' },
{ label: 'Estado', value: 'Activo' }
```

Si agregás posts, actualizá estos valores o implementá cálculo dinámico.
