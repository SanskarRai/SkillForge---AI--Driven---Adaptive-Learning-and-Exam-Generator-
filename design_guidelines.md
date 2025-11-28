# SkillForge: AI-Driven Adaptive Learning Platform - Design Guidelines

## Design Approach
**Selected System**: Material Design (adapted) with custom gradient theming
**Rationale**: EdTech platforms benefit from Material's structured hierarchy, clear data visualization patterns, and established interactive components while maintaining a modern, engaging aesthetic through custom theming.

## Core Design Elements

### Typography
- **Primary Font**: Inter (Google Fonts) - clean, modern, highly legible
- **Display/Headers**: Inter Bold (600-700 weight)
  - H1: 2.5rem (landing hero)
  - H2: 2rem (page titles)
  - H3: 1.5rem (card titles, section headers)
- **Body Text**: Inter Regular (400 weight)
  - Large: 1.125rem (important descriptions)
  - Standard: 1rem (general content)
  - Small: 0.875rem (metadata, timestamps)
- **Accent Font**: Inter Medium (500 weight) for buttons and CTAs

### Layout System
**Spacing Scale**: Use Tailwind units of 2, 4, 6, 8, 12, and 16
- Card padding: p-6 (mobile), p-8 (desktop)
- Section spacing: mb-8 between card groups
- Component gaps: gap-4 for grids, gap-2 for inline elements
- Page margins: px-4 (mobile), px-8 (tablet), px-12 (desktop)

### Component Library

**Topbar**
- Height: h-16 fixed across all breakpoints
- Layout: Flex container with justify-between
- Back button (when applicable): Left-aligned, icon + "Back" text
- Title: Centered on internal pages, right-aligned "SkillForge" on dashboards
- Icons (Notification + Profile): Right-aligned, gap-4, size 24px
- Background: Semi-transparent white (glass effect) with backdrop-blur
- Shadow: Subtle bottom shadow for elevation

**Card Component (Glass Morphism)**
- Background: White with 90% opacity
- Border: 1px solid rgba(255,255,255,0.3)
- Border radius: rounded-xl (12px)
- Shadow: Soft shadow (0 4px 6px rgba(0,0,0,0.1))
- Hover state: Transform translateY(-4px), enhanced shadow (0 8px 16px rgba(0,0,0,0.15))
- Transition: All 0.3s ease
- Text color: Dark gray (#1F2937) for high contrast on white cards

**Dashboard Grid Layout**
- Desktop: 3-column grid (grid-cols-3)
- Tablet: 2-column grid (md:grid-cols-2)
- Mobile: Single column (grid-cols-1)
- Gap: gap-6 between cards
- Card min-height: 180px for consistency

**Progress Bar Component**
- Container: Full width, h-3, rounded-full background
- Fill: Gradient (matches theme), rounded-full, smooth transition
- Label: Above bar showing percentage/status in small text
- Container background: Light gray (rgba(0,0,0,0.1))

**Buttons**
- Primary: Solid background, white text, rounded-lg, px-6 py-3
- Secondary: Outlined with border, theme color text, same padding
- Small/Inline: px-4 py-2, smaller font size
- Hover: Slight scale (1.02) and enhanced shadow
- When on images: Add backdrop-blur-md and semi-transparent background

**Search Bar (Courses Page)**
- Full width on mobile, max-w-md on desktop
- Height: h-12
- Border: 1px solid light gray
- Rounded: rounded-full for modern look
- Icon: Search icon left-aligned inside input
- Padding: pl-12 pr-4 to accommodate icon

**Course Cards (Student Courses)**
- Same glass morphism as dashboard cards
- Layout: Title at top, ProgressBar in middle, course metadata below
- "Add Course" button: Fixed bottom-right floating action button or top-right of page
- Hover: Same lift effect as dashboard cards

### Gradient Background
**Primary Gradient**: Linear gradient from top to bottom
- Top color: Light purple/blue (#E0E7FF or similar)
- Bottom color: Light pink/peach (#FCE7F3 or similar)
- Direction: 180deg (top to bottom)
- Fixed background on body element, consistent across all pages

### Landing Page Structure
**Hero Section**: 
- Height: 85vh on desktop, auto on mobile
- Layout: Two-column (text left, image/illustration right on desktop)
- Headline: Large, bold (3-4rem desktop, 2rem mobile)
- Subheadline: Supporting text below in regular weight
- CTA Buttons: Two buttons side by side - "Get Started" (primary) + "Learn More" (secondary)
- Background: Same gradient as entire app

**Features Section**:
- Three-column grid of feature cards
- Each card: Icon (48px), title, short description
- Icons: Use Material Icons or Heroicons

**Call-to-Action Section**:
- Centered content with large heading
- Single prominent button
- Supporting text about platform benefits

### Role Selection & Authentication Pages
**Layout**: Centered card (max-w-md) on gradient background
- Role cards: 2x2 grid on desktop, stacked on mobile
- Each role: Icon + label, hover state with lift effect
- Login/Register forms: Single column, generous spacing (gap-6)
- Input fields: h-12, rounded-lg, border, focus state with theme color
- OTP input (Register - Student): 6 individual boxes, centered, gap-2

### Dashboard Specific Elements
**Stat Cards**: Display metrics with large numbers and labels
**Activity Lists**: Timeline-style with timestamps and status indicators
**Action Buttons**: Grouped in card footers or as floating actions
**Empty States**: Centered icon + message when no data exists

### Responsive Behavior
- Mobile: Stack all multi-column layouts to single column
- Tablet: Reduce to 2 columns max
- Desktop: Full 3-column layouts where applicable
- Topbar: Remains fixed at top, responsive padding

### Images
No hero images required for this application. Focus on icon-based illustrations and data visualization through progress bars and charts. Icons should be consistent throughout (choose either Heroicons or Material Icons CDN).

### Accessibility
- All interactive elements: min-height 44px for touch targets
- Form inputs: Proper labels, placeholder text, error states
- Color contrast: Ensure dark text on white cards meets WCAG AA standards
- Focus states: Visible outline on keyboard navigation
- Semantic HTML: Proper heading hierarchy, button vs. link usage