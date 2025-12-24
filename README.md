# IndoreMart - Local Marketplace for Indore

IndoreMart is a full-stack e-commerce platform connecting local vendors and customers in Indore. Built with the MERN stack (MongoDB concept with in-memory storage for this demo, Express, React, Node.js).

## Payment Gateway Integration

This project includes Razorpay payment gateway integration for secure online payments. To enable payments:

1. Create a Razorpay account at https://razorpay.com
2. Get your API keys from the dashboard
3. Set environment variables:
   - `RAZORPAY_KEY_ID`: Your Razorpay Key ID
   - `RAZORPAY_KEY_SECRET`: Your Razorpay Key Secret
4. Update the keys in `server/routes.ts` or use environment variables

## Features

### For Vendors
- Register and create a vendor account with shop details
- Add, edit, and delete products with images, descriptions, and pricing
- Manage product inventory through an intuitive dashboard
- Track products uploaded to the marketplace

### For Customers
- Browse products from local Indore vendors
- Search and filter products by category
- View detailed product information
- Add products to cart with quantity management
- Secure checkout process
- Track order history
- Persistent cart across sessions

### Security & Authentication
- JWT-based authentication
- Separate login flows for vendors and customers
- Password hashing with bcrypt
- Protected routes for vendor and customer-specific features

## Tech Stack

### Frontend
- **React** with TypeScript
- **Wouter** for routing
- **TanStack Query** for data fetching and caching
- **React Hook Form** with Zod validation
- **Shadcn/ui** components with Tailwind CSS
- **Lucide React** icons

### Backend
- **Node.js** with Express
- **TypeScript** for type safety
- **In-memory storage** (MemStorage implementation)
- **JWT** for authentication
- **bcrypt** for password hashing
- **express-validator** for request validation

## Getting Started

### Prerequisites
- Node.js 20+ installed
- npm or yarn package manager

### Installation & Running

1. **Install dependencies**
   ```bash
   npm install
   ```

2. **Start the application**
   ```bash
   npm run dev
   ```

3. **Access the application**
   - Open your browser to `http://localhost:5000`
   - The frontend and backend run on the same port (5000)

## Project Structure

```
├── client/                 # Frontend React application
│   ├── src/
│   │   ├── components/    # Reusable React components
│   │   ├── contexts/      # React contexts (Auth)
│   │   ├── pages/         # Page components
│   │   └── lib/           # Utilities and helpers
│   └── index.html
│
├── server/                 # Backend Express application
│   ├── middleware/        # Express middleware (auth)
│   ├── routes.ts          # API route handlers
│   └── storage.ts         # Data storage interface
│
├── shared/                 # Shared types and schemas
│   └── schema.ts          # Zod schemas and TypeScript types
│
└── README.md
```

## API Endpoints

### Authentication
- `POST /api/auth/signup` - Register new user (vendor or customer)
- `POST /api/auth/login` - Login user

### Products
- `GET /api/products` - Get all products with vendor info
- `GET /api/products/:id` - Get single product details
- `GET /api/vendor/products` - Get vendor's own products (requires vendor auth)
- `POST /api/products` - Create new product (requires vendor auth)
- `PATCH /api/products/:id` - Update product (requires vendor auth)
- `DELETE /api/products/:id` - Delete product (requires vendor auth)

### Cart
- `GET /api/cart` - Get user's cart items (requires customer auth)
- `POST /api/cart` - Add item to cart (requires customer auth)
- `PATCH /api/cart/:id` - Update cart item quantity (requires customer auth)
- `DELETE /api/cart/:id` - Remove item from cart (requires customer auth)

### Orders
- `GET /api/orders` - Get user's order history (requires customer auth)
- `POST /api/orders` - Create new order from cart (requires customer auth)

## User Roles

### Vendor
- Can register with shop name
- Access to vendor dashboard
- Full CRUD operations on their own products
- Cannot access customer features (cart, orders)

### Customer
- Standard user registration
- Browse and search all products
- Shopping cart functionality
- Place and track orders
- Cannot access vendor dashboard

## Design Features

- **Responsive Design**: Works seamlessly on mobile, tablet, and desktop
- **Modern UI**: Clean, professional interface with Poppins and Inter fonts
- **Color Scheme**: Primary green theme representing local marketplace
- **Accessibility**: Proper ARIA labels and keyboard navigation
- **Loading States**: Skeleton screens and loading indicators
- **Error Handling**: User-friendly error messages with toast notifications

## Data Models

### User
- name, email, password (hashed)
- role: 'vendor' or 'customer'
- shopName (for vendors only)

### Product
- name, price, description, category
- imageUrl, location (default: Indore)
- vendorId (reference to vendor)

### Cart Item
- userId, productId, quantity

### Order
- userId, totalPrice, status
- items: array of order items with product references

## Future Enhancements

- Admin dashboard for vendor/product approval
- Image upload with Multer
- Wishlist feature
- Contact us page
- Advanced search and filtering
- Real-time notifications
- Payment gateway integration
- MongoDB Atlas integration for production

## License

This project is open source and available for educational purposes.

## Contributors

Built with ❤️ in Indore
