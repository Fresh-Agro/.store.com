# Fresh Agro: Technical Workplan & Architecture Design

## 1. System Architecture Overview
A modern, scalable architecture designed for high-concurrency grocery retail.

- **Frontend:** Next.js (App Router) for SEO-optimized product pages and server-side rendering.
- **Backend:** Node.js/Express (Microservices-ready) or Next.js Server Actions for rapid development.
- **Database:** PostgreSQL (Relational data for orders/users) + Redis (Session/Cart caching).
- **Styling:** Tailwind CSS with a mobile-first approach.
- **Infrastructure:** AWS/Vercel with S3 for product image hosting.

---

## 2. Phase 1: Database & API Design (Schema)

```sql
-- Core Database Schema (PostgreSQL)

-- Users & Auth
CREATE TABLE users (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  phone_number VARCHAR(15) UNIQUE NOT NULL,
  full_name VARCHAR(100),
  is_verified BOOLEAN DEFAULT false,
  created_at TIMESTAMP DEFAULT NOW()
);

-- Localization & Zones
CREATE TABLE delivery_zones (
  id SERIAL PRIMARY KEY,
  district VARCHAR(50),
  area VARCHAR(100),
  is_active BOOLEAN DEFAULT true,
  delivery_fee DECIMAL(10, 2) DEFAULT 50.00,
  min_order_for_free_delivery DECIMAL(10, 2) DEFAULT 1500.00
);

-- Catalog
CREATE TABLE products (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  name_en VARCHAR(255),
  name_bn VARCHAR(255),
  category VARCHAR(100),
  base_price DECIMAL(10, 2),
  unit_type VARCHAR(20), -- 'fixed' (pack) or 'weight' (kg/gm)
  stock_quantity DECIMAL(10, 2),
  image_url TEXT
);

-- Orders & Checkout
CREATE TABLE orders (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  user_id UUID REFERENCES users(id),
  total_amount DECIMAL(10, 2),
  delivery_fee DECIMAL(10, 2),
  delivery_slot TIMESTAMP,
  payment_status VARCHAR(20), -- 'Pending', 'Paid', 'COD'
  order_status VARCHAR(20), -- 'Placed', 'Packing', 'Out for Delivery', 'Completed'
  address_json JSONB,
  created_at TIMESTAMP DEFAULT NOW()
);
```

---

## 3. Phase 2: Frontend & UI Logic

### Persistent Cart State Manager (Zustand/React Context)
Handles the complex logic of weight-based increments (e.g., adding 500g steps).

```javascript
// store/useCartStore.js
import { create } from 'zustand';

export const useCartStore = create((set) => ({
  items: [],
  addItem: (product, quantity, type = 'fixed') => set((state) => {
    const existing = state.items.find(i => i.id === product.id);
    if (existing) {
      return {
        items: state.items.map(i => 
          i.id === product.id ? { ...i, quantity: i.quantity + quantity } : i
        )
      };
    }
    return { items: [...state.items, { ...product, quantity, type }] };
  }),
  removeItem: (id) => set((state) => ({
    items: state.items.filter(i => i.id !== id)
  })),
}));
```

---

## 4. Phase 3: Payment & Delivery Logic
Integrating local MFS (bKash/Nagad) via SSLCOMMERZ or similar aggregators.

### Delivery Slot Component Logic
```javascript
const DeliverySlots = () => {
  const slots = [
    { label: 'Express (60 mins)', value: 'express' },
    { label: 'Today: 4 PM - 6 PM', value: 't1' },
    { label: 'Tomorrow: 10 AM - 12 PM', value: 'tm1' }
  ];
  return (
    <div className="grid grid-cols-2 gap-4">
      {slots.map(slot => (
        <button className="p-4 border rounded hover:bg-green-50">
          {slot.label}
        </button>
      ))}
    </div>
  );
};
```

---

## 5. Phase 4: Order Management & Tracking
Live status tracking using a simplified state machine.

- **Backend Trigger:** When an admin updates `order_status`, a webhook or WebSocket event pushes the update to the "My Orders" panel.
- **Refund Policy Logic:** If an item is rejected at the doorstep, the rider updates the quantity via a Delivery App, triggering a partial refund calculation on the `total_amount`.
