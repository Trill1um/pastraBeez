# PastraBeez Design System Rules
## Figma to Code Integration Guidelines

This document outlines the rules for integrating Figma designs into the PastraBeez codebase using the Model Context Protocol (MCP).

## 📋 Table of Contents
1. [Design System Structure](#design-system-structure)
2. [Typography System](#typography-system)
3. [Color System](#color-system)
4. [Component Integration Rules](#component-integration-rules)
5. [Asset Management](#asset-management)
6. [Figma MCP Integration Workflow](#figma-mcp-integration-workflow)

---

## 🏗️ Design System Structure

### Token Definitions Location
```
frontend/src/styles/bee-colors.css
```
**Central design system file containing:**
- CSS custom properties for colors
- Typography variables and classes
- Component-specific styles
- Responsive design patterns

### Token Structure Format
```css
:root {
  /* Color tokens */
  --bee-yellow: #ffdd00;
  --bee-orange: #f7b81a;
  
  /* Semantic mappings */
  --text-primary: var(--bee-maroon);
  --bg-brand: var(--bee-yellow);
  
  /* Typography tokens */
  --font-bee-pollen: 'b Bee Pollen', cursive;
  --text-base: 16px;
  --leading-normal: 1.5;
}
```

### Component Architecture
**Framework:** React 18 + Vite
**Styling:** CSS Custom Properties + Tailwind CSS
**File Structure:**
```
frontend/src/
├── pages/           # Page components
├── styles/          # Design system styles
└── assets/          # Static assets
```

---

## ✍️ Typography System

### **CRITICAL RULE: Typography Validation Process**

**Before using ANY typography from Figma:**

1. **Check `bee-colors.css` first** for existing typography classes
2. **If typography exists** → Use existing CSS class
3. **If typography doesn't exist** → Add to `bee-colors.css` → Use new class

### Typography Class Naming Convention
```css

/* Type-based naming (Based on Boldness; title: 600, body: 400, item: 500) */
.bee-title, .bee-body-text, .bee-item 

/* Context-based naming */
.bee-logo
.bee-nav
.bee-footer

/* Hierarchy-based naming */
.placeholder-h1, .placeholder-h2, .placeholder-h3, .placeholder-h4, .placeholder-h5, .placeholder-h6, .placeholder-body, .placeholder-small

/* Component-specific naming */
.placeholder-product-name
.placeholder-seller-name
.placeholder-price
.placeholder-likes

/* Breakpoint */
.placeholder-Desktop,
.placeholder-Tabler,
.placeholder-Mobile

/* Naming format */
.bee-type-hierarchy-breakpoint
.bee-context-breakpoint

/* Naming format example */
.bee-title-h6-Desktop,
.bee-body-h2-Tablet,
.bee-body-body-Mobile,
.bee-logo-Mobile,
.bee-item-name-Mobile,
.bee-item-price-Mobile
```

### Existing Typography Classes in `bee-colors.css`

#### **Logo Typography**
```css
.bee-logo-desktop          /* b Bee Pollen, 49px, weight 400, line-height 1.1 */
.bee-footer-logo-desktop   /* Just Me Again Down Here, 64px, weight 400, line-height 1.1 */
```

#### **Heading Typography**
```css
.bee-h1, .bee-body-h1-desktop     /* Quicksand, 49px, weight 400, line-height 1.1 */
.bee-h2, .bee-title-h2-desktop    /* Fredoka One, 43px, weight 400, line-height 1.1 */
.bee-h3                           /* Fredoka One, 32px, weight 400, line-height 1.3 */
.bee-h4, .bee-title-h4-desktop    /* Fredoka One, 32px, weight 400, line-height 1.3 */
.bee-h5                           /* Fredoka One, 25px, weight 400, line-height 1.3 */
.bee-h6, .bee-title-h6-desktop    /* Fredoka One, 25px, weight 400, line-height 1.3 */
```

#### **Body Typography**
```css
.bee-body-text, .bee-body-text-desktop  /* Quicksand, 16px, weight 400, line-height 1.5 */
.bee-body-large                         /* Quicksand, 18px, weight 400, line-height 1.5 */
.bee-body-small                         /* Quicksand, 14px, weight 400, line-height 1.5 */
.bee-body-xs                            /* Quicksand, 12px, weight 400, line-height 1.6 */
```

#### **Navigation Typography**
```css
.bee-nav-text, .bee-nav-desktop    /* Quicksand, 20px, weight 400, line-height 1.5 */
```

#### **Footer Typography**
```css
.bee-footer-title, .bee-footer-title-desktop      /* Fredoka One, 25px, weight 400, line-height 1.3 */
.bee-footer-body, .bee-footer-body-desktop         /* Poppins, 18px, weight 400, line-height 1.5 */
.bee-footer-sitemap, .bee-footer-sitemap-desktop   /* Quicksand, 20px, weight 600, line-height 1.5 */
```

#### **Product Card Typography**
```css
.bee-product-name    /* Fredoka, weight 600, letter-spacing -0.375px, line-height 1.3 */
.bee-seller-name     /* Quicksand, weight 500, letter-spacing 0.07px, line-height 1.6 */
.bee-price           /* Fredoka One, weight 700, letter-spacing -0.42px, line-height 1.3 */
.bee-likes           /* Quicksand, weight 500, letter-spacing 0.08px, line-height 1.5 */
```

#### **Button & Input Typography**
```css
.bee-btn-text        /* Quicksand, weight 700, line-height 1.3 */
.bee-input-text      /* Quicksand, weight 400, line-height 1.5 */
.bee-badge-text      /* Quicksand, weight 500, letter-spacing 0.12px, line-height 1.6 */
```

### Typography Addition Process
When Figma typography doesn't exist in `bee-colors.css`:

1. **Identify the typography specs** from `#get_code`
2. **Determine appropriate class name** following naming convention
3. **Add to bee-colors.css** in appropriate section
4. **Use the new class** in components

**Example Addition:**
```css
/* NEW TYPOGRAPHY - Added to bee-colors.css */
.bee-new-component-text {
  font-family: var(--font-quicksand);
  font-size: var(--text-lg);
  font-weight: 500;
  line-height: var(--leading-normal);
  letter-spacing: 0.05px;
  color: var(--text-primary);
}
```

---

## 🎨 Color System

### Color Variables Location
All colors are defined in `frontend/src/styles/bee-colors.css`

### Primary Brand Colors
```css
:root {
  --bee-yellow: #ffdd00;        /* Primary brand yellow */
  --bee-orange: #f7b81a;        /* Secondary orange/amber */
  --bee-cream: #fee4a2;         /* Light cream for badges */
  --bee-dark-blue: #141b34;     /* Logo text, brand text */
  --bee-maroon: #5c1802;        /* Dark text, prices */
  --bee-red: #ec4b1c;           /* Product names, CTAs */
  --bee-black: #111111;         /* Pure black for text */
  --bee-medium-gray: #8d8d8d;   /* Secondary text */
  --bee-light-gray: #d9d9d9;    /* Light borders */
  --bee-white: #ffffff;         /* Pure white */
}
```

### Semantic Color Mappings
```css
:root {
  /* Text Colors */
  --text-primary: var(--bee-maroon);
  --text-secondary: var(--bee-medium-gray);
  --text-brand: var(--bee-dark-blue);
  --text-product: var(--bee-red);
  --text-seller: var(--bee-orange);
  --text-price: var(--bee-maroon);
  --text-likes: var(--bee-yellow);
  
  /* Background Colors */
  --bg-primary: var(--bee-white);
  --bg-brand: var(--bee-yellow);
  --bg-secondary: var(--bee-orange);
  --bg-accent: var(--bee-cream);
  
  /* Border Colors */
  --border-primary: var(--bee-orange);
  --border-secondary: var(--bee-light-gray);
}
```

### Color Usage Classes
```css
/* Background utilities */
.bg-bee-primary, .bg-bee-brand, .bg-bee-secondary, etc.

/* Text color utilities */
.text-bee-primary, .text-bee-secondary, .text-bee-brand, etc.

/* Component-specific classes */
.bee-header, .bee-footer, .bee-card, .bee-nav-link, etc.
```

---

## 🧩 Component Integration Rules

### **MCP Integration Workflow**

#### Step 1: Get Figma Code
```javascript
// Use MCP to get component code
#mcp_my-mcp-server2_get_code
```

#### Step 2: Typography Validation
1. **Extract typography specs** from generated code
2. **Check `bee-colors.css`** for existing classes
3. **Match or create** appropriate typography class

**Example Check:**
```javascript
// Generated Figma code shows:
font-family: 'Quicksand:Regular'
font-size: 16px
font-weight: 400
line-height: 1.5

// Check bee-colors.css for match:
.bee-body-text {
  font-family: var(--font-quicksand);  ✅ MATCH
  font-size: var(--text-base);         ✅ MATCH (16px)
  font-weight: 400;                    ✅ MATCH
  line-height: var(--leading-normal);  ✅ MATCH (1.5)
}

// RESULT: Use .bee-body-text class
```

#### Step 3: Color Integration
1. **Replace hardcoded colors** with CSS custom properties
2. **Use semantic color classes** where possible
3. **Add new colors** to `bee-colors.css` if needed

**Example:**
```jsx
// ❌ DON'T USE hardcoded colors
<div className="text-[#5c1802] bg-[#ffdd00]">

// ✅ DO USE design system classes
<div className="text-bee-primary bg-bee-brand">

// ✅ OR USE custom properties in inline styles
<div style={{ color: 'var(--text-primary)', backgroundColor: 'var(--bg-brand)' }}>
```

#### Step 4: Component Structure
```jsx
// Component template structure
import React from 'react';
import '../styles/bee-colors.css';

const ComponentName = () => {
  return (
    <div className="bee-component-container">
      <h2 className="bee-h2">Title</h2>
      <p className="bee-body-text">Content</p>
      <button className="bee-btn-primary">
        <span className="bee-btn-text">Action</span>
      </button>
    </div>
  );
};

export default ComponentName;
```

### Responsive Design Integration
```css
/* Mobile-first responsive classes */
@media (max-width: 768px) {
  .bee-responsive-text {
    font-size: clamp(14px, 3vw, 16px);
  }
}

/* Tablet breakpoint */
@media (min-width: 769px) and (max-width: 1024px) {
  .bee-responsive-text {
    font-size: 16px;
  }
}
```

---

## 🖼️ Asset Management

### Asset Structure
```
frontend/public/
├── vite.svg
frontend/src/assets/
├── react.svg
```

### Figma Asset Integration
```javascript
// Assets are served from MCP server
const beeIcon = "http://localhost:3845/assets/5c1f69025ddee607f040bb51fefab0636c716933.png";
const productImage = "http://localhost:3845/assets/5796a00a87e46e940e0620124510ffbacc908c69.png";

// Usage in components
<img src={beeIcon} alt="Bee icon" className="bee-icon" />
```

### Asset Optimization Rules
1. **Use MCP-served assets** during development
2. **Download and optimize** for production
3. **Implement lazy loading** for better performance
4. **Use appropriate alt text** for accessibility

---

## 🔄 Figma MCP Integration Workflow

### Complete Integration Process

#### 1. **Design Analysis**
```javascript
// Get component code from Figma
#mcp_my-mcp-server2_get_code

// Extract design variables if needed
#mcp_my-mcp-server2_get_variable_defs
```

#### 2. **Typography Validation & Integration**
```javascript
// PROCESS:
// 1. Extract typography from generated code
// 2. Search bee-colors.css for existing matches
// 3a. IF EXISTS → Use existing class
// 3b. IF NOT EXISTS → Add to bee-colors.css → Use new class
```

#### 3. **Color System Integration**
```javascript
// Replace all hardcoded colors with:
// - CSS custom properties: var(--bee-color-name)
// - Utility classes: .text-bee-primary, .bg-bee-brand
// - Component classes: .bee-card, .bee-button
```

#### 4. **Component Creation**
```jsx
// Template structure
import React from 'react';
import '../styles/bee-colors.css';

const NewComponent = () => {
  return (
    <div className="bee-new-component">
      {/* Use typography classes from bee-colors.css */}
      <h1 className="bee-h1">Title</h1>
      <p className="bee-body-text">Content</p>
      
      {/* Use color classes from bee-colors.css */}
      <button className="bee-btn-primary">
        <span className="bee-btn-text">Click me</span>
      </button>
    </div>
  );
};
```

#### 5. **Responsive Implementation**
```css
/* Add responsive styles to bee-colors.css */
@media (max-width: 768px) {
  .bee-new-component {
    /* Mobile styles */
  }
}
```

### **Validation Checklist**

Before finalizing any Figma integration:

- [ ] **Typography checked** against `bee-colors.css`
- [ ] **Colors use** CSS custom properties or utility classes
- [ ] **No hardcoded** Tailwind colors (e.g., `text-[#ffffff]`)
- [ ] **Responsive breakpoints** implemented
- [ ] **Accessibility** attributes added
- [ ] **Performance optimization** considered
- [ ] **Component follows** BEM-like naming convention

---

## 🛠️ Development Guidelines

### File Organization
```
frontend/src/
├── pages/
│   ├── Catalog.jsx              # Uses bee-colors.css
│   ├── HomePage.jsx
│   └── LoginPage.jsx
├── styles/
│   ├── bee-colors.css           # 🎯 MAIN DESIGN SYSTEM FILE
│   ├── catalog.css              # Component-specific styles
│   └── E-Catalog-variables.css
└── assets/
    └── react.svg
```

### Import Standards
```jsx
// Always import design system first
import '../styles/bee-colors.css';

// Then component-specific styles if needed
import '../styles/component-name.css';
```

### Class Naming Consistency
```css
/* Follow bee- prefix convention */
.bee-component-name { }       /* Component container */
.bee-element-name { }         /* Element within component */
.bee-modifier-name { }        /* State or variant modifier */
```

### Performance Considerations
1. **CSS Custom Properties** for dynamic theming
2. **Class-based styles** for reusability
3. **Responsive utility classes** for flexibility
4. **Font loading optimization** with `font-display: swap`

---

## 📝 Summary

**Key Integration Rules:**
1. **Always check `bee-colors.css` first** for existing typography/colors
2. **Reuse existing classes** whenever possible
3. **Add new styles** to `bee-colors.css` when needed
4. **Use semantic naming** for new additions
5. **Maintain responsive design** principles
6. **Follow accessibility** best practices

This design system ensures consistency, maintainability, and seamless integration between Figma designs and the PastraBeez codebase using the Model Context Protocol.
