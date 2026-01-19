# Product Page Template Guide

Use this guide to quickly create all remaining product pages using the `product-mammotion-luba.html` template.

---

## Quick Creation Steps

1. **Copy the template file**
   ```bash
   cp product-mammotion-luba.html product-[NEW-NAME].html
   ```

2. **Find & Replace these values:**

### Basic Information (replace throughout file)
- Search: `MAMMOTION LUBA 3 AWD`
- Replace with: `[Your Product Name]`

- Search: `product-mammotion-luba.html`
- Replace with: `product-[your-file-name].html`

- Search: `$3,299.00`
- Replace with: `$[Your Price]`

- Search: `Commercial Lawn Robot`
- Replace with: `[Residential Lawn / Commercial Lawn / Commercial Floor]`

### Product Description
Replace the main description paragraph (line ~152) with your product description

### Key Features
Update the 6 feature list items (lines ~161-217) with your product's features

### Specifications
Update the spec table (lines ~245-310) with your product's specs

### Images
Update image paths:
- Main image: `images/mammotion-luba-main.jpg` → `images/[your-product]-main.jpg`
- Thumbnails: `images/mammotion-luba-1.jpg` → `images/[your-product]-1.jpg`

---

## Product Data Templates

Copy and paste these into your product pages:

### YARBO PRODUCTS

#### Yarbo Core
```
Name: Yarbo Core
Price: $3,599.00
Category: Residential Lawn Robot
Description: The foundation of your automated lawn care system. Modular design allows you to add snow blowing, mowing, leaf blowing, and trimming capabilities as needed.

Features:
- Modular platform for unlimited versatility
- RTK-GPS navigation with centimeter accuracy
- Weather-resistant all-season design
- Smart app control with real-time monitoring
- Quick-swap module system
- Powerful battery system

Specs:
- Battery Type: Lithium-ion rechargeable
- Charging Time: 2-3 hours
- Runtime: Up to 4 hours per charge
- Navigation: RTK-GPS
- Connectivity: WiFi + 4G
- Weather Resistance: IPX6 rated
- Weight: 15 kg (33 lbs)
- Warranty: 2 years
```

#### Yarbo Snow Blower
```
Name: Yarbo Snow Blower
Price: $4,299.00
Category: Residential Lawn Robot
Description: Complete automated snow removal system combining Yarbo Core with powerful Snow Blower Module. Clears driveways and paths with precision RTK-GPS navigation.

Features:
- Powerful two-stage snow clearing
- Throws snow up to 30 feet
- Handles up to 12 inches of snow
- Automatic path optimization
- Works in temperatures down to -4°F
- Schedule multiple clearing passes

Specs:
- Clearing Width: 24 inches
- Max Snow Depth: 12 inches
- Throw Distance: Up to 30 feet
- Min Temperature: -4°F (-20°C)
- Coverage: Up to 6 acres
- Runtime: 2-3 hours per charge
- Weight: 25 kg (55 lbs)
- Warranty: 2 years
```

#### Yarbo Lawn Mower
```
Name: Yarbo Lawn Mower
Price: $3,999.00
Category: Residential Lawn Robot
Description: Autonomous mowing for lawns up to 6 acres. Zero-wire technology with smart scheduling and multi-zone management.

Features:
- Zero-wire perimeter-free operation
- Multi-zone lawn mapping
- Adjustable cutting height (1-4 inches)
- Rain sensor auto-return
- Obstacle detection and avoidance
- Smart scheduling based on grass growth

Specs:
- Coverage Area: Up to 6 acres
- Cutting Width: 20 inches
- Cutting Height: 1-4 inches adjustable
- Max Slope: 45%
- Runtime: 3-4 hours per charge
- Blade System: Triple blade
- Weight: 20 kg (44 lbs)
- Warranty: 2 years
```

#### Yarbo Lawn Mower Pro
```
Name: Yarbo Lawn Mower Pro
Price: $5,499.00
Category: Residential Lawn Robot
Description: Professional-grade mowing with enhanced cutting power, wider deck, and extended battery for larger properties.

Features:
- Enhanced 28-inch cutting deck
- Dual motor system for maximum power
- Extended battery for 8+ hour runtime
- Professional striping patterns
- Advanced terrain adaptation
- Premium mulching system

Specs:
- Coverage Area: Up to 12 acres
- Cutting Width: 28 inches
- Cutting Height: 0.75-4.5 inches
- Max Slope: 50%
- Runtime: 6-8 hours per charge
- Motor Power: Dual 300W motors
- Weight: 28 kg (62 lbs)
- Warranty: 3 years
```

#### Yarbo Leaf Blower
```
Name: Yarbo Leaf Blower
Price: $3,799.00
Category: Residential Lawn Robot
Description: Automated leaf collection and debris management. Perfect for fall cleanup with powerful air flow and intelligent path planning.

Features:
- High-velocity air system
- Automatic collection bin
- Multi-pass debris clearing
- Edge cleaning mode
- Wet/dry debris handling
- Scheduled seasonal operation

Specs:
- Air Velocity: 200 MPH
- Collection Capacity: 50 gallons
- Coverage: Up to 6 acres
- Runtime: 3-4 hours per charge
- Debris Types: Leaves, grass, light branches
- Weight: 22 kg (48 lbs)
- Warranty: 2 years
```

#### Yarbo Trimmer
```
Name: Yarbo Trimmer
Price: $735.00
Category: Residential Lawn Robot
Description: Precision edge trimming module for perfect property finishing along fences, walls, and walkways.

Features:
- Auto-adjusting trim height
- Dual-spinning nylon line
- Edge detection sensors
- Works with all Yarbo systems
- Lightweight design
- Easy attachment system

Specs:
- Trim Width: 12 inches
- Line Type: Heavy-duty nylon
- Compatible: All Yarbo Core systems
- Runtime: 1-2 hours per charge
- Weight: 3 kg (6.6 lbs)
- Warranty: 2 years
```

### COMMERCIAL PRODUCTS (Placeholder Specs - Update as needed)

#### Sveaverken Thor
```
Name: Sveaverken Thor
Price: $12,999.00
Category: Commercial Lawn Robot
Description: Heavy-duty commercial mower designed for large properties, golf courses, and demanding terrain. Industrial-grade construction for year-round operation.

Features:
- Industrial-grade cutting system
- Coverage up to 20 acres
- Advanced GPS navigation
- Weather-resistant design
- Fleet management capability
- Remote monitoring

Specs:
- Coverage Area: Up to 20 acres
- Cutting Width: 36 inches
- Runtime: 8-10 hours
- Weight: 120 kg (265 lbs)
- Warranty: 3 years commercial
```

#### Echo TM-1000
```
Name: Echo TM-1000
Price: $8,999.00
Category: Commercial Lawn Robot
Description: Professional autonomous mower for sports fields and large commercial properties with precision cutting and smart management.

Features:
- Sports field striping patterns
- Multi-unit fleet control
- Real-time monitoring
- Precision edge cutting
- Weather adaptive operation
- Low noise operation

Specs:
- Coverage Area: Up to 15 acres
- Cutting Width: 30 inches
- Runtime: 6-8 hours
- Weight: 95 kg (209 lbs)
- Warranty: 3 years
```

#### Pudu CC1
```
Name: Pudu CC1
Price: $14,999.00
Category: Commercial Floor Cleaner
Description: Automated floor scrubber for retail, warehouse, and commercial facilities. Professional cleaning with autonomous navigation.

Features:
- Dual-brush cleaning system
- Water recovery system
- Autonomous navigation
- Obstacle avoidance
- Scheduled cleaning programs
- Remote monitoring

Specs:
- Cleaning Width: 26 inches
- Tank Capacity: 15 gallons
- Runtime: 4-5 hours
- Coverage: Up to 50,000 sq ft
- Weight: 150 kg (330 lbs)
- Warranty: 2 years
```

#### Pudu CC1 Pro
```
Name: Pudu CC1 Pro
Price: $17,999.00
Category: Commercial Floor Cleaner
Description: Enhanced scrubbing power with advanced navigation, longer runtime, and larger tanks for extended operations.

Features:
- Enhanced scrubbing pressure
- Extended battery system
- Advanced AI navigation
- Multi-floor mapping
- Fleet management ready
- Professional reporting

Specs:
- Cleaning Width: 28 inches
- Tank Capacity: 20 gallons
- Runtime: 6-8 hours
- Coverage: Up to 80,000 sq ft
- Weight: 175 kg (385 lbs)
- Warranty: 3 years
```

---

## Quick File Naming Convention

Use this pattern for all product files:
- `product-[brand]-[model].html`

Examples:
- product-yarbo-core.html
- product-yarbo-snow-blower.html
- product-sveaverken-thor.html
- product-pudu-cc1.html
- product-echo-tm1000.html

**Package files:**
- product-4in1-yard-robot.html
- product-5in1-yard-robot.html
- product-snow-lawn-combo.html

---

## Images Needed Per Product

For best results, each product should have:
1. **Main image** - `images/[product-name]-main.jpg` (800x600px+)
2. **4 Thumbnails** - `images/[product-name]-1.jpg` through `-4.jpg` (200x200px+)

If you don't have multiple angles, use the same image for all 5 images.

---

## Batch Creation Script (Optional)

If you're comfortable with command line, you can create all files at once:

```bash
# Create all Yarbo residential products
for product in "core" "snow-blower" "lawn-mower" "lawn-mower-pro" "leaf-blower" "trimmer"; do
  cp product-mammotion-luba.html product-yarbo-$product.html
done

# Create all commercial lawn products
for product in "sveaverken-thor" "echo-tm1000" "echo-tm1050" "echo-tm2000" "echo-tm2050"; do
  cp product-mammotion-luba.html product-$product.html
done

# Create all floor cleaners
for product in "pudu-cc1" "pudu-cc1-pro" "pudu-mt1" "pudu-mt1-vac" "sveabot-s100-pro-m" "sveabot-s100-pro-r"; do
  cp product-mammotion-luba.html product-$product.html
done

# Create all packages
for product in "4in1-yard-robot" "5in1-yard-robot" "snow-lawn-combo" "lawn-leaf-combo" "snow-leaf-combo"; do
  cp product-mammotion-luba.html product-$product.html
done
```

Then edit each file individually with the correct information.

---

## Testing Checklist

After creating each product page:
- [ ] Product name appears in title tag
- [ ] Price is correct
- [ ] All navigation links work
- [ ] Images load (or show placeholder)
- [ ] "Request Quote" button works
- [ ] Mobile view looks good
- [ ] Product is listed in products.html
- [ ] Product appears in mega menu

---

## Time Estimate

- Per product page: 10-15 minutes
- Total for all 29 products: 5-7 hours

**Pro Tip:** Do all the copy/paste first, then go back and fill in content. It's faster to do one task at a time across all files.

---

Good luck! You've got this! 🚀
