<template>
  <div class="space-y-10 pt-0 p-6 md:p-16 flex flex-col justify-center">
    <div>
      <p
        class="text-dark-grayish-blue font-bold text-sm uppercase tracking-wide mb-5"
      >
        Sneaker Company
      </p>
      <h2
        class="text-3xl md:text-4xl lg:text-5xl font-bold text-very-dark-blue mb-6"
      >
        Fall Limited Edition Sneakers
      </h2>
      <p class="text-dark-grayish-blue leading-relaxed">
        These low-profile sneakers are your perfect casual wear companion.
        Featuring a durable rubber outer sole, they’ll withstand everything the
        weather can offer.
      </p>
    </div>

    <!-- Pricing -->
    <div
      class="space-y-2 max-sm:flex max-sm:items-center max-sm:justify-between"
    >
      <div class="flex items-center space-x-4">
        <span class="text-3xl font-bold text-very-dark-blue">$125.00</span>
        <span
          class="bg-very-dark-blue text-light-grayish-blue font-bold px-2 py-1 rounded text-sm"
        >
          50%
        </span>
      </div>
      <p class="text-dark-grayish-blue font-bold line-through">$250.00</p>
    </div>

    <!-- Add to Cart Section -->
    <div class="space-y-4 md:flex md:space-y-0 md:space-x-4">
      <!-- Quantity Selector -->
      <div class="flex items-center bg-light-grayish-blue rounded-lg md:w-40">
        <button
          @click="$emit('decrementQuantity')"
          class="py-6 px-4 hover:bg-gray-200 hover:opacity-75 transition-colors rounded-l-lg"
          aria-label="Decrease quantity"
        >
          <img src="/images/icon-minus.svg" alt="Minus" class="w-3 h-1" />
        </button>
        <span class="flex-1 text-center font-bold text-very-dark-blue">
          {{ quantity }}
        </span>
        <button
          @click="$emit('incrementQuantity')"
          class="py-5 px-4 hover:bg-gray-200 hover:opacity-75 transition-colors rounded-r-lg"
          aria-label="Increase quantity"
        >
          <img src="/images/icon-plus.svg" alt="Plus" class="w-3 h-3" />
        </button>
      </div>

      <!-- Add to Cart Button -->
      <button
        @click="$emit('addToCart')"
        class="flex-1 max-sm:w-full bg-primary-orange text-very-dark-blue font-bold py-4 px-6 rounded-lg hover:opacity-75 transition-opacity flex items-center justify-center space-x-3 shadow-lg hover:shadow-xl"
      >
        <img
          src="/images/icon-cart.svg"
          alt="Cart"
          class="w-5 h-5 brightness-0"
        />
        <span>Add to cart</span>
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
interface Props {
  quantity: number;
}

defineProps<Props>();
defineEmits<{
  decrementQuantity: [];
  incrementQuantity: [];
  addToCart: [];
}>();
</script>
