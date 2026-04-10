# Design System - servi.cam

## Philosophy
Mobile-first. Feels like a native app but runs in the browser.
Every decision prioritizes the 375px mobile screen first.

## Color Palette

### Primary - Orange (action, urgency, CTA)
- primary-50:  #FFF7ED
- primary-100: #FFEDD5
- primary-200: #FED7AA
- primary-300: #FDBA74
- primary-400: #FB923C
- primary-500: #F97316  ← main brand orange
- primary-600: #EA580C  ← hover states
- primary-700: #C2410C  ← pressed states

### Secondary - Blue (trust, navigation, links)
- secondary-50:  #EFF6FF
- secondary-100: #DBEAFE
- secondary-200: #BFDBFE
- secondary-300: #93C5FD
- secondary-400: #60A5FA
- secondary-500: #3B82F6  ← main brand blue
- secondary-600: #2563EB  ← hover states
- secondary-700: #1D4ED8  ← pressed states

### Neutrals
- white:        #FFFFFF  ← backgrounds
- gray-50:      #F9FAFB  ← subtle backgrounds
- gray-100:     #F3F4F6  ← cards, inputs
- gray-200:     #E5E7EB  ← borders, dividers
- gray-400:     #9CA3AF  ← placeholder text
- gray-600:     #4B5563  ← secondary text
- gray-900:     #111827  ← primary text

### Semantic
- success:  #22C55E  (green-500)
- warning:  #EAB308  (yellow-500)
- error:    #EF4444  (red-500)
- urgent:   #F97316  (same as primary, reinforces urgency)

## Typography

### Font
Plus Jakarta Sans (Google Fonts)
Import: https://fonts.google.com/specimen/Plus+Jakarta+Sans
Weights used: 400 (regular), 500 (medium), 600 (semibold), 700 (bold)

### Scale (mobile-first)
- text-xs:   12px / line-height 16px  → labels, badges
- text-sm:   14px / line-height 20px  → secondary text, captions
- text-base: 16px / line-height 24px  → body text (minimum for mobile)
- text-lg:   18px / line-height 28px  → card titles
- text-xl:   20px / line-height 28px  → section headers
- text-2xl:  24px / line-height 32px  → page titles
- text-3xl:  30px / line-height 36px  → hero text

### Usage rules
- Never below 14px on mobile (legibility)
- Page titles: 2xl bold
- Card titles: lg semibold
- Body: base regular
- Labels and badges: xs medium uppercase

## Spacing
Base unit: 4px (Tailwind default)
- xs:  4px   (gap between inline elements)
- sm:  8px   (tight padding)
- md:  16px  (standard padding, card inner)
- lg:  24px  (section spacing)
- xl:  32px  (major section breaks)
- 2xl: 48px  (hero sections)

## Border radius
- sm:   6px   (inputs, small badges)
- md:   12px  (cards, buttons)
- lg:   16px  (bottom sheets, modals)
- full: 9999px (pills, avatars, tags)

## Shadows
- shadow-sm:  subtle card lift
- shadow-md:  floating elements, dropdowns
- shadow-lg:  modals, bottom sheets

## Navigation (mobile)

### Top tabs
- Fixed at top below header
- Max 4-5 tabs
- Active tab: primary orange underline + orange text
- Inactive: gray-400 text
- No icons in tabs, text only for clarity

### Header (mobile)
- Height: 56px fixed
- White background
- Left: logo or back arrow
- Right: notification bell + avatar
- No hamburger menu

## Components

### Buttons
- Primary: bg-primary-500 text-white rounded-xl px-6 py-3 font-semibold
- Secondary: bg-secondary-500 text-white rounded-xl px-6 py-3 font-semibold
- Outline: border-2 border-primary-500 text-primary-500 rounded-xl
- Ghost: text-primary-500 no background no border
- Destructive: bg-error text-white rounded-xl
- Full width on mobile always
- Height minimum 48px (thumb friendly)

### Cards
- bg-white rounded-2xl shadow-sm p-4
- Border: none (use shadow only)
- Hover: shadow-md transition

### Inputs
- bg-gray-100 rounded-xl px-4 py-3 text-base
- Focus: ring-2 ring-primary-500 bg-white
- Height minimum 48px
- Full width always on mobile
- Label above input, never placeholder as label

### Badges / Tags
- rounded-full px-3 py-1 text-xs font-medium uppercase
- Category: bg-secondary-100 text-secondary-700
- Urgent: bg-primary-100 text-primary-700
- Active: bg-success/10 text-success
- Inactive: bg-gray-100 text-gray-600

### Avatar
- rounded-full object-cover
- Sizes: w-8 h-8 (sm), w-10 h-10 (md), w-16 h-16 (lg)
- Fallback: initials on bg-primary-100 text-primary-600

### Rating stars
- Orange fill: text-primary-500
- Empty: text-gray-200
- Always show numeric value next to stars

### Bottom sheet (modals mobile)
- Fixed bottom-0 left-0 right-0
- rounded-t-2xl bg-white
- Drag handle: w-12 h-1 bg-gray-200 mx-auto mt-3 rounded-full
- Max height: 90vh with scroll inside

## Breakpoints
- Mobile first: 375px base
- sm: 640px
- md: 768px (tablet)
- lg: 1024px (desktop optional)
- Primary target: 375px to 430px

## Mobile UX rules
- All tap targets minimum 48x48px
- No hover-only interactions
- Swipe gestures where natural (dismiss, navigate)
- Loading skeletons instead of spinners
- Empty states always have an action CTA
- Errors always have a recovery action

## Tailwind config additions
Add to tailwind.config.js:
colors:
  primary: (orange scale above)
  secondary: (blue scale above)
fonts:
  sans: ['Plus Jakarta Sans', 'sans-serif']
