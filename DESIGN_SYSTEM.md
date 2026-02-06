# ShopHub E-Commerce Design System
## Amazon-Inspired Modern Design

---

## 🎨 Color Palette

### Primary Colors
- **Primary Orange**: `#FF9900` - Main action buttons, highlights
- **Primary Dark**: `#E88B00` - Hover states for primary elements
- **Secondary Navy**: `#232F3E` - Header, footer, navigation
- **Accent Blue**: `#146EB4` - Links, interactive elements

### Status Colors
- **Success Green**: `#10B981` - Success messages, in-stock
- **Warning Yellow**: `#F59E0B` - Warnings, low stock
- **Danger Red**: `#EF4444` - Errors, out of stock
- **Info Blue**: `#3B82F6` - Information messages

### Neutral Colors
- **Background**: `#F3F4F6` (gray-50)
- **Card Background**: `#FFFFFF` (white)
- **Text Primary**: `#111827` (gray-900)
- **Text Secondary**: `#6B7280` (gray-500)
- **Border**: `#D1D5DB` (gray-300)

---

## 📐 Layout Structure

### Header (Amazon-Style)
```
┌─────────────────────────────────────────────────────────┐
│ Logo | Location | Search Bar | Account | Orders | Cart  │
├─────────────────────────────────────────────────────────┤
│ ☰ All | Today's Deals | Customer Service | Registry    │
└─────────────────────────────────────────────────────────┘
```

**Components:**
- Logo (left-aligned)
- Location selector with icon
- Full-width search bar with category dropdown
- Account dropdown
- Orders link
- Cart with badge
- Secondary navigation bar

### Product Listing Layout
```
┌──────────┬────────────────────────────────────────┐
│          │  Sort By: [Dropdown]                   │
│ Filters  ├────────────────────────────────────────┤
│          │  ┌────┐ ┌────┐ ┌────┐                 │
│ Category │  │ P1 │ │ P2 │ │ P3 │                 │
│ Price    │  └────┘ └────┘ └────┘                 │
│ Rating   │  ┌────┐ ┌────┐ ┌────┐                 │
│          │  │ P4 │ │ P5 │ │ P6 │                 │
│          │  └────┘ └────┘ └────┘                 │
└──────────┴────────────────────────────────────────┘
```

---

## 🎯 Component Specifications

### 1. Product Card
```html
<div class="bg-white p-4 rounded shadow-sm hover:shadow-md">
  <img> <!-- 300x300px -->
  <h3> <!-- Product title (2 lines max) -->
  <div> <!-- Rating stars + count -->
  <div> <!-- Price (large) + strikethrough -->
  <p> <!-- Delivery info -->
  <span> <!-- Badge (Deal/Best Seller) -->
</div>
```

**Features:**
- White background
- Subtle shadow that lifts on hover
- Product image (square, 300x300px)
- Title truncated to 2 lines
- Star rating with review count
- Large price display
- Delivery information
- Status badges (Deal, Best Seller, etc.)

### 2. Search Bar
```html
<div class="flex">
  <select> <!-- Category dropdown -->
  <input> <!-- Search input -->
  <button> <!-- Search button (orange) -->
</div>
```

### 3. Filter Sidebar
```html
<aside class="w-64">
  <div class="bg-white p-4">
    <h3>Department</h3>
    <label><input type="checkbox"> Category</label>
    
    <h3>Price</h3>
    <label><input type="radio"> Price Range</label>
    
    <h3>Customer Review</h3>
    <div>★★★★★ & Up</div>
  </div>
</aside>
```

### 4. Navigation Links
- Hover effect: White border
- Padding: `px-2 py-1`
- Font size: `text-sm`
- Transition: All 200ms

---

## 📱 Responsive Breakpoints

```css
Mobile:  < 768px  (1 column)
Tablet:  768px - 1024px (2 columns)
Desktop: > 1024px (3-4 columns)
```

---

## 🎭 Typography

### Font Family
```css
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Helvetica', 'Arial', sans-serif;
```

### Font Sizes
- **Heading 1**: `text-2xl` (24px) - Page titles
- **Heading 2**: `text-xl` (20px) - Section titles
- **Heading 3**: `text-lg` (18px) - Card titles
- **Body**: `text-base` (16px) - Regular text
- **Small**: `text-sm` (14px) - Secondary text
- **Extra Small**: `text-xs` (12px) - Labels, badges

### Font Weights
- **Bold**: `font-bold` (700) - Headings, prices
- **Semibold**: `font-semibold` (600) - Subheadings
- **Medium**: `font-medium` (500) - Links
- **Normal**: `font-normal` (400) - Body text

---

## 🎨 Design Patterns

### Product Price Display
```html
<div class="flex items-baseline gap-2">
  <span class="text-2xl font-bold">$129<sup class="text-sm">.99</sup></span>
  <span class="text-sm text-gray-500 line-through">$199.99</span>
</div>
```

### Star Rating
```html
<div class="flex items-center gap-2">
  <span class="text-primary">★★★★★</span>
  <span class="text-sm text-accent">128</span>
</div>
```

### Delivery Info
```html
<p class="text-xs text-gray-600">
  FREE delivery <span class="font-bold">Tomorrow</span>
</p>
```

### Status Badges
```html
<!-- Deal Badge -->
<span class="bg-red-600 text-white text-xs px-2 py-1 rounded">
  Save 35%
</span>

<!-- Best Seller -->
<span class="bg-green-700 text-white text-xs px-2 py-1 rounded">
  Best Seller
</span>

<!-- Amazon's Choice -->
<span class="bg-primary text-white text-xs px-2 py-1 rounded">
  Amazon's Choice
</span>
```

---

## 🔘 Button Styles

### Primary Button
```html
<button class="bg-primary hover:bg-primary-dark text-white px-6 py-2 rounded transition-colors duration-200">
  Add to Cart
</button>
```

### Secondary Button
```html
<button class="border border-gray-300 hover:bg-gray-100 px-6 py-2 rounded transition-colors duration-200">
  Add to List
</button>
```

### Link Button
```html
<a class="text-accent hover:text-primary-dark hover:underline">
  See more
</a>
```

---

## 📦 Page Templates

### All Pages Must Include:

1. **Header** (Amazon-style)
   - Logo
   - Location selector
   - Search bar
   - Account menu
   - Orders link
   - Cart with badge
   - Navigation bar

2. **Main Content Area**
   - Max width: `max-w-7xl`
   - Padding: `px-4 py-4`
   - Background: `bg-gray-50`

3. **Footer** (Amazon-style)
   - "Back to top" button
   - 4-column link grid
   - Copyright notice

---

## 🎯 Page-Specific Guidelines

### Homepage
- Hero banner with deals
- Category cards (4 columns)
- Featured products grid
- Promotional banners

### Product Listing
- Left sidebar filters (fixed width: 256px)
- Product grid (responsive columns)
- Sort dropdown (top right)
- Pagination (bottom center)

### Product Detail
- Large image gallery (left)
- Product info (right)
- "Add to Cart" button (prominent, orange)
- Delivery information
- Product description tabs
- Related products carousel

### Cart
- Item list with thumbnails
- Quantity selectors
- Remove buttons
- Subtotal (right sidebar)
- Proceed to checkout (orange button)

### Checkout
- Multi-step process
- Address form
- Payment method
- Order review
- Place order button

---

## ✨ Animation Guidelines

### Hover Effects
```css
/* Cards */
hover:shadow-md transition-shadow duration-200

/* Buttons */
hover:bg-primary-dark transition-colors duration-200

/* Links */
hover:underline hover:text-accent

/* Images */
hover:scale-105 transition-transform duration-300
```

### Loading States
- Skeleton screens for content loading
- Spinner for button actions
- Progress bar for multi-step processes

---

## 📋 Checklist for Each Page

- [ ] Amazon-style header with all components
- [ ] Proper color scheme (orange primary, navy secondary)
- [ ] Responsive layout (mobile, tablet, desktop)
- [ ] Hover effects on interactive elements
- [ ] Proper typography hierarchy
- [ ] Consistent spacing (Tailwind spacing scale)
- [ ] Amazon-style footer
- [ ] Accessibility (ARIA labels, keyboard navigation)
- [ ] Loading states
- [ ] Error states

---

## 🚀 Implementation Status

### ✅ Completed Pages
1. **index.html** - Homepage (Tailwind + animations)
2. **products.html** - Product listing (Amazon-style)
3. **admin-dashboard.html** - Admin dashboard
4. **admin-products.html** - Product management
5. **admin-orders.html** - Order management

### ⏳ Needs Amazon-Style Conversion
1. **product-detail.html** - Product details page
2. **cart.html** - Shopping cart
3. **checkout.html** - Checkout process
4. **login.html** - Login page
5. **register.html** - Registration page
6. **profile.html** - User profile
7. **order-confirmation.html** - Order success
8. **order-tracking.html** - Track orders
9. **categories.html** - Category browser
10. **about.html** - About page
11. **contact.html** - Contact page
12. **forgot-password.html** - Password reset

---

## 📝 Notes

- All pages use Tailwind CSS CDN
- No custom CSS file needed
- Responsive by default
- Amazon-inspired but unique branding
- Focus on usability and conversion
- Clean, professional appearance

---

**Last Updated**: February 5, 2026
**Version**: 2.0.0 (Amazon-Inspired Design)
