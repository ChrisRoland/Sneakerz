<template>
  <div
    v-if="isOpen"
    class="fixed inset-0 bg-black/75 z-50 flex items-center justify-center p-4"
    @click="$emit('close')"
  >
    <div class="max-w-lg w-full" @click.stop>
      <div class="flex justify-end mb-4">
        <button
          @click="$emit('close')"
          class="transition-colors"
          aria-label="Close lightbox"
        >
          <div
            class="w-5 h-5 bg-white hover:bg-[#ff7d1a] transition-colors duration-200"
            style="
              mask: url('/images/icon-close.svg') no-repeat center;
              mask-size: contain;
            "
          ></div>
        </button>
      </div>

      <div class="relative">
        <img
          :src="currentImage"
          alt="Fall Limited Edition Sneakers"
          class="w-full rounded-lg"
        />

        <button
          @click="$emit('previousIcon')"
          class="absolute -left-4 top-1/2 -translate-y-1/2 bg-white rounded-full py-3 px-3.5 shadow-lg hover:bg-gray-50 transition-colors"
          aria-label="Previous icon"
        >
          <div
            class="w-3 h-4 bg-black hover:bg-[#ff7d1a] transition-colors duration-200"
            style="
              mask: url('/images/icon-previous.svg') no-repeat center;
              mask-size: contain;
            "
          ></div>
        </button>
        <button
          @click="$emit('nextIcon')"
          class="absolute -right-4 top-1/2 -translate-y-1/2 bg-white rounded-full py-3 px-3.5 shadow-lg hover:bg-gray-50 transition-colors"
          aria-label="Next icon"
        >
          <div
            class="w-3 h-4 bg-black hover:bg-[#ff7d1a] transition-colors duration-200"
            style="
              mask: url('/images/icon-next.svg') no-repeat center;
              mask-size: contain;
            "
          ></div>
        </button>
      </div>

      <div class="grid grid-cols-4 gap-4 mt-6">
        <button
          v-for="(image, index) in productImages"
          :key="index"
          @click="$emit('setCurrentImage', index)"
          class="aspect-square rounded-lg overflow-hidden border-2 transition-all bg-white"
          :class="
            currentImageIndex === index
              ? 'border-primary-orange'
              : 'border-none'
          "
        >
          <img
            :src="image.thumbnail"
            :alt="`Product view ${index + 1}`"
            class="w-full h-full object-cover"
            :class="
              currentImageIndex === index
                ? 'border-primary-orange opacity-55'
                : 'border-none hover:opacity-75'
            "
          />
        </button>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
interface ProductImage {
  full: string;
  thumbnail: string;
}

interface Props {
  isOpen: boolean;
  productImages: ProductImage[];
  currentImage: string;
  currentImageIndex: number;
}

defineProps<Props>();
defineEmits<{
  close: [];
  previousIcon: [];
  nextIcon: [];
  setCurrentImage: [index: number];
}>();
</script>
