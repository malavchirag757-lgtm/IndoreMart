# IndoreMart Design Guidelines

## Design Approach
**Reference-Based**: Drawing inspiration from modern e-commerce platforms (Etsy, Shopify) and local marketplace aesthetics, adapted for Indore's local vendor ecosystem. The design balances professional polish with local market warmth.

## Core Design Principles
- **Local First**: Celebrate Indore's identity through design elements that feel authentic and trustworthy
- **Vendor Empowerment**: Make vendor tools feel powerful yet approachable
- **Seamless Shopping**: Reduce friction in the customer journey from browse to checkout
- **Visual Hierarchy**: Clear distinction between primary actions (Add to Cart, Checkout) and secondary functions

---

## Typography System

**Font Families** (via Google Fonts CDN):
- Primary: 'Inter' - Clean, modern sans-serif for body text and UI elements
- Headings: 'Poppins' - Slightly rounded, friendly for headlines and product names

**Type Scale**:
- Hero Headline: 48px / Bold (Poppins)
- Page Headers: 36px / Semibold (Poppins)
- Section Titles: 24px / Semibold (Poppins)
- Product Names: 18px / Medium (Poppins)
- Body Text: 16px / Regular (Inter)
- Small Text: 14px / Regular (Inter)
- Button Text: 16px / Medium (Inter)

---

## Layout System

**Spacing Primitives**: Consistent 8px grid system
- Micro spacing: 8px, 16px (buttons, form inputs)
- Component spacing: 24px, 32px (card padding, section gaps)
- Section spacing: 48px, 64px, 80px (vertical rhythm between major sections)

**Container Widths**:
- Max content width: 1280px
- Product grid container: 1200px
- Form containers: 480px
- Dashboard panels: Full width with inner padding

**Grid System**:
- Product Grid: 4 columns (desktop) → 2 columns (tablet) → 1 column (mobile)
- Vendor Dashboard: 3-column layout for product management
- Category Grid: 6 columns (desktop) → 3 columns (tablet) → 2 columns (mobile)

---

## Component Library

### Navigation
**Primary Header** (Fixed on scroll):
- Logo left-aligned with "IndoreMart" wordmark
- Center: Search bar with category dropdown (prominent, 600px wide on desktop)
- Right: Cart icon with badge, User avatar/Login button
- Below: Category navigation bar with 8-10 main categories (horizontal scroll on mobile)
- Height: 120px total (80px main + 40px category bar)

**Vendor Dashboard Navigation**:
- Sidebar navigation (250px wide) with: Dashboard, My Products, Add Product, Orders, Settings
- Collapsible on tablet/mobile to hamburger menu

### Product Cards
**Standard Product Card**:
- Image: 1:1 aspect ratio, 280px × 280px (desktop)
- Vendor badge: Small rounded badge with shop name
- Product name: 2-line truncation with ellipsis
- Price: Large, prominent (20px semibold)
- Rating: Star icons + review count
- Quick "Add to Cart" button on hover (desktop) / always visible (mobile)
- Subtle shadow on hover with scale transform (1.02)

### Forms
**Authentication Forms** (Login/Signup):
- Centered card layout (max-width 480px)
- Large icon/illustration at top (200px height)
- Input fields: Full-width, 48px height, rounded corners (8px)
- Primary button: Full-width, 52px height
- Secondary links below (Register/Login toggle)
- Role selector for signup (Customer/Vendor toggle buttons)

**Product Upload Form** (Vendor):
- Two-column layout (image upload left, details right)
- Image dropzone: 400px × 400px with drag-and-drop
- Input fields: Name, Price, Category (dropdown), Description (textarea)
- Rich text editor for description (simple formatting)
- Location: Pre-filled "Indore" with pin icon

### Shopping Cart
**Cart Sidebar** (Slide-in from right):
- Width: 420px (desktop), full-screen (mobile)
- Product list: Image (80px), name, price, quantity selector, remove button
- Sticky footer: Subtotal, taxes, total, Checkout button
- Empty state: Illustration with "Start Shopping" CTA

**Cart Page** (Full page):
- Left column (60%): Cart items list
- Right column (40%): Order summary card (sticky)
- Continue Shopping link + Clear Cart option

### Order Flow
**Checkout Page**:
- Multi-step progress indicator at top (Delivery → Payment → Review)
- Left: Forms for each step
- Right: Order summary (sticky)
- Large "Place Order" button at bottom
- Trust badges (secure payment, local delivery icons)

### Dashboard Components
**Vendor Dashboard Cards**:
- Statistics cards: Sales, Products, Orders (3-column grid)
- Recent orders table with status badges
- Quick actions: Add Product (prominent CTA)
- Product management table: Edit/Delete actions

---

## Page-Specific Layouts

### Homepage
1. **Hero Section** (600px height):
   - Full-width background image showcasing Indore marketplace/local products
   - Overlay with heading "Indore's Local Marketplace"
   - Subheading: "Support local vendors, shop local products"
   - Large search bar (centered, 700px wide)
   - Browse Categories button
   
2. **Featured Categories** (8 category cards):
   - Icon-based cards in 4-column grid
   - Hover effect with slight lift

3. **Trending Products**:
   - Horizontal scrollable carousel with 8-10 products
   - "View All" link

4. **How It Works** (For Vendors + Customers):
   - 3-column layout with icons
   - Steps: Register → List Products → Start Selling (Vendors)
   - Steps: Browse → Add to Cart → Checkout (Customers)

5. **Local Vendors Spotlight**:
   - Featured vendor cards with shop images
   - 3-column grid

6. **Footer**:
   - 4-column layout: About Indore, Quick Links, Categories, Contact
   - Social media icons
   - Newsletter signup form
   - Copyright with "Made in Indore ❤️"

### Product Details Page
- **Image Gallery** (left, 60%): Main image (600px) with thumbnail strip below
- **Product Info** (right, 40%): Name, price, rating, vendor info card, description, Add to Cart (large button), quantity selector
- **Vendor Info Card**: Shop name, location badge, "View Shop" link
- **Related Products** section below

### Vendor Dashboard
- **Overview cards** at top with key metrics
- **Product management table** with search/filter
- **Quick add product** button (floating action button style)

---

## Interactive Elements

**Buttons**:
- Primary: Solid fill, rounded corners (8px), 48px height, medium font weight
- Secondary: Outline style with 2px border
- Icon buttons: Circular, 40px diameter
- Hover states: Slight darkening + subtle scale (1.05)

**Loading States**:
- Skeleton screens for product cards
- Spinner for form submissions
- Progress bars for image uploads

**Notifications**:
- Toast messages: Top-right corner, slide-in animation
- Success (green accent), Error (red accent), Info (blue accent)
- Auto-dismiss after 4 seconds

**Animations** (Minimal):
- Page transitions: Subtle fade (200ms)
- Cart icon: Bounce when item added
- Product cards: Gentle hover lift
- Modal/sidebar: Slide-in from direction (300ms ease-out)

---

## Images

**Hero Image**:
- Large hero section with marketplace/vendor image
- Description: Vibrant local Indore market scene with colorful stalls, products, or bustling shopping atmosphere
- Treatment: Subtle dark overlay (30% opacity) for text readability
- Buttons on hero: Blurred background (backdrop-filter: blur(10px))

**Product Images**:
- Placeholder service: Use placeholder images for demo products
- Real images: Vendors upload product photos
- All product images: Square aspect ratio, centered, white/neutral background preferred

**Category Icons**:
- Use Heroicons for category representation
- Electronics, Fashion, Home & Kitchen, Books, Sports, Beauty, Food, etc.

**Empty States**:
- Illustration-style graphics for empty cart, no products, no orders
- Light, friendly tone

**Vendor Shop Images**:
- Banner images for vendor profiles (16:9 aspect ratio)
- Shop logo/avatar (circular, 100px)

---

## Accessibility & Polish

- Form labels clearly visible and associated with inputs
- Error messages inline below fields (red text, 14px)
- Focus states: Visible outline (2px, accent color)
- Alt text for all product/vendor images
- Keyboard navigation support throughout
- Loading indicators for async operations
- Empty states with helpful messaging and CTAs

This design creates a professional, trustworthy e-commerce platform that celebrates local Indore vendors while providing modern shopping convenience.