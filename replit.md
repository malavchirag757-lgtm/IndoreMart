# IndoreMart - Local Marketplace Platform

## Overview

IndoreMart is a full-stack e-commerce marketplace designed to connect local vendors and customers in Indore. The platform enables vendors to list and manage products while providing customers with a seamless shopping experience including cart management, checkout, and order tracking.

The application is built as a monorepo with a React frontend and Express backend, utilizing TypeScript throughout for type safety. The current implementation uses in-memory storage but is architected with Drizzle ORM schemas to support future PostgreSQL integration.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Framework & Routing**
- React with TypeScript as the primary UI framework
- Wouter for lightweight client-side routing (chosen over React Router for smaller bundle size)
- Component-based architecture with clear separation between pages, shared components, and UI primitives

**State Management & Data Fetching**
- TanStack Query (React Query) for server state management, caching, and data synchronization
- Eliminates need for Redux/MobX by handling async operations declaratively
- Local state via React hooks (useState, useContext) for UI-specific state
- AuthContext provider pattern for authentication state shared across components

**Form Handling & Validation**
- React Hook Form for performant form state management
- Zod schemas for runtime validation (shared between client and server)
- @hookform/resolvers bridges React Hook Form with Zod schemas
- Form validation happens client-side before API calls to improve UX

**UI Component System**
- Shadcn/ui as the component foundation (provides unstyled, accessible primitives)
- Radix UI primitives for complex interactive components (dropdowns, dialogs, tooltips)
- Tailwind CSS for styling with custom design tokens
- Design system defined in tailwind.config.ts with CSS variables for theming
- Custom font system using Google Fonts (Inter for body, Poppins for headings)

**Design Philosophy**
- Reference-based approach inspired by modern e-commerce platforms (Etsy, Shopify)
- 8px grid spacing system for consistency
- Mobile-first responsive design with breakpoints for tablet/desktop
- Accessibility considerations baked into Radix UI primitives

### Backend Architecture

**Framework & Runtime**
- Node.js with Express for HTTP server
- TypeScript for type safety across the entire backend
- ES Modules (type: "module" in package.json) for modern JavaScript features

**Authentication & Authorization**
- JWT-based stateless authentication (no sessions stored server-side)
- Separate token generation for vendors and customers based on role field
- bcrypt for password hashing (10 rounds)
- Middleware pattern for route protection (authenticateToken, requireVendor, requireCustomer)
- Tokens stored in localStorage on client, sent via Authorization header

**API Design**
- RESTful API structure with versioned routes (/api/*)
- Request validation using express-validator
- Zod schemas shared between frontend and backend for consistent validation
- JSON request/response format throughout
- Error handling with appropriate HTTP status codes

**Data Layer Architecture**
- IStorage interface defines contract for all data operations
- MemStorage class implements IStorage using in-memory Map structures
- This abstraction allows swapping storage implementations without changing business logic
- Drizzle ORM schemas defined but not actively used (prepared for database migration)

**Storage Implementation Strategy**
- Current: In-memory storage using JavaScript Maps (demo/development mode)
- Future: PostgreSQL database with Drizzle ORM (schema already defined)
- Five main data entities: Users, Products, CartItems, Orders, OrderItems
- Foreign key relationships maintained in schema definitions

**Development Tools**
- Vite for frontend development server with HMR
- tsx for running TypeScript directly in development
- esbuild for production backend bundling
- Custom logging middleware for request/response tracking

### Data Models

**User Model**
- Supports two roles: 'customer' and 'vendor'
- Vendors have additional shopName field
- Single table for both user types (discriminated by role field)
- Email serves as unique identifier for authentication

**Product Model**
- Belongs to a vendor via foreign key (vendorId)
- Includes pricing (decimal for precision), category, description, imageUrl
- Location field defaults to "Indore" (enforcing local marketplace concept)
- Created timestamp for tracking

**Cart Model**
- User-product association with quantity
- Persistent across sessions (stored server-side, not browser)
- One cart per user with multiple items

**Order Model**
- Captures completed transactions
- Links to user and stores order items in separate table
- Status field for order lifecycle (pending, confirmed, delivered)
- Total price calculated at checkout time

### Route Protection Strategy

**Public Routes**
- Home page (product browsing)
- Product details view
- Login/signup pages

**Customer-Only Routes**
- Shopping cart
- Checkout process
- Order history

**Vendor-Only Routes**
- Dashboard for product management
- Add/edit/delete products

**Implementation**
- Frontend: ProtectedRoute component wraps routes requiring authentication
- Backend: Middleware functions check JWT and user role before allowing access
- Unauthorized requests redirect to login (frontend) or return 401/403 (backend)

### Build & Deployment Architecture

**Development Mode**
- Vite dev server proxies API requests to Express backend
- HMR for instant frontend updates
- tsx watches and restarts backend on changes

**Production Build**
- Frontend: Vite bundles React app into static assets (dist/public)
- Backend: esbuild bundles Express server into dist/index.js
- Single node process serves both static files and API
- Static files served from dist/public via Express in production

**Environment Handling**
- NODE_ENV differentiates development/production
- DATABASE_URL environment variable prepared for PostgreSQL connection
- JWT_SECRET for token signing (defaults provided for development)

## External Dependencies

### Core Framework Dependencies
- **React** (^18.3.1): UI framework
- **Express** (^4.18.2): HTTP server framework
- **TypeScript** (^5.6.2): Type safety across stack
- **Vite** (^5.4.11): Frontend build tool and dev server

### Data Fetching & State
- **@tanstack/react-query** (^5.60.5): Server state management
- **wouter** (^3.3.5): Routing library

### Authentication & Security
- **jsonwebtoken** (^9.0.2): JWT token generation/verification
- **bcrypt** (^6.0.0): Password hashing
- **express-validator** (^7.2.0): Request validation

### UI & Styling
- **Tailwind CSS** (^3.4.1): Utility-first CSS framework
- **Shadcn/ui components**: Collection of Radix UI-based components
- **Radix UI primitives**: Accessible component primitives (@radix-ui/*)
- **lucide-react** (^0.462.0): Icon library
- **class-variance-authority** (^0.7.1): Variant management for components
- **tailwind-merge** (^2.5.4): Intelligent Tailwind class merging

### Form Handling
- **react-hook-form** (^7.54.0): Form state management
- **zod** (^3.23.8): Schema validation
- **@hookform/resolvers** (^3.10.0): Validation resolver bridge

### Database (Prepared, Not Active)
- **drizzle-orm** (^0.38.3): TypeScript ORM
- **@neondatabase/serverless** (^0.10.4): Serverless Postgres driver
- **drizzle-kit** (^0.29.1): Schema migrations tool

### Development Tools
- **tsx** (^4.19.2): TypeScript execution
- **esbuild** (^0.24.0): JavaScript bundler
- **@vitejs/plugin-react** (^4.3.3): React plugin for Vite
- **@replit/vite-plugin-***: Replit-specific development tools

### Utilities
- **date-fns** (^3.6.0): Date formatting and manipulation
- **clsx** (^2.1.1): Conditional className utility
- **nanoid** (^5.0.9): Unique ID generation