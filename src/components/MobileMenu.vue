<template>
  <div
    v-if="isOpen"
    class="fixed inset-0 bg-black/75 z-50 md:hidden"
    @click="$emit('close')"
  >
    <nav
      class="bg-white h-full w-64 p-6"
      @click.stop
    >
      <button
        @click="$emit('close')"
        class="mb-8 p-2 -ml-2"
        aria-label="Close menu"
      >
        <img src="/images/icon-close.svg" alt="Close" class="w-5 h-5" />
      </button>
      
      <div class="space-y-6">
        <a href="#" class="block text-lg font-bold text-very-dark-blue">Collections</a>
        <a href="#" class="block text-lg font-bold text-very-dark-blue">Men</a>
        <a href="#" class="block text-lg font-bold text-very-dark-blue">Women</a>
        <a href="#" class="block text-lg font-bold text-very-dark-blue">About</a>
        <a href="#" class="block text-lg font-bold text-very-dark-blue">Contact</a>
      </div>
    </nav>
  </div>
</template>

<script setup lang="ts">
interface Props {
  isOpen: boolean
}

defineProps<Props>()
defineEmits<{
  close: []
}>()
</script>