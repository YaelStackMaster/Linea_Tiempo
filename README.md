# Vue Carousel con Tailwind CSS

Un carrusel moderno y elegante construido con Vue.js 3 y Tailwind CSS, optimizado para despliegue en Vercel.

## Características

- ✨ **Vue.js 3** - Framework moderno y reactivo
- 🎨 **Tailwind CSS** - Estilos utilitarios y responsive
- 📱 **Diseño Responsivo** - Se adapta a todos los dispositivos
- 🎭 **Animaciones Suaves** - Transiciones fluidas y efectos visuales
- ⌨️ **Navegación por Teclado** - Flechas izquierda/derecha
- 🔄 **Autoplay** - Reproducción automática opcional
- 🎯 **Indicadores de Puntos** - Navegación directa a slides
- 🚀 **Optimizado para Vercel** - Despliegue rápido y eficiente

## Instalación

1. Instala las dependencias:
```bash
npm install
```

2. Ejecuta el servidor de desarrollo:
```bash
npm run dev
```

3. Abre [http://localhost:3000](http://localhost:3000) en tu navegador.

## Construcción para Producción

```bash
npm run build
```

## Despliegue en Vercel

1. Sube tu código a GitHub
2. Conecta tu repositorio en [Vercel](https://vercel.com)
3. Vercel detectará automáticamente que es un proyecto Vue.js
4. ¡Tu carrusel estará listo en minutos!

## Personalización

### Cambiar Slides

Edita el array `slides` en `src/components/Carousel.vue`:

```javascript
slides: [
  {
    title: 'Tu Título',
    description: 'Tu descripción',
    image: 'URL_de_tu_imagen',
    buttonText: 'Texto del Botón'
  }
  // ... más slides
]
```

### Modificar Estilos

Los estilos están basados en Tailwind CSS. Puedes modificar las clases en los componentes o agregar estilos personalizados en `src/style.css`.

### Configurar Autoplay

Cambia el intervalo de autoplay en el método `startAutoplay()`:

```javascript
this.autoplayInterval = setInterval(() => {
  this.nextSlide()
}, 3000) // 3 segundos
```

## Tecnologías Utilizadas

- **Vue.js 3** - Framework de JavaScript progresivo
- **Vite** - Herramienta de construcción rápida
- **Tailwind CSS** - Framework CSS utilitario
- **PostCSS** - Procesador CSS
- **Autoprefixer** - Prefijos CSS automáticos

## Estructura del Proyecto

```
vue-carousel/
├── src/
│   ├── components/
│   │   └── Carousel.vue
│   ├── App.vue
│   ├── main.js
│   └── style.css
├── index.html
├── package.json
├── vite.config.js
├── tailwind.config.js
├── postcss.config.js
├── vercel.json
└── README.md
```

## Licencia

MIT

