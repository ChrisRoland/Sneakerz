<template>
  <div class="space-y-7 md:mt-10">
    <!-- Main Image -->
    <div class="relative md:px-20">
      <div
        class="aspect-square md:rounded-2xl overflow-hidden cursor-pointer"
        @click="$emit('openLightbox')"
      >
        <img
          :src="currentImage"
          alt="Fall Limited Edition Sneakers"
          class="w-full h-full object-cover"
        />
      </div>
      
      <!-- Mobile Navigation Arrows -->
      <div class="md:hidden">
        <button
          @click="$emit('previousImage')"
          class="absolute left-4 top-1/2 -translate-y-1/2 bg-white rounded-full py-3 px-3.5 shadow-lg hover:bg-gray-50 transition-colors"
          aria-label="Previous image"
        >
          <img src="/images/icon-previous.svg" alt="Previous" class="w-3 h-4" />
        </button>
        <button
          @click="$emit('nextImage')"
          class="absolute right-4 top-1/2 -translate-y-1/2 bg-white rounded-full py-3 px-3.5 shadow-lg hover:bg-gray-50 transition-colors"
          aria-label="Next image"
        >
          <img src="/images/icon-next.svg" alt="Next" class="w-3 h-4" />
        </button>
      </div>
    </div>
    
    <!-- Thumbnail Images (Desktop only) -->
    <div class="hidden md:grid grid-cols-4 gap-4 px-20">
      <button
        v-for="(image, index) in productImages"
        :key="index"
        @click="$emit('setCurrentImage', index)"
        class="aspect-square rounded-lg overflow-hidden border-2 transition-all bg-white"
        :class="currentImageIndex === index 
          ? 'border-primary-orange' 
          : 'border-none'"
      >
        <img
          :src="image.thumbnail"
          :alt="`Product view ${index + 1}`"
          class="w-full h-full object-cover transition-all"
          :class="currentImageIndex === index 
          ? 'border-primary-orange opacity-55' 
          : 'border-none hover:opacity-75'"
        />
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
interface ProductImage {
  full: string
  thumbnail: string
}

interface Props {
  productImages: ProductImage[]
  currentImage: string
  currentImageIndex: number
}

defineProps<Props>()
defineEmits<{
  openLightbox: []
  previousImage: []
  nextImage: []
  setCurrentImage: [index: number]
}>()
</script>