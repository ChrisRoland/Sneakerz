# Sneakers Product Page

A responsive e-commerce product page built with Vue 3, TypeScript, and Tailwind CSS. Features a modern design with interactive elements, mobile-first responsive layout, and full accessibility support.

![Sneakers Preview](/sneakerz/public/desktop-design.jpg)

## Features

### Core Functionality
- **Product Gallery**: Interactive image carousel with thumbnail navigation
- **Responsive Design**: Mobile-first approach with breakpoints at 375px and 1440px
- **Shopping Cart**: Add/remove items with quantity selector and persistent cart state
- **Lightbox Modal**: Full-screen image viewer for desktop users
- **Mobile Navigation**: Hamburger menu with slide-out navigation

### Interactive Elements
- Hover effects on all interactive components
- Smooth transitions and animations
- Cart item counter with real-time updates
- Image navigation with previous/next controls
- Quantity increment/decrement controls

## Tech Stack

- **Framework**: [Vue 3](https://vuejs.org/) with Composition API
- **Language**: [TypeScript](https://www.typescriptlang.org/)
- **Styling**: [Tailwind CSS](https://tailwindcss.com/)
- **Build Tool**: [Vite](https://vitejs.dev/)
- **Icons**: Custom SVG icons (included in images)

## Project Structure

```
sneakerz/
├── public/
│   └── images/               # Product images and icons
│       ├── icon-*.svg       # UI icons
│       ├── image-product-*.jpg  # Product photos
│       └── logo.svg         # Brand logo
├── src/
│   ├── components/          # Vue components
│   │   ├── AppHeader.vue    # Main navigation header
│   │   ├── CartDropdown.vue # Shopping cart overlay
│   │   ├── LightboxModal.vue # Image lightbox
│   │   ├── MobileMenu.vue   # Mobile navigation menu
│   │   ├── ProductDetails.vue # Product info and purchase
│   │   └── ProductGallery.vue # Image carousel
│   ├── App.vue             # Main application component
│   ├── main.ts             # Application entry point
│   └── style.css           # Global styles and Tailwind imports
├── index.html              # HTML template
├── package.json            # Dependencies and scripts
├── tailwind.config.js      # Tailwind configuration
├── tsconfig.json           # TypeScript configuration
└── vite.config.ts          # Vite configuration
```

## Design System

### Colors
- **Primary Orange**: `hsl(26, 100%, 55%)`
- **Pale Orange**: `hsl(25, 100%, 94%)`
- **Very Dark Blue**: `hsl(220, 13%, 13%)`
- **Dark Grayish Blue**: `hsl(219, 9%, 45%)`
- **Grayish Blue**: `hsl(220, 14%, 75%)`
- **Light Grayish Blue**: `hsl(223, 64%, 98%)`

### Typography
- **Font Family**: [Kumbh Sans](https://fonts.google.com/specimen/Kumbh+Sans)
- **Font Weights**: 400 (Regular), 700 (Bold)
- **Base Font Size**: 16px

## Getting Started

### Prerequisites
- Node.js (v16 or higher)
- npm or yarn package manager

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/sneakers-ecommerce.git
   cd sneakers-ecommerce
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Add product images**
   Place your product images in the `public/images/` directory with the following naming convention:
   - `image-product-1.jpg` through `image-product-4.jpg` (main images)
   - `image-product-1-thumbnail.jpg` through `image-product-4-thumbnail.jpg` (thumbnails)
   - Include all SVG icons as shown in the project structure

4. **Start development server**
   ```bash
   npm run dev
   ```

5. **Open your browser**
   Navigate to `http://localhost:5173`

### Build for Production

```bash
# Build the project
npm run build

# Preview the build
npm run preview
```

## Responsive Behavior

### Mobile
- Hamburger navigation menu
- Full-width image carousel with navigation arrows
- Stacked layout for product details
- Touch-friendly interactive elements

### Desktop
- Horizontal navigation bar
- Grid layout with image gallery and product details side-by-side
- Thumbnail navigation below main image
- Lightbox modal for image viewing
- Hover effects on interactive elements

## Configuration

### Tailwind CSS Customization

The project includes custom Tailwind configuration in `tailwind.config.js`:

```javascript
theme: {
  extend: {
    colors: {
      'primary-orange': 'hsl(26, 100%, 55%)',
      'pale-orange': 'hsl(25, 100%, 94%)',
      // ... other custom colors
    },
    fontFamily: {
      'kumbh': ['Kumbh Sans', 'sans-serif'],
    }
  }
}
```

### TypeScript Configuration

Strict TypeScript configuration with:
- Component prop validation
- Event emission typing
- Interface definitions for cart items and product images

## Component Architecture

### State Management
- **Reactive State**: Vue 3 Composition API with `ref()` and `computed()`
- **Props & Emits**: Strongly typed component communication
- **Local Storage**: Ready for cart persistence (not implemented)

## Key Features Implementation

### Cart Functionality
- Add items with quantity selection
- Remove items from cart
- Real-time cart counter updates
- Automatic cart opening after adding items

### Image Gallery
- Touch/click navigation on mobile
- Thumbnail selection on desktop
- Lightbox modal for enhanced viewing
- Keyboard navigation support

## Future Enhancements

- [ ] Product variants (sizes, colors)
- [ ] Multiple product pages with routing
- [ ] User authentication
- [ ] Checkout process
- [ ] Search and filtering
- [ ] Wishlist functionality

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

**Thanks for checking out this project! <3**