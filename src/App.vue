<template>
  <div class="min-h-screen bg-gradient-to-br from-blue-50 via-indigo-50 to-purple-50 py-4 sm:py-6 lg:py-12">
    <div class="container mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-6 sm:mb-8 lg:mb-12">
        <h1 class="text-2xl sm:text-3xl lg:text-5xl xl:text-6xl font-bold text-gray-800 mb-2 sm:mb-4 leading-tight">
          Historia de la Computación Móvil
        </h1>
        <p class="text-sm sm:text-base lg:text-xl text-gray-600 max-w-2xl mx-auto">
Un recorrido por las principales fechas de La Historio de la Computacion Movil 
        </p>
      </div>
      
      <Carousel />
    </div>
  </div>
</template>

<script>
import Carousel from './components/Carousel.vue'

export default {
  name: 'App',
  components: {
    Carousel
  }
}
</script>
