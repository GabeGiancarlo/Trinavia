# Dashboard Demo Page Design Doc

## Purpose
Simulate the admin dashboard for AeroVine’s owners—tracking sales, analytics (views, clicks, conversions), and managing shop inventory (drones and fleets). A demo of e-commerce backend functionality.

## Design and Feel
- **Overall Vibe**: Like a vineyard control room with a tech edge—warm and earthy, yet precise and data-driven. The nerve center where winemaking meets business analytics.
- **User Experience**: Clear and actionable—owners grasp performance and update stock without friction. Dense but organized, prioritizing at-a-glance insights and simple controls.
- **Visual Tone**: Rustic undertones (vine motifs, textures) with sleek charts and tables—a wooden desk with high-tech monitors. Data pops against a vineyard backdrop.
- **Interaction**: Functional and snappy—hover on graphs for details, clickable mock buttons (e.g., “Add Stock”), collapsible sections. Polished but static for demo.

## Layout

### 1. Top Navigation
- Logo: "AeroVine" (top left)
- Links: "Home" | "Catalog" | "Showcase" | "News/Updates" | "Dashboard Demo" (active)
- Button: "Cart" (top right, disabled in demo)

### 2. Sidebar Menu
- Title: "Dashboard Menu"
- Items:
  - "Overview" (active)
  - "Sales Analytics" (scrolls to sales graphs)
  - "Traffic Analytics" (scrolls to views/clicks/conversions)
  - "Inventory Management" (scrolls to stock tools)
  - "Orders" (placeholder, grayed out)
  - "Settings" (placeholder, grayed out)

### 3. Main Dashboard
- Title: "AeroVine Owner Dashboard"
- Text: "Your hub for sales, analytics, and inventory—see how AeroVine thrives."

#### Analytics Section
- Title: "Performance at a Glance"
- Text: "Track your shop’s success with real-time insights."
- Components:
  1. **Sales Graph**
     - Type: Line chart
     - Data: "Sales Over Time" ($5k Jan, $8k Feb, $12k Mar 2025)
     - Text: "Total Sales: $25,000 (Past 3 Months)"
  2. **Views Counter**
     - Type: Number stat
     - Data: "Site Views: 15,000 (Past 30 Days)"
     - Text: "Up 20% from last month"
  3. **Clicks Graph**
     - Type: Bar chart
     - Data: "CTA Clicks" (500 “Shop Now,” 300 “Contact Us”)
     - Text: "Top Click: Shop Now (62%)"
  4. **Conversions Stat**
     - Type: Percentage + number
     - Data: "Conversion Rate: 3.5% (525 sales from 15k views)"
     - Text: "Industry Avg: 2.5%"

#### Inventory Section
- Title: "Manage Your Stock"
- Text: "Keep your shop stocked—add, edit, or monitor drone inventory."
- Components:
  1. **Inventory Table**
     - Columns: Product | Stock | Price | Status
     - Rows:
       - VineScout | 12 units | $3,200 | In Stock
       - SprayVine | 8 units | $2,800 | Low Stock
       - GuardGrape | 15 units | $2,900 | In Stock
       - HarvestEye | 5 units | $3,500 | Low Stock
       - WaterWing | 20 units | $2,500 | In Stock
       - Vineyard Essentials (Fleet) | 3 bundles | $5,700 | In Stock
       - Harvest Boost (Fleet) | 2 bundles | $8,900 | Low Stock
       - Total Vineyard Control (Fleet) | 1 bundle | $15,000 | Low Stock
  2. **Action Buttons**
     - "Add Stock" (mock button)
     - "Edit Product" (mock button, per row)
     - "View Orders" (links to grayed-out Orders section)

### 4. CTA Section
- Title: "Ready to Run Your Own Vineyard Shop?"
- Text: "This is a demo—see our solutions or reach out to bring it to life."
- CTAs:
  - "Explore Catalog" (links to Catalog page)
  - "Contact Us" (links to contact form/email placeholder)

### 5. Footer
- Links: "Home" | "Catalog" | "Contact Us"
- Text: "AeroVine © 2025 – Elevating Vineyards Worldwide"