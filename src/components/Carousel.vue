<template>
  <div class="max-w-4xl mx-auto px-2 sm:px-4 lg:px-8">
    <!-- Carrusel Container -->
    <div class="relative bg-white rounded-2xl sm:rounded-3xl shadow-2xl sm:shadow-3xl overflow-hidden">
      <!-- Slides Container -->
      <div 
        class="flex transition-transform duration-800 ease-out"
        :style="{ transform: `translateX(-${currentIndex * 100}%)` }"
      >
        <div 
          v-for="(slide, index) in slides" 
          :key="index"
          class="w-full flex-shrink-0 relative"
        >
          <div class="aspect-[3/4] sm:aspect-[4/3] lg:aspect-video relative overflow-hidden">
            <img 
              :src="slide.image" 
              :alt="slide.title"
              class="w-full h-full object-cover"
            />
            <div class="absolute inset-0 bg-gradient-to-t from-black via-black/20 to-black/40"></div>
            <div class="absolute inset-0 flex items-end sm:items-center justify-center p-6 sm:p-8 lg:p-12">
              <div class="text-center text-white max-w-3xl w-full">
                <h2 class="text-3xl sm:text-4xl lg:text-5xl xl:text-6xl font-bold mb-3 sm:mb-6 animate-fade-in leading-tight">
                  {{ slide.title }}
                </h2>
                <p class="text-base sm:text-lg lg:text-xl xl:text-2xl mb-6 sm:mb-8 animate-fade-in leading-relaxed opacity-90">
                  {{ slide.description }}
                </p>
                <button 
                  v-if="slide.buttonText"
                  class="bg-white text-gray-900 px-6 sm:px-8 lg:px-10 py-3 sm:py-4 rounded-full font-bold hover:bg-gray-100 transition-all duration-300 animate-fade-in text-sm sm:text-base lg:text-lg shadow-lg hover:shadow-xl transform hover:scale-105"
                >
                  {{ slide.buttonText }}
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Dots Indicator - Enhanced Responsive -->
      <div class="absolute bottom-4 sm:bottom-8 left-1/2 transform -translate-x-1/2 flex space-x-3 sm:space-x-4">
        <button 
          v-for="(slide, index) in slides" 
          :key="index"
          @click="goToSlide(index)"
          class="w-3 h-3 sm:w-4 sm:h-4 rounded-full transition-all duration-300 border-2 border-white/30"
          :class="currentIndex === index ? 'bg-white scale-125 border-white' : 'bg-white/50 hover:bg-white/75 hover:scale-110'"
        ></button>
      </div>

      <!-- Enhanced Progress Bar -->
      <div class="absolute bottom-0 left-0 w-full h-1.5 sm:h-2 bg-white/20">
        <div 
          class="h-full bg-gradient-to-r from-blue-400 to-purple-500 transition-all duration-300 ease-linear rounded-r-full"
          :style="{ width: `${((currentIndex + 1) / slides.length) * 100}%` }"
        ></div>
      </div>

      <!-- Slide Counter - Enhanced -->
      <div class="absolute top-4 right-4 bg-black/20 backdrop-blur-sm text-white px-3 py-1 rounded-full text-sm sm:text-base font-medium">
        {{ currentIndex + 1 }} / {{ slides.length }}
      </div>
    </div>

    <!-- Enhanced Slide Counter Below -->
    <div class="mt-6 sm:mt-8 text-center">
      <div class="inline-flex items-center space-x-2 bg-white/80 backdrop-blur-sm px-4 py-2 rounded-full shadow-lg">
        <span class="text-gray-700 font-semibold text-sm sm:text-base">
          {{ currentIndex + 1 }} de {{ slides.length }}
        </span>
        <div class="w-1 h-1 bg-gray-400 rounded-full"></div>
        <span class="text-gray-500 text-xs sm:text-sm">
          {{ getSlideTitle(currentIndex) }}
        </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Carousel',
  data() {
    return {
      currentIndex: 0,
      autoplayInterval: null,
      slides: [
        {
          title: '1947',
          description: 'Se desarrolla el transistor en los laboratorios Bell, base de la miniaturización y de la futura movilidad.',
          image: '/img/3.png'
        },
        {
          title: '1965',
          description: 'Aparece el concepto de computadora personal portátil en visiones de Gordon Moore y otros pioneros.',
          image: '/img/45.png'
        },
        {
          title: '1973',
          description: 'Martin Cooper (Motorola) realiza la primera llamada desde un teléfono móvil.',
          image: '/img/image.png'
        },
        {
          title: '1983',
          description: 'Sale al mercado el Motorola DynaTAC 8000X, primer celular comercial.',
          image: '/img/1947.png'
        },
        {
          title: '1989',
          description: 'Se presenta la Grid Compass 1101, considerada la primera laptop moderna usada incluso por la NASA.',
          image: 'https://images.unsplash.com/photo-1517336714731-489689fd1ca8?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2026&q=80'
        },
        {
          title: '1992',
          description: 'IBM lanza el Simon Personal Communicator, considerado el primer smartphone (llamadas, correo, agenda, juegos).',
          image: 'https://images.unsplash.com/photo-1511707171634-5f897ff02aa9?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2080&q=80'
        },
        {
          title: '1996',
          description: 'Nokia presenta el Nokia 9000 Communicator, con funciones de fax, email y navegación básica.',
          image: 'https://images.unsplash.com/photo-1511707171634-5f897ff02aa9?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2080&q=80'
        },
        {
          title: '1999',
          description: 'Aparecen los primeros teléfonos con conexión a Internet móvil (Nokia 7110 con WAP).',
          image: 'https://images.unsplash.com/photo-1511707171634-5f897ff02aa9?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2080&q=80'
        },
        {
          title: '2000',
          description: 'Se expande el uso de BlackBerry, pionero en correo electrónico móvil empresarial.',
          image: 'https://images.unsplash.com/photo-1511707171634-5f897ff02aa9?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2080&q=80'
        },
        {
          title: '2007',
          description: 'Apple revoluciona la industria con el iPhone, introduciendo pantalla táctil capacitiva y App Store.',
          image: 'https://images.unsplash.com/photo-1511707171634-5f897ff02aa9?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2080&q=80'
        },
        {
          title: '2008',
          description: 'Google lanza Android, sistema operativo abierto que se convierte en el más usado del mundo.',
          image: 'https://images.unsplash.com/photo-1511707171634-5f897ff02aa9?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2080&q=80'
        },
        {
          title: '2010',
          description: 'Se popularizan las tabletas con el lanzamiento del iPad de Apple.',
          image: 'https://images.unsplash.com/photo-1517336714731-489689fd1ca8?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2026&q=80'
        },
        {
          title: '2015',
          description: 'La computación móvil supera a la de escritorio en acceso a Internet global.',
          image: 'https://images.unsplash.com/photo-1511707171634-5f897ff02aa9?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2080&q=80'
        },
        {
          title: '2020',
          description: 'Despliegue masivo de 5G, impulsando IoT, realidad aumentada y computación en la nube móvil.',
          image: 'https://images.unsplash.com/photo-1511707171634-5f897ff02aa9?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2080&q=80'
        },
        {
          title: '2023-2025',
          description: 'Avances en inteligencia artificial integrada en dispositivos móviles, smartphones plegables y ecosistemas multiplataforma.',
          image: 'https://images.unsplash.com/photo-1511707171634-5f897ff02aa9?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2080&q=80'
        }
      ]
    }
  },
  methods: {
    nextSlide() {
      if (this.currentIndex < this.slides.length - 1) {
        this.currentIndex++
      } else {
        this.currentIndex = 0
      }
    },
    goToSlide(index) {
      this.currentIndex = index
      this.resetAutoplay()
    },
    startAutoplay() {
      this.autoplayInterval = setInterval(() => {
        this.nextSlide()
      }, 6000) // 6 segundos por slide para dar más tiempo a leer
    },
    stopAutoplay() {
      if (this.autoplayInterval) {
        clearInterval(this.autoplayInterval)
        this.autoplayInterval = null
      }
    },
    resetAutoplay() {
      this.stopAutoplay()
      this.startAutoplay()
    },
    getSlideTitle(index) {
      const titles = [
        'Transistor', 'Computadora Portátil', 'Primera Llamada', 'Primer Celular',
        'Primera Laptop', 'Primer Smartphone', 'Nokia Communicator', 'Internet Móvil',
        'BlackBerry', 'iPhone', 'Android', 'iPad', 'Móvil Domina', '5G', 'IA Móvil'
      ]
      return titles[index] || ''
    },
    handleSwipe(startX, endX) {
      const swipeThreshold = 50
      const diff = startX - endX

      if (Math.abs(diff) > swipeThreshold) {
        if (diff > 0) {
          // Swipe left - next slide
          this.nextSlide()
        } else {
          // Swipe right - previous slide
          this.currentIndex = this.currentIndex > 0 ? this.currentIndex - 1 : this.slides.length - 1
        }
        this.resetAutoplay()
      }
    }
  },
  mounted() {
    // Iniciar autoplay automáticamente
    this.startAutoplay()
    
    // Pausar autoplay cuando la ventana no está visible
    document.addEventListener('visibilitychange', () => {
      if (document.hidden) {
        this.stopAutoplay()
      } else {
        this.startAutoplay()
      }
    })

    // Pausar autoplay cuando el usuario interactúa con el carrusel
    const carousel = document.querySelector('.max-w-4xl')
    if (carousel) {
      carousel.addEventListener('mouseenter', () => {
        this.stopAutoplay()
      })
      
      carousel.addEventListener('mouseleave', () => {
        this.startAutoplay()
      })

      // Touch events para móviles
      carousel.addEventListener('touchstart', () => {
        this.stopAutoplay()
      })
      
      carousel.addEventListener('touchend', () => {
        setTimeout(() => {
          this.startAutoplay()
        }, 2000)
      })

      // Swipe gestures para móviles
      let startX = 0
      let endX = 0

      carousel.addEventListener('touchstart', (e) => {
        startX = e.touches[0].clientX
      })

      carousel.addEventListener('touchend', (e) => {
        endX = e.changedTouches[0].clientX
        this.handleSwipe(startX, endX)
      })
    }

    // Navegación por teclado (solo en desktop)
    document.addEventListener('keydown', (e) => {
      if (e.key === 'ArrowLeft') {
        this.currentIndex = this.currentIndex > 0 ? this.currentIndex - 1 : this.slides.length - 1
        this.resetAutoplay()
      } else if (e.key === 'ArrowRight') {
        this.nextSlide()
        this.resetAutoplay()
      }
    })
  },
  beforeUnmount() {
    this.stopAutoplay()
    document.removeEventListener('visibilitychange')
    document.removeEventListener('keydown')
  }
}
</script>
