# HUBSPOT DEAL CREATION INTEGRATION GUIDE

## 🎯 GOAL
When someone submits a "Request Quote" form on a product page, automatically:
1. ✅ Create a contact in HubSpot (if doesn't exist)
2. ✅ Create a deal in HubSpot
3. ✅ Email you the quote request
4. ✅ Include product info, customer info, and maintenance package

---

## 📋 OPTION 1: ZAPIER + HUBSPOT (RECOMMENDED)

This is the best approach because it gives you both email notifications AND HubSpot CRM integration.

### STEP 1: Create Zapier Webhook (5 minutes)

1. Go to **zapier.com** and log in
2. Click **"Create Zap"**
3. Search for **"Webhooks by Zapier"**
4. Choose **"Catch Hook"**
5. Click **Continue**
6. Copy the webhook URL (looks like: `https://hooks.zapier.com/hooks/catch/123456/abcdef/`)
7. Click **"Test trigger"** (leave this tab open)

### STEP 2: Update Your Product Forms (5 minutes)

In each product detail page, update the form:

```html
<form class="quote-form" id="quoteForm" 
      action="https://hooks.zapier.com/hooks/catch/YOUR_ID/YOUR_CODE/" 
      method="POST">
```

Replace `YOUR_ID/YOUR_CODE` with your actual Zapier webhook path.

### STEP 3: Test the Webhook (2 minutes)

1. Go to one of your product pages
2. Fill out the quote request form
3. Click "Request Quote"
4. Go back to Zapier tab
5. Click "Test trigger" - it should show your test data
6. Click **Continue**

### STEP 4: Create Contact in HubSpot (5 minutes)

1. Click **"+"** to add an action
2. Search for **"HubSpot"**
3. Choose **"Create or Update Contact"**
4. Connect your HubSpot account (if not already)
5. Configure the mapping:

**Email** ← `customer_email` (from webhook)
**First Name** ← Split `customer_name` at space, take first part
**Last Name** ← Split `customer_name` at space, take last part
**Phone Number** ← `customer_phone`
**Address** ← `customer_address`
**City** ← `customer_city`
**State** ← `customer_state`

**Custom Properties** (create these in HubSpot if needed):
- **Property Size** ← `property_size`
- **Interested Product** ← `product_name`
- **Quote Request Date** ← Current timestamp

6. Click **Continue**
7. Click **Test action**

### STEP 5: Create Deal in HubSpot (10 minutes)

1. Click **"+"** to add another action
2. Search for **"HubSpot"**
3. Choose **"Create Deal"**
4. Configure the mapping:

**Deal Name** ← Format: "Quote - [product_name]" 
- Example: "Quote - Yarbo Lawn Mower"

**Amount** ← `product_price` 
- You'll need to strip the "$" and "," 
- In Zapier, use Formatter to clean: `product_price` → Number

**Deal Stage** ← "Quote Requested" (create this stage in HubSpot)

**Pipeline** ← "Sales Pipeline" (or your pipeline name)

**Contact** ← Use the Contact ID from Step 4

**Custom Properties**:
- **Manufacturer** ← `manufacturer`
- **Product Name** ← `product_name`
- **Maintenance Package** ← `maintenance_plan`
- **Property Size** ← `property_size`
- **Customer Notes** ← `notes`

6. Click **Continue**
7. Click **Test action**

### STEP 6: Send Email to You (5 minutes)

1. Click **"+"** to add another action
2. Search for **"Gmail"** (or your email provider)
3. Choose **"Send Email"**
4. Configure:

**To**: contact@myrobopro.com
**Subject**: New Quote Request - [product_name]
**Body**: 
```
NEW QUOTE REQUEST

PRODUCT INFORMATION:
Product: [product_name]
Price: [product_price]
Manufacturer: [manufacturer]

CUSTOMER INFORMATION:
Name: [customer_name]
Email: [customer_email]
Phone: [customer_phone]
Address: [customer_address], [customer_city], [customer_state]
Property Size: [property_size]

MAINTENANCE PACKAGE:
Selected: [maintenance_plan]

ADDITIONAL NOTES:
[notes]

---
HubSpot Deal: [Link to deal from Step 5]
Submitted: [timestamp]
```

5. Click **Continue**
6. Click **Test action**
7. Check your inbox!

### STEP 7: Turn On Your Zap

1. Click **"Publish"** in the top right
2. Name your Zap: "Product Quote to HubSpot"
3. Done! Your Zap is now live 🎉

---

## 📋 OPTION 2: HUBSPOT FORMS NATIVE (NO ZAPIER)

If you want to skip Zapier and use HubSpot forms directly:

### STEP 1: Create Form in HubSpot

1. Go to **HubSpot** → **Marketing** → **Forms**
2. Click **"Create Form"**
3. Choose **"Embedded Form"**
4. Add these fields:
   - Email (required)
   - First Name
   - Last Name
   - Phone Number
   - Address
   - City
   - State
   - Product Name (single-line text)
   - Product Price (single-line text)
   - Manufacturer (single-line text)
   - Property Size (dropdown)
   - Maintenance Package (dropdown)
   - Additional Notes (multi-line text)

### STEP 2: Create Custom Properties (if needed)

In HubSpot, go to **Settings** → **Properties** → **Contact Properties**

Create these if they don't exist:
- Product Name (single-line text)
- Product Price (single-line text)
- Manufacturer (single-line text)
- Property Size (dropdown)
- Maintenance Package (dropdown)

### STEP 3: Set Up Form Workflow

1. Go to **HubSpot** → **Automation** → **Workflows**
2. Click **"Create Workflow"**
3. Choose **"From Scratch"** → **"Contact-based"**
4. Set trigger: **"Form Submission"** → Select your quote form
5. Add action: **"Create Deal"**
   - Pipeline: Sales Pipeline
   - Deal Stage: Quote Requested
   - Deal Name: "Quote - [Product Name]"
   - Amount: [Product Price]
6. Add action: **"Send internal email notification"**
   - To: contact@myrobopro.com
   - Subject: New Quote Request
   - Body: Include all form fields

### STEP 4: Get Form Embed Code

1. Go back to your form
2. Click **"Share"** → **"Embed"**
3. Copy the embed code
4. Paste into your product pages

### STEP 5: Style HubSpot Form (Optional)

HubSpot forms have default styling. Add custom CSS to match your brand:

```css
/* HubSpot Form Overrides */
.hs-form-field label {
    font-family: var(--font-system);
    font-weight: 600;
    color: var(--slate-700);
}

.hs-form-field input[type="text"],
.hs-form-field input[type="email"],
.hs-form-field input[type="tel"],
.hs-form-field select,
.hs-form-field textarea {
    padding: 1rem;
    border: 2px solid var(--slate-200);
    border-radius: 0.75rem;
    font-family: var(--font-body);
}

.hs-submit input[type="submit"] {
    width: 100%;
    padding: 1.5rem;
    background: linear-gradient(135deg, var(--primary) 0%, var(--primary-light) 100%);
    color: white;
    font-family: var(--font-system);
    font-weight: 700;
    border: none;
    border-radius: 0.75rem;
}
```

---

## 📋 OPTION 3: HUBSPOT API DIRECT (ADVANCED)

For full control, use HubSpot API directly with JavaScript.

### STEP 1: Get HubSpot API Key

1. Go to **HubSpot** → **Settings** → **Integrations** → **API Key**
2. Click **"Create Key"** (or use existing)
3. Copy your API key

**⚠️ IMPORTANT**: Never expose API key in front-end code! Use server-side or Zapier.

### STEP 2: Create Server Endpoint

You'll need a backend (Node.js, PHP, etc.) to handle this:

```javascript
// Example Node.js endpoint
const axios = require('axios');

app.post('/submit-quote', async (req, res) => {
  const { 
    customer_name, 
    customer_email, 
    customer_phone,
    product_name,
    product_price,
    maintenance_plan 
  } = req.body;
  
  // Split name
  const [firstName, ...lastNameParts] = customer_name.split(' ');
  const lastName = lastNameParts.join(' ');
  
  // Create Contact
  const contactResponse = await axios.post(
    'https://api.hubapi.com/crm/v3/objects/contacts',
    {
      properties: {
        email: customer_email,
        firstname: firstName,
        lastname: lastName,
        phone: customer_phone
      }
    },
    {
      headers: {
        'Authorization': `Bearer YOUR_API_KEY`,
        'Content-Type': 'application/json'
      }
    }
  );
  
  const contactId = contactResponse.data.id;
  
  // Create Deal
  await axios.post(
    'https://api.hubapi.com/crm/v3/objects/deals',
    {
      properties: {
        dealname: `Quote - ${product_name}`,
        amount: product_price.replace(/[$,]/g, ''),
        dealstage: 'quote_requested',
        pipeline: 'default'
      },
      associations: [
        {
          to: { id: contactId },
          types: [{ associationCategory: 'HUBSPOT_DEFINED', associationTypeId: 3 }]
        }
      ]
    },
    {
      headers: {
        'Authorization': `Bearer YOUR_API_KEY`,
        'Content-Type': 'application/json'
      }
    }
  );
  
  res.json({ success: true });
});
```

---

## 🎯 RECOMMENDED APPROACH FOR YOU

**Best Option: Zapier + HubSpot (Option 1)**

**Why?**
- ✅ No coding required
- ✅ You already have Zapier
- ✅ You already have HubSpot
- ✅ Get email notification + CRM entry
- ✅ Easy to modify later
- ✅ Can add more automations (Slack, SMS, etc.)

**Setup Time**: 30 minutes
**Monthly Cost**: $0 (free tier sufficient)

---

## 🏗️ HUBSPOT SETUP REQUIREMENTS

### Create These Custom Properties in HubSpot:

**Contact Properties:**
1. **Product Interest** - Single-line text
2. **Property Size** - Dropdown (Under 1/4 acre, 1/4-1/2, 1/2-1, 1-2, Over 2)
3. **Maintenance Package Interest** - Dropdown (None, 1-Year, 3-Year, 5-Year)

**Deal Properties:**
1. **Manufacturer** - Single-line text
2. **Product Name** - Single-line text
3. **Maintenance Package** - Dropdown (None, 1-Year, 3-Year, 5-Year)
4. **Property Size** - Dropdown (same as contact)
5. **Customer Notes** - Multi-line text

### Create This Pipeline Stage:

**Pipeline**: Sales Pipeline
**Stage**: Quote Requested (10% probability)

Other suggested stages:
- Quote Sent (25%)
- Site Assessment Scheduled (40%)
- Proposal Sent (60%)
- Negotiation (75%)
- Closed Won (100%)
- Closed Lost (0%)

---

## 📧 EMAIL NOTIFICATION TEMPLATE

For the Gmail step in Zapier, use this template:

**Subject**: 
```
🤖 New Quote Request - {{product_name}} | {{customer_name}}
```

**Body**:
```
NEW QUOTE REQUEST RECEIVED

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📦 PRODUCT INFORMATION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Product: {{product_name}}
Price: {{product_price}}
Manufacturer: {{manufacturer}}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
👤 CUSTOMER INFORMATION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Name: {{customer_name}}
Email: {{customer_email}}
Phone: {{customer_phone}}
Address: {{customer_address}}
City/State: {{customer_city}}, {{customer_state}}
Property Size: {{property_size}}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🛠️ MAINTENANCE PACKAGE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Selected Plan: {{maintenance_plan}}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📝 CUSTOMER NOTES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

{{notes}}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🔗 QUICK ACTIONS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

View in HubSpot: [Deal Link]
Reply to Customer: mailto:{{customer_email}}
Call Customer: tel:{{customer_phone}}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Submitted: {{timestamp}}
Via: Product Detail Page - {{product_name}}
```

---

## 🧪 TESTING YOUR INTEGRATION

### Test Checklist:

1. **Submit Test Quote**
   - [ ] Fill out form on product page
   - [ ] Use real email (yours)
   - [ ] Select a maintenance package
   - [ ] Add notes
   - [ ] Submit

2. **Check Zapier**
   - [ ] Go to Zapier.com
   - [ ] Click on your Zap
   - [ ] View "Task History"
   - [ ] Verify all steps succeeded

3. **Check HubSpot Contact**
   - [ ] Go to HubSpot → Contacts
   - [ ] Search for test email
   - [ ] Verify all fields populated

4. **Check HubSpot Deal**
   - [ ] Go to HubSpot → Deals
   - [ ] Find your test deal
   - [ ] Verify deal name, amount, stage
   - [ ] Check associated contact
   - [ ] Verify custom properties

5. **Check Email**
   - [ ] Check inbox (contact@myrobopro.com)
   - [ ] Verify all information present
   - [ ] Test "Reply to Customer" link
   - [ ] Test "Call Customer" link

### Common Issues:

**"Contact created but deal didn't"**
→ Make sure you're using Contact ID from Step 4 in Step 5

**"Deal amount is $0"**
→ Use Zapier Formatter to remove "$" and "," from price

**"Maintenance package shows as 'none' always"**
→ Check radio button name attribute is "maintenance_plan"

**"Email arrives but formatting is broken"**
→ Use "Formatted" body type in Gmail action, not "Plain"

---

## 🚀 GOING LIVE

Once testing is successful:

1. **Turn on your Zap** (if not already)
2. **Update all product pages** with webhook URL
3. **Train your team** on responding to leads
4. **Set up email notifications** for new deals in HubSpot
5. **Create follow-up sequences** (optional)

### Pro Tips:

- **Response Time Goal**: Reply within 2-4 hours
- **Follow-up Sequence**: 
  - Day 0: Immediate auto-reply
  - Day 0: Personal follow-up (2-4 hours)
  - Day 2: Check-in if no response
  - Day 7: Final follow-up

- **Track Metrics**:
  - Quote requests per week
  - Response time
  - Quote-to-sale conversion rate
  - Most requested products

---

## 📱 BONUS: SLACK NOTIFICATIONS

Want real-time notifications in Slack?

1. In your Zapier workflow, add another action
2. Choose "Slack"
3. Select "Send Channel Message"
4. Configure:
   - Channel: #sales (or your channel)
   - Message: 
   ```
   🚨 New Quote Request!
   
   Product: {{product_name}} ({{product_price}})
   Customer: {{customer_name}}
   Email: {{customer_email}}
   Phone: {{customer_phone}}
   
   Maintenance: {{maintenance_plan}}
   
   View in HubSpot: [Deal Link]
   ```

Now your team gets instant Slack alerts!

---

## 📊 ANALYTICS & REPORTING

### HubSpot Reports to Create:

1. **Quote Request Volume**
   - Deals by create date
   - Grouped by product
   - Show as line chart

2. **Conversion Rate**
   - Deals in "Quote Requested" stage
   - vs. Deals in "Closed Won"
   - Calculate percentage

3. **Product Interest**
   - Deals by product name
   - Show as pie chart
   - Filter last 30 days

4. **Maintenance Package Adoption**
   - Deals by maintenance package
   - Show as bar chart
   - Compare packages

---

## ✅ FINAL CHECKLIST

Before considering your integration complete:

- [ ] Zapier Zap created and turned ON
- [ ] HubSpot custom properties created
- [ ] HubSpot pipeline stage "Quote Requested" exists
- [ ] Test quote submitted successfully
- [ ] Contact created in HubSpot with all fields
- [ ] Deal created in HubSpot with correct info
- [ ] Email notification received
- [ ] All product pages updated with webhook URL
- [ ] Team trained on responding to leads
- [ ] Follow-up process documented

---

**Need help with any step? Let me know where you're stuck and I can provide specific guidance!**
