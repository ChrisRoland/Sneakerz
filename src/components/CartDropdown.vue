<template>
  <div
    v-if="isOpen"
    class="fixed inset-0 z-40 md:relative md:inset-auto"
    @click="$emit('close')"
  >
    <div
      class="absolute top-20 md:-top-2 right-4 md:right-6 bg-white rounded-lg shadow-2xl w-80 md:w-96 z-50"
      @click.stop
    >
      <div class="p-6 border-b border-grayish-blue/20">
        <h3 class="font-bold text-very-dark-blue">Cart</h3>
      </div>
      
      <div class="p-6">
        <div v-if="cartItems.length === 0" class="text-center py-12">
          <p class="text-dark-grayish-blue font-bold">Your cart is empty.</p>
        </div>
        
        <div v-else class="space-y-4">
          <div
            v-for="item in cartItems"
            :key="item.id"
            class="flex items-center space-x-4"
          >
            <img :src="item.image" :alt="item.name" class="w-12 h-12 rounded object-cover" />
            <div class="flex-1">
              <p class="text-dark-grayish-blue">{{ item.name }}</p>
              <p class="text-dark-grayish-blue">
                ${{ item.price.toFixed(2) }} x {{ item.quantity }}
                <span class="font-bold text-very-dark-blue ml-2">
                  ${{ (item.price * item.quantity).toFixed(2) }}
                </span>
              </p>
            </div>
            <button
              @click="$emit('removeItem', item.id)"
              class="p-2 hover:bg-gray-100 rounded"
              aria-label="Remove item"
            >
              <img src="/images/icon-delete.svg" alt="Delete" class="w-4 h-4" />
            </button>
          </div>
          
          <button 
          @click="$emit('close')"
          class="w-full bg-primary-orange text-white font-bold py-4 rounded-lg hover:bg-primary-orange/80 transition-colors">
            Checkout
          </button>
        </div>
      </div>
    </div>
  </div>
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
  isOpen: boolean
  cartItems: CartItem[]
}

defineProps<Props>()
defineEmits<{
  close: []
  removeItem: [id: string]
}>()
</script>