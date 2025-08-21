<template>
  <div class="min-h-screen bg-white font-kumbh">
    <Header 
      :cart-item-count="cartItems.length"
      :cart-items="cartItems"
      @toggle-mobile-menu="toggleMobileMenu"
      @toggle-cart="toggleCart"
    />

    <!-- Mobile Navigation -->
    <MobileMenu 
      :is-open="isMobileMenuOpen"
      @close="closeMobileMenu"
    />

    <!-- Cart Dropdown -->
    <CartDropdown 
      :is-open="isCartOpen"
      :cart-items="cartItems"
      @close="closeCart"
      @remove-item="removeFromCart"
    />

    <!-- Main Content -->
    <main class="max-w-7xl mx-auto px-0 md:px-6 md:py-12">
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 lg:gap-5">
        <!-- Product Images -->
        <ProductGallery 
          :product-images="productImages"
          :current-image="currentImage"
          :current-image-index="currentImageIndex"
          @open-lightbox="openLightbox"
          @previous-image="previousImage"
          @next-image="nextImage"
          @set-current-image="setCurrentImage"
        />

        <!-- Product Details -->
        <ProductDetails 
          :quantity="quantity"
          @decrement-quantity="decrementQuantity"
          @increment-quantity="incrementQuantity"
          @add-to-cart="addToCart"
        />
      </div>
    </main>

    <!-- Lightbox -->
    <LightboxModal 
      :is-open="isLightboxOpen"
      :product-images="productImages"
      :current-image="currentImage"
      :current-image-index="currentImageIndex"
      @close="closeLightbox"
      @previous-image="previousImage"
      @next-image="nextImage"
      @set-current-image="setCurrentImage"
    />
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'
import Header from './components/Header.vue'
import MobileMenu from './components/MobileMenu.vue'
import CartDropdown from './components/CartDropdown.vue'
import ProductGallery from './components/ProductGallery.vue'
import ProductDetails from './components/ProductDetails.vue'
import LightboxModal from './components/LightboxModal.vue'

// Component state
const isMobileMenuOpen = ref(false)
const isCartOpen = ref(false)
const isLightboxOpen = ref(false)
const currentImageIndex = ref(0)
const quantity = ref(0)

// Cart state
interface CartItem {
  id: string
  name: string
  price: number
  quantity: number
  image: string
}

const cartItems = ref<CartItem[]>([])

// Product data
const productImages = [
  {
    full: '/images/image-product-1.jpg',
    thumbnail: '/images/image-product-1-thumbnail.jpg'
  },
  {
    full: '/images/image-product-2.jpg',
    thumbnail: '/images/image-product-2-thumbnail.jpg'
  },
  {
    full: '/images/image-product-3.jpg',
    thumbnail: '/images/image-product-3-thumbnail.jpg'
  },
  {
    full: '/images/image-product-4.jpg',
    thumbnail: '/images/image-product-4-thumbnail.jpg'
  }
]

// Computed properties
const currentImage = computed(() => productImages[currentImageIndex.value]?.full || productImages[0].full)

// Methods
const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const closeMobileMenu = () => {
  isMobileMenuOpen.value = false
}

const toggleCart = () => {
  isCartOpen.value = !isCartOpen.value
}

const closeCart = () => {
  isCartOpen.value = false
}

const openLightbox = () => {
  if (window.innerWidth >= 768) { // Only open on desktop
    isLightboxOpen.value = true
  }
}

const closeLightbox = () => {
  isLightboxOpen.value = false
}

const setCurrentImage = (index: number) => {
  currentImageIndex.value = index
}

const nextImage = () => {
  currentImageIndex.value = (currentImageIndex.value + 1) % productImages.length
}

const previousImage = () => {
  currentImageIndex.value = currentImageIndex.value === 0 
    ? productImages.length - 1 
    : currentImageIndex.value - 1
}

const incrementQuantity = () => {
  quantity.value++
}

const decrementQuantity = () => {
  if (quantity.value > 0) {
    quantity.value--
  }
}

const addToCart = () => {
  if (quantity.value > 0) {
    const existingItem = cartItems.value.find(item => item.id === 'fall-limited-sneakers')
    
    if (existingItem) {
      existingItem.quantity += quantity.value
    } else {
      cartItems.value.push({
        id: 'fall-limited-sneakers',
        name: 'Fall Limited Edition Sneakers',
        price: 125.00,
        quantity: quantity.value,
        image: productImages[0].thumbnail
      })
    }
    
    quantity.value = 0
    // isCartOpen.value = true
  }
}

const removeFromCart = (itemId: string) => {
  const index = cartItems.value.findIndex(item => item.id === itemId)
  if (index > -1) {
    cartItems.value.splice(index, 1)
  }
}
</script>