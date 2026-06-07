# Guía de uso

## Navegación

El blog está disponible en la ruta `/blog`. Abrite en:

```
http://localhost:5173/blog     (desarrollo)
https://tusitio.com/blog       (producción)
```

## Pantalla principal (lista de artículos)

Al entrar al blog ves:

1. **Header** — Título del blog y descripción
2. **Búsqueda** — Campo de texto para filtrar artículos
3. **Stats Dashboard** — 4 indicadores:
   - Total de artículos publicados
   - Cantidad de categorías únicas
   - Tiempo promedio de lectura
   - Estado del blog (Activo)
4. **Grilla de artículos** — Tarjetas con gradient, categoría, título, extracto, fecha y tiempo de lectura

## Buscar artículos

Escribí en el campo de búsqueda para filtrar por:

- **Título** del artículo
- **Categoría**

La búsqueda es en tiempo real (filtra mientras escribís). Si no hay resultados, se muestra un mensaje "No se encontraron artículos".

## Leer un artículo

Hacé click en cualquier tarjeta para abrir la vista detalle:

- **Header visual** — Gradient de color que representa el artículo
- **Metadata** — Categoría, fecha formateada y tiempo de lectura
- **Título completo**
- **Contenido** con formato:
  - `## Subtítulos` → encabezados
  - `- Listas` → items
  - `**Negrita**` → énfasis
  - Párrafos normales

Usá el botón **← Volver** para regresar a la lista.

## Secciones adicionales

En la vista lista, al final hay:

- **Sobre Este Blog** — Descripción del proyecto
- **Próximamente** — Funcionalidades futuras

## Footer

En todas las vistas:

- Información del autor
- Enlaces (App Hermética, Servicios, Contacto)
- Redes sociales (X/Twitter, Instagram, YouTube)
- Frase de cierre

## Responsive

El blog se adapta automáticamente:

| Dispositivo | Columnas de grilla |
|---|---|
| Mobile (≥360px) | 1 columna |
| Tablet (≥768px) | 2 columnas |
| Desktop (≥1024px) | 2 columnas |

Los stats se muestran en 2 columnas en mobile y 4 en desktop.
