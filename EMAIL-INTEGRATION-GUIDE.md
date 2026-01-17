# EMAIL INTEGRATION SETUP GUIDE
## Product Quote Requests with Maintenance Packages

## 🎯 WHAT YOU'RE BUILDING

When a customer clicks "Request Quote" on a product, they'll see a form that asks for:
- Customer Information (Name, Email, Phone, Address)
- Product they're interested in (auto-filled from product page)
- Maintenance Package selection (None, 1-Year, 3-Year, 5-Year)
- Additional notes/questions

When submitted, YOU receive an email with all this information.

---

## 📧 OPTION 1: ZAPIER + GMAIL (RECOMMENDED - EASIEST)

### Step 1: Create Zapier Webhook
1. Go to zapier.com
2. Click "Create Zap"
3. Search for "Webhooks by Zapier"
4. Choose "Catch Hook"
5. Copy the webhook URL (looks like: `https://hooks.zapier.com/hooks/catch/123456/abcdef/`)

### Step 2: Update Your Website Forms
In each product detail page, update the form action:

```html
<form id="productQuoteForm" action="https://hooks.zapier.com/hooks/catch/YOUR_ID/YOUR_CODE/" method="POST">
```

Replace `YOUR_ID/YOUR_CODE` with your actual Zapier webhook URL parts.

### Step 3: Test the Webhook
1. In Zapier, click "Test trigger"
2. Go to any product page on your site
3. Fill out the form and click "Request Quote"
4. Zapier should catch the test data
5. Click "Continue"

### Step 4: Add Gmail Action
1. Click "+" to add an action
2. Search for "Gmail"
3. Choose "Send Email"
4. Connect your Gmail account
5. Configure email:

**To**: Your email (e.g., contact@myrobopro.com)
**Subject**: New Quote Request - [Product Name]
**Body**: Use this template:

```
NEW QUOTE REQUEST

PRODUCT INFORMATION:
Product Name: [Insert productName from webhook]
Product Price: [Insert productPrice from webhook]
Manufacturer: [Insert manufacturer from webhook]

CUSTOMER INFORMATION:
Name: [Insert customerName from webhook]
Email: [Insert customerEmail from webhook]
Phone: [Insert customerPhone from webhook]
Address: [Insert customerAddress from webhook]
City/State/Zip: [Insert customerCity from webhook]

MAINTENANCE PACKAGE:
Selected Plan: [Insert maintenancePlan from webhook]

ADDITIONAL NOTES:
[Insert notes from webhook]

---
Submitted: [Insert timestamp from webhook]
```

### Step 5: Turn On Zap
Click "Publish" and your Zap is live!

---

## 📧 OPTION 2: HUBSPOT FORMS (IF YOU USE HUBSPOT CRM)

### Step 1: Create HubSpot Form
1. Go to HubSpot > Marketing > Forms
2. Click "Create Form"
3. Choose "Embedded Form"
4. Add these fields:
   - First Name (required)
   - Last Name (required)
   - Email (required)
   - Phone Number
   - Address
   - City
   - State
   - Product Name (single-line text)
   - Product Price (single-line text)
   - Manufacturer (single-line text)
   - Maintenance Package (dropdown: None, 1-Year Plan, 3-Year Plan, 5-Year Plan)
   - Additional Notes (multi-line text)

### Step 2: Set Up Notifications
1. Go to Form Settings > Options
2. Under "Send form notifications to"
3. Add your email: contact@myrobopro.com
4. Customize email template to include all fields

### Step 3: Get Embed Code
1. Click "Publish" > "Embed"
2. Copy the JavaScript embed code
3. Paste it into your product detail pages where the form should appear

### Step 4: Style the Form
HubSpot forms come with default styling. You can:
- Use HubSpot's form styles
- Add custom CSS in your stylesheet
- Use HubSpot's form editor to match your brand

---

## 📧 OPTION 3: FORMSPREE (SIMPLEST - NO ZAPIER NEEDED)

### Step 1: Create Formspree Account
1. Go to formspree.io
2. Sign up (free plan allows 50 submissions/month)
3. Click "New Form"
4. Enter your email (where you want to receive quotes)

### Step 2: Get Form Endpoint
Formspree will give you a form endpoint URL like:
`https://formspree.io/f/YOUR_FORM_ID`

### Step 3: Update Website Forms
In your product detail pages, use this form code:

```html
<form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
    <input type="hidden" name="_subject" value="New Quote Request">
    <input type="hidden" name="product_name" value="Yarbo Lawn Mower">
    <input type="hidden" name="product_price" value="$3,999">
    <input type="hidden" name="manufacturer" value="Yarbo">
    
    <input type="text" name="customer_name" placeholder="Full Name" required>
    <input type="email" name="customer_email" placeholder="Email" required>
    <input type="tel" name="customer_phone" placeholder="Phone Number" required>
    <input type="text" name="customer_address" placeholder="Street Address">
    <input type="text" name="customer_city" placeholder="City, State, ZIP">
    
    <label>Maintenance Package:</label>
    <select name="maintenance_plan">
        <option value="none">No Maintenance Package</option>
        <option value="1-year">1-Year Maintenance Plan</option>
        <option value="3-year">3-Year Maintenance Plan</option>
        <option value="5-year">5-Year Maintenance Plan</option>
    </select>
    
    <textarea name="notes" placeholder="Questions or additional information"></textarea>
    
    <button type="submit" class="btn-primary">Request Quote</button>
</form>
```

### Step 4: Customize Email Template (Optional)
In Formspree dashboard:
1. Go to your form settings
2. Click "Email Templates"
3. Customize subject line and email format

**Pros of Formspree:**
- ✅ Easiest to set up (5 minutes)
- ✅ No coding required
- ✅ Spam protection included
- ✅ Mobile-responsive

**Cons:**
- ❌ Limited to 50 submissions/month on free plan
- ❌ Less customization than Zapier

---

## 📧 OPTION 4: NETLIFY FORMS (IF USING NETLIFY HOSTING)

### Step 1: Add netlify Attribute
Simply add `netlify` to your form tag:

```html
<form name="product-quote" method="POST" data-netlify="true" netlify-honeypot="bot-field">
    <input type="hidden" name="form-name" value="product-quote">
    <!-- Your form fields here -->
</form>
```

### Step 2: Enable Email Notifications
1. Go to Netlify Dashboard
2. Select your site
3. Go to "Forms" in left menu
4. Click on your form name
5. Click "Notifications" > "Add notification"
6. Choose "Email notification"
7. Enter your email: contact@myrobopro.com
8. Customize email template

**Pros of Netlify Forms:**
- ✅ Free (100 submissions/month)
- ✅ Zero configuration if using Netlify
- ✅ Built-in spam filtering

**Cons:**
- ❌ Only works if hosting on Netlify
- ❌ Limited customization

---

## 🎨 MAINTENANCE PACKAGE PRICING (For Your Reference)

You should create these packages and price them. Example structure:

### 1-Year Plan
- 2 maintenance visits per year
- Priority support response
- 10% discount on parts
- **Price**: ~$299/year

### 3-Year Plan
- 2 maintenance visits per year
- Priority support response
- 15% discount on parts
- Extended warranty coverage
- **Price**: ~$799 (Save $98)

### 5-Year Plan
- 3 maintenance visits per year
- VIP support (24hr response)
- 20% discount on parts
- Extended warranty coverage
- Free blade replacements
- **Price**: ~$1,199 (Save $296)

---

## 🔧 TESTING YOUR SETUP

### Test Checklist:
1. [ ] Go to a product page
2. [ ] Click "Request Quote"
3. [ ] Fill out the form with test data
4. [ ] Select a maintenance package
5. [ ] Submit the form
6. [ ] Check your email inbox (contact@myrobopro.com)
7. [ ] Verify all information is included:
   - Product name
   - Product price
   - Customer information
   - Maintenance package selection
   - Notes

### Troubleshooting:
- **No email received?** Check spam folder first
- **Missing information?** Verify form field names match your email template
- **Form not submitting?** Check browser console for JavaScript errors
- **Zapier not catching?** Make sure webhook URL is correct

---

## 📱 MOBILE OPTIMIZATION

All form options work on mobile. Test on:
- iPhone Safari
- Android Chrome
- Tablet devices

Make sure:
- Form fields are easy to tap
- Text is readable
- "Request Quote" button is prominent
- Maintenance package dropdown is easy to use

---

## 🎯 RECOMMENDED APPROACH FOR YOU

Based on your setup (Gmail + HubSpot + Zapier available):

**BEST OPTION: Zapier + Gmail**
Why:
- ✅ Most flexible
- ✅ You already have Zapier
- ✅ Can add automation later (e.g., add to HubSpot CRM automatically)
- ✅ Unlimited submissions
- ✅ Full control over email format

**Setup Time**: 15-20 minutes
**Monthly Cost**: $0 (Zapier free tier is enough)

---

## 🔄 ADVANCED: AUTO-ADD TO HUBSPOT

If you want quotes to automatically create contacts/deals in HubSpot:

### In Your Zapier Workflow:
1. After Gmail step, add another action
2. Choose "HubSpot"
3. Select "Create Contact"
4. Map fields:
   - Email → Email
   - First Name → customerName (first word)
   - Last Name → customerName (last word)
   - Phone → customerPhone
   - etc.
5. Add another action for "Create Deal"
6. Deal properties:
   - Deal Name: "Quote - [Product Name]"
   - Amount: [Product Price]
   - Deal Stage: "Quote Requested"
   - Pipeline: "Sales Pipeline"

Now every quote request:
1. ✅ Emails you
2. ✅ Creates contact in HubSpot
3. ✅ Creates deal in pipeline
4. ✅ All automatic!

---

## 📋 NEXT STEPS

1. **Choose your integration method** (I recommend Zapier + Gmail)
2. **Follow setup steps above**
3. **Test with a real submission**
4. **Verify email arrives correctly**
5. **Go live!**

---

## 🆘 NEED HELP?

Common Issues:

**"I don't see the Zapier webhook URL"**
→ Make sure you selected "Webhooks by Zapier" and "Catch Hook"

**"Form submits but I don't get email"**
→ Check if Zap is turned ON (toggle in top right)

**"Email format looks wrong"**
→ Edit Gmail action and use the field mappings from webhook data

**"Can I get a copy email to the customer?"**
→ Yes! Add another Gmail action in Zapier to send to [customerEmail from webhook]

---

**File to reference for form HTML**: See `product-detail-template.html` (I'm creating next)

---

Let me know which integration method you want to use and I can provide the exact code for your forms!
