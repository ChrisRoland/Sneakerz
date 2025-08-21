<template>
  <header class="">
    <div class="max-w-7xl mx-auto px-4 md:px-0 md:pt-2 md:pb-5 border-b border-grayish-blue/50">
      <div class="flex items-center justify-between h-16 md:h-20">
        <!-- Mobile menu button and logo -->
        <div class="flex items-center">
          <button
            @click="$emit('toggleMobileMenu')"
            class="md:hidden p-2 mr-4"
            aria-label="Toggle menu"
          >
            <img src="/images/icon-menu.svg" alt="Menu" class="w-5 h-5" />
          </button>
          
          <div class="">
            <img src="/images/logo.svg" alt="sneakers" class="h-6" />
          </div>

          <!-- Desktop Navigation -->
          <nav class="hidden md:flex items-center space-x-8 ml-20">
            <a href="#" class="text-dark-grayish-blue hover:text-very-dark-blue transition-colors relative group">
              Collections
              <span class="absolute -bottom-12 left-0 right-0 h-1 bg-primary-orange transform scale-x-0 group-hover:scale-x-100 transition-transform"></span>
            </a>
            <a href="#" class="text-dark-grayish-blue hover:text-very-dark-blue transition-colors relative group">
              Men
              <span class="absolute -bottom-12 left-0 right-0 h-1 bg-primary-orange transform scale-x-0 group-hover:scale-x-100 transition-transform"></span>
            </a>
            <a href="#" class="text-dark-grayish-blue hover:text-very-dark-blue transition-colors relative group">
              Women
              <span class="absolute -bottom-12 left-0 right-0 h-1 bg-primary-orange transform scale-x-0 group-hover:scale-x-100 transition-transform"></span>
            </a>
            <a href="#" class="text-dark-grayish-blue hover:text-very-dark-blue transition-colors relative group">
              About
              <span class="absolute -bottom-12 left-0 right-0 h-1 bg-primary-orange transform scale-x-0 group-hover:scale-x-100 transition-transform"></span>
            </a>
            <a href="#" class="text-dark-grayish-blue hover:text-very-dark-blue transition-colors relative group">
              Contact
              <span class="absolute -bottom-12 left-0 right-0 h-1 bg-primary-orange transform scale-x-0 group-hover:scale-x-100 transition-transform"></span>
            </a>
          </nav>
        </div>


        <!-- Cart and Profile -->
        <div class="flex items-center space-x-4 md:space-x-6">
          <button
            @click="$emit('toggleCart')"
            class="relative p-2 transition-opacity"
            aria-label="Shopping cart"
          >
            <img src="/images/icon-cart.svg" alt="Cart" class="w-6 h-6 opacity-75 hover:opacity-100" />
            <span
            v-for="item in cartItems"
            :key="item.id"
              v-if="cartItemCount > 0"
              class="absolute -top-1 -right-1 bg-primary-orange text-white text-xs rounded-full w-5 h-5 flex items-center justify-center font-bold"
            >
              <!-- {{ cartItemCount }} -->
              {{ item.quantity }}
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
interface CartItem {
  id: string
  name: string
  price: number
  quantity: number
  image: string
}

interface Props {
  cartItemCount: number
  cartItems: CartItem[]
}

defineProps<Props>()
defineEmits<{
  toggleMobileMenu: []
  toggleCart: []
}>()
</script>