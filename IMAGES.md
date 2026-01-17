# Images Documentation - My Robo Pro Website Redesign

## Overview
This document lists all images used in the redesigned website, including which original images were kept and which new images need to be added.

---

## KEPT IMAGES (From Original Website)

These images from your original website were retained and are still being used:

### 1. Logo
- **Filename**: `robo-mow-and-snow-logo.jpg`
- **Location**: `/images/robo-mow-and-snow-logo.jpg`
- **Used On**: All pages (header, footer)
- **Purpose**: Company logo/branding
- **Status**: ✅ KEPT - Used throughout site

### 2. Background Images (Optional)
- **Filename**: `home.webp` (if it exists)
- **Location**: `/images/home.webp`
- **Used On**: About page hero section
- **Status**: Referenced but may need updating

- **Filename**: `mountains.webp` (if it exists)
- **Location**: `/images/mountains.webp`
- **Used On**: About page content sections
- **Status**: Referenced but may need updating

---

## NEW IMAGES NEEDED

### Homepage Category Cards (3 images required)
These images should be added to give visual identity to each category card on the homepage:

#### 1. Residential Yard Care Image
- **Suggested Filename**: `residential-yard-robot.jpg`
- **Location**: `/images/residential-yard-robot.jpg`
- **Dimensions**: 800x600px minimum
- **Description**: Photo of a residential robot lawn mower or snow blower (Yarbo or similar) on a nice residential lawn
- **Used On**: Homepage - first category card
- **Alternative**: Can use Yarbo promotional photos

#### 2. Commercial Mower Image
- **Suggested Filename**: `commercial-mower-robot.jpg`
- **Location**: `/images/commercial-mower-robot.jpg`
- **Dimensions**: 800x600px minimum
- **Description**: Photo of a commercial robotic mower on a large property (park, golf course, commercial landscape)
- **Used On**: Homepage - second category card
- **Alternative**: Can use manufacturer promotional photos

#### 3. Floor Cleaning Robot Image
- **Suggested Filename**: `floor-cleaning-robot.jpg`
- **Location**: `/images/floor-cleaning-robot.jpg`
- **Dimensions**: 800x600px minimum
- **Description**: Photo of an autonomous floor scrubber/cleaner in a warehouse or commercial space (Pudu Robotics or similar)
- **Used On**: Homepage - third category card
- **Alternative**: Can use Pudu Robotics or other manufacturer promotional photos

---

### Product Pages Images

#### Residential Mowers Page
These images show specific Yarbo products:

##### 4. Yarbo Lawn Mower
- **Suggested Filename**: `yarbo-lawn-mower.jpg`
- **Location**: `/images/yarbo-lawn-mower.jpg`
- **Dimensions**: 1200x900px minimum
- **Description**: Yarbo Lawn Mower (Core + Mower Module) product photo
- **Used On**: Residential Mowers page - first product card
- **Source**: Get from Yarbo marketing materials

##### 5. Yarbo Lawn Mower Pro
- **Suggested Filename**: `yarbo-lawn-mower-pro.jpg`
- **Location**: `/images/yarbo-lawn-mower-pro.jpg`
- **Dimensions**: 1200x900px minimum
- **Description**: Yarbo Lawn Mower Pro product photo
- **Used On**: Residential Mowers page - second product card (with PRO badge)
- **Source**: Get from Yarbo marketing materials

##### 6. Yarbo Mower + Trimmer
- **Suggested Filename**: `yarbo-mower-trimmer.jpg`
- **Location**: `/images/yarbo-mower-trimmer.jpg`
- **Dimensions**: 1200x900px minimum
- **Description**: Yarbo system with both mower and trimmer modules
- **Used On**: Residential Mowers page - third product card
- **Source**: Get from Yarbo marketing materials

---

## IMAGE SOURCES & RECOMMENDATIONS

### Where to Get Images

#### 1. Manufacturer Marketing Materials
- **Yarbo**: Contact your Yarbo dealer representative for high-res product photos
  - Website: yarbo.com or yarbo.ai
  - These are professional photos specifically for dealers
  - Usually available in a dealer portal or media kit

- **Mammotion**: If carrying their products, get photos from their dealer portal
  - Website: mammotion.com

- **Pudu Robotics**: For floor cleaners when ready
  - Website: pudurobotics.com
  - Contact them for commercial dealer photos

#### 2. Professional Photography (Recommended)
- Hire a local photographer to take photos of actual installed units
- Show units in real Utah environments (residential yards, commercial properties)
- Authentic local photos build more trust than stock photos

#### 3. Stock Photography (Temporary)
If you need placeholder images immediately:
- **Unsplash.com** - Free high-quality photos
- **Pexels.com** - Free stock photos
- Search terms: "robot lawn mower", "autonomous mower", "floor scrubber robot"

---

## IMAGE SPECIFICATIONS

### Technical Requirements

**Format**: JPG or WebP preferred
- JPG for compatibility
- WebP for better compression (smaller file sizes)

**Dimensions**:
- Category cards: 800x600px minimum
- Product cards: 1200x900px minimum
- Hero backgrounds: 1920x1080px minimum

**File Size**:
- Compress images to under 500KB each
- Use tools like TinyPNG.com or Squoosh.app

**Quality**:
- High resolution (at least 72 DPI for web)
- Good lighting
- Professional appearance
- Consistent style across all images

---

## IMAGE PLACEHOLDERS IN CODE

### Where Placeholders Exist

All placeholder image locations are marked in the HTML with comments like:
```html
<!-- REPLACE WITH IMAGE: filename.jpg -->
<div class="placeholder-image">
    <!-- SVG icon shown until real image added -->
</div>
```

### Pages with Image Placeholders

1. **index.html** - 3 category card placeholders
2. **residential-mowers.html** - 3 product image placeholders
3. **commercial-floor.html** - No specific product images yet (coming soon section)

---

## REPLACING PLACEHOLDERS

### Step-by-Step Process

1. **Obtain Images**: Get photos from manufacturer or take your own
2. **Optimize Images**: Compress to appropriate file size
3. **Upload to /images folder**: Place all images in the images directory
4. **Update HTML**: Replace placeholder div with actual img tag

### Example Replacement

**Before (placeholder):**
```html
<div class="product-image">
    <!-- REPLACE WITH IMAGE: yarbo-lawn-mower.jpg -->
    <div class="placeholder-image residential" style="height: 300px;">
        <svg>...</svg>
    </div>
</div>
```

**After (real image):**
```html
<div class="product-image">
    <img src="images/yarbo-lawn-mower.jpg" alt="Yarbo Lawn Mower" style="width: 100%; height: 300px; object-fit: cover;">
</div>
```

---

## COLOR-CODED PLACEHOLDERS

The placeholder backgrounds use category colors to help identify which section they belong to:

- **Green gradient** (residential): `rgba(16, 185, 129, 0.1-0.2)` 
- **Blue gradient** (commercial): `rgba(14, 165, 233, 0.1-0.2)`
- **Purple gradient** (floor): `rgba(139, 92, 246, 0.1-0.2)`

These match the new color scheme:
- Residential: Green (`#10b981`)
- Commercial: Blue (`#0ea5e9`)
- Floor Cleaners: Purple (`#8b5cf6`)

---

## QUICK REFERENCE CHECKLIST

- [ ] Logo - robo-mow-and-snow-logo.jpg (ALREADY HAVE ✅)
- [ ] Homepage Card 1 - residential-yard-robot.jpg (NEED)
- [ ] Homepage Card 2 - commercial-mower-robot.jpg (NEED)
- [ ] Homepage Card 3 - floor-cleaning-robot.jpg (NEED)
- [ ] Product 1 - yarbo-lawn-mower.jpg (NEED)
- [ ] Product 2 - yarbo-lawn-mower-pro.jpg (NEED)
- [ ] Product 3 - yarbo-mower-trimmer.jpg (NEED)

**Total new images needed: 6**
**Total images kept: 1 (logo)**

---

## PRIORITY ORDER

If you need to add images gradually, here's the recommended priority:

### HIGH PRIORITY (Add First)
1. **residential-yard-robot.jpg** - Homepage is most visited page
2. **commercial-mower-robot.jpg** - Homepage visibility
3. **floor-cleaning-robot.jpg** - Complete the homepage

### MEDIUM PRIORITY (Add Next)
4. **yarbo-lawn-mower.jpg** - Primary product page
5. **yarbo-lawn-mower-pro.jpg** - Featured product

### LOWER PRIORITY (Can Wait)
6. **yarbo-mower-trimmer.jpg** - Additional product variant

---

## NOTES

- All pages are fully functional with or without images
- Placeholder SVGs provide visual structure until real images are added
- Images enhance the site but aren't required for launch
- The CSS is styled to handle images gracefully with object-fit properties
- Consider adding more Yarbo product photos as your inventory expands

---

## CONTACT FOR IMAGES

**Yarbo**:
- Dealer Portal: (contact your representative)
- Email: (your dealer contact)

**Need Help?**
- Professional photographer recommendation available
- Image optimization assistance available
- Bulk image processing can be automated

---

Last Updated: January 2026
