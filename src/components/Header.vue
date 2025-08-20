<template>
  <header class="border-b border-grayish-blue/20">
    <div class="max-w-7xl mx-auto px-4 md:px-6">
      <div class="flex items-center justify-between h-16 md:h-20">
        <!-- Mobile menu button and logo -->
        <div class="flex items-center space-x-4">
          <button
            @click="$emit('toggleMobileMenu')"
            class="md:hidden p-2 -ml-2"
            aria-label="Toggle menu"
          >
            <img src="/images/icon-menu.svg" alt="Menu" class="w-5 h-5" />
          </button>
          
          <h1 class="text-2xl md:text-3xl font-bold text-very-dark-blue">
            <img src="/images/logo.svg" alt="sneakers" class="h-6" />
          </h1>
        </div>

        <!-- Desktop Navigation -->
        <nav class="hidden md:flex items-center space-x-8 ml-12">
          <a href="#" class="text-dark-grayish-blue hover:text-very-dark-blue transition-colors relative group">
            Collections
            <span class="absolute -bottom-6 left-0 right-0 h-1 bg-primary-orange transform scale-x-0 group-hover:scale-x-100 transition-transform"></span>
          </a>
          <a href="#" class="text-dark-grayish-blue hover:text-very-dark-blue transition-colors relative group">
            Men
            <span class="absolute -bottom-6 left-0 right-0 h-1 bg-primary-orange transform scale-x-0 group-hover:scale-x-100 transition-transform"></span>
          </a>
          <a href="#" class="text-dark-grayish-blue hover:text-very-dark-blue transition-colors relative group">
            Women
            <span class="absolute -bottom-6 left-0 right-0 h-1 bg-primary-orange transform scale-x-0 group-hover:scale-x-100 transition-transform"></span>
          </a>
          <a href="#" class="text-dark-grayish-blue hover:text-very-dark-blue transition-colors relative group">
            About
            <span class="absolute -bottom-6 left-0 right-0 h-1 bg-primary-orange transform scale-x-0 group-hover:scale-x-100 transition-transform"></span>
          </a>
          <a href="#" class="text-dark-grayish-blue hover:text-very-dark-blue transition-colors relative group">
            Contact
            <span class="absolute -bottom-6 left-0 right-0 h-1 bg-primary-orange transform scale-x-0 group-hover:scale-x-100 transition-transform"></span>
          </a>
        </nav>

        <!-- Cart and Profile -->
        <div class="flex items-center space-x-4 md:space-x-6">
          <button
            @click="$emit('toggleCart')"
            class="relative p-2 hover:opacity-75 transition-opacity"
            aria-label="Shopping cart"
          >
            <img src="/images/icon-cart.svg" alt="Cart" class="w-6 h-6" />
            <span
              v-if="cartItemCount > 0"
              class="absolute -top-1 -right-1 bg-primary-orange text-white text-xs rounded-full w-5 h-5 flex items-center justify-center font-bold"
            >
              {{ cartItemCount }}
            </span>
          </button>
          
          <div class="w-8 h-8 md:w-10 md:h-10 rounded-full overflow-hidden border-2 border-transparent hover:border-primary-orange transition-colors cursor-pointer">
            <img src="/images/image-avatar.png" alt="Profile" class="w-full h-full object-cover" />
          </div>
        </div>
      </div>
    </div>
  </header>
</template>

<script setup lang="ts">
interface Props {
  cartItemCount: number
}

defineProps<Props>()
defineEmits<{
  toggleMobileMenu: []
  toggleCart: []
}>()
</script>