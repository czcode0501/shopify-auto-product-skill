---
name: shopify-auto-product
description: "Use when automatically researching, selecting, and launching low-budget Shopify test products: find niches, create products/collections/pages in Shopify Admin via local CDP, write policies, and prepare fulfillment/pixel/image next steps."
version: 1.0.0
author: Hermes Agent
license: MIT
metadata:
  hermes:
    tags: [shopify, ecommerce, dropshipping, pet-products, product-launch, cdp]
    related_skills: [shopify-store-operations, industry-dissection-template, agent-reach]
---

# Shopify Pet Product Launch Workflow

## Overview

This skill captures the reusable workflow used to research and set up a low-budget Shopify product test for a Canada-based student seller targeting the US/Canada first, with optional UK/Australia later. The specific launch example was a **pet hair cleanup** product line built around lightweight, non-sensitive, China-direct-friendly products:

1. Reusable Pet Hair Remover Roller
2. Reusable Pet Hair Removal Glove
3. Pet Hair Roller + Grooming Glove Set
4. Collection: Pet Hair Cleanup Essentials
5. Landing page: Pet Hair Cleanup Essentials
6. Shipping Policy and Return/Refund Policy for China-direct testing

The workflow emphasizes real execution in Shopify Admin, not just advice. Use the user's logged-in local Chromium browser through CDP when cloud browser sessions hit Shopify login, Cloudflare, or cookie isolation.

## When to Use

Use this skill when the user wants to:

- Research Shopify product directions for low-budget dropshipping / China-direct testing
- Choose lightweight, non-sensitive, low-risk ecommerce products
- Build a first Shopify product line around one hero SKU + add-on + bundle
- Create Shopify products, collections, pages, and policies in the actual admin
- Use local Chrome/Edge CDP at `127.0.0.1:9222` to operate an already logged-in Shopify session
- Set up first product-page/landing-page structure before adding supplier images, DSers/CJ, or pixels

Do **not** use this for:

- Medical, supplement, cosmetics, food, weapons, adult, tobacco, alcohol, CBD, or regulated products
- Products requiring high-certification compliance unless the user explicitly accepts that risk
- Copying supplier/marketplace images without permission
- Pretending DSers/CJ/TikTok/Meta are connected without account authorization and pixel IDs

## User and Product Constraints

Default assumptions from this launch pattern:

- Seller is a Canada-based student with limited budget
- No inventory at the start; test first via Shopify
- Target markets: US and Canada by default
- Advantage: can source from China
- Product constraints:
  - lightweight and small
  - non-fragile
  - no battery or minimal electronics
  - non-food, non-drug, non-supplement, non-medical
  - no imitation brands or IP-risk products
  - not clothing/size-dependent high-return SKUs
  - visually demonstrable in short-form video
  - feasible China sourcing and direct fulfillment
  - target selling price ideally around USD/CAD 30–80 for main/bundle offers, lower for add-ons only

## Research Workflow

### 1. Find audiences first

Research at least 10 potential audiences before picking products. Useful starting audiences:

- Pet owners
- Car owners
- Fitness beginners
- Small apartment renters
- Desk/office workers
- Travelers
- Outdoor users
- Students
- Gamers
- Home organization enthusiasts

For each audience, evaluate:

- Who they are
- Specific repeated pain points
- Willingness to pay
- Suitability for Shopify ad conversion
- Whether the problem is visible enough for TikTok/Reels demos

### 2. Find demand and keywords

For each promising audience, collect:

- Google/SEO trend signals where available
- Common search keywords
- Long-tail keywords
- TikTok/Instagram/YouTube Shorts content angles
- Reddit/Quora/Amazon review pain points
- Common complaints
- Products users are already buying

For pet hair cleanup, useful keyword themes include:

- pet hair remover
- reusable pet hair remover
- pet hair remover roller
- dog hair remover for couch
- cat hair remover for furniture
- pet hair remover for car seats
- reusable lint roller for pet hair
- pet grooming glove
- dog shedding glove
- cat grooming glove

### 3. Find products

Search across Amazon, TikTok, AliExpress, 1688, Temu, Etsy, eBay, Pinterest, Meta Ad Library, and TikTok Creative Center where available.

For the pet hair launch, the product logic was:

- Hero SKU: reusable pet hair remover roller
- Add-on: reusable pet hair removal glove
- Bundle: roller + glove set

Why this combination works:

- Lightweight
- Manual/no battery
- Non-sensitive product category
- Clear before/after content potential
- Easy to understand in 3 seconds
- Solves a recurring pet-owner pain
- Bundle increases AOV without adding much complexity

### 4. Score products

Use this 100-point scoring model:

- Pain intensity: 20
- Search demand: 15
- Social content potential: 15
- Existing purchase demand on Amazon/Etsy/TikTok: 15
- China supply feasibility: 10
- Low logistics difficulty: 10
- Margin potential: 10
- Competitor weakness clarity: 5

Automatically reject:

- Food, medicine, supplements, cosmetics, medical devices
- IP-risk products, lookalikes, branded/trademark-adjacent goods
- Large/heavy/fragile products
- Size-dependent apparel with high returns
- Strong-certification products
- Adult products, weapons, self-defense products, tobacco, alcohol, CBD
- Products with too-low AOV for paid ads

## Shopify Admin Access via Local CDP

### When needed

Use local CDP if the browser tool lands on Shopify login, Cloudflare, or a separate unauthenticated browser session.

### Launch Chrome or Edge with CDP on Windows Git Bash

Chrome:

```bash
"/c/Program Files/Google/Chrome/Application/chrome.exe" \
  --remote-debugging-port=9222 \
  --user-data-dir="$HOME/.hermes/chrome-debug" \
  --no-first-run \
  --no-default-browser-check
```

Edge:

```bash
"/c/Program Files (x86)/Microsoft/Edge/Application/msedge.exe" \
  --remote-debugging-port=9222 \
  --user-data-dir="$HOME/.hermes/edge-debug" \
  --no-first-run \
  --no-default-browser-check
```

Then have the user log into Shopify in that browser.

### Verify CDP

```bash
curl -sS http://127.0.0.1:9222/json/version
curl -sS http://127.0.0.1:9222/json/list
```

Find a page with `admin.shopify.com` and use its `webSocketDebuggerUrl`.

### Python CDP pattern

Chrome may reject websocket connections unless `suppress_origin=True` is used.

```python
import json, requests, websocket

CDP = 'http://127.0.0.1:9222'

def shopify_tab():
    for t in requests.get(CDP + '/json/list').json():
        if t.get('type') == 'page' and 'admin.shopify.com' in t.get('url', ''):
            return t
    raise RuntimeError('No Shopify Admin tab found')

class CDPClient:
    def __init__(self, ws_url):
        self.ws = websocket.create_connection(ws_url, timeout=30, suppress_origin=True)
        self.i = 0

    def call(self, method, params=None):
        self.i += 1
        msg = {'id': self.i, 'method': method}
        if params is not None:
            msg['params'] = params
        self.ws.send(json.dumps(msg))
        while True:
            r = json.loads(self.ws.recv())
            if r.get('id') == self.i:
                return r

    def eval(self, expr, await_promise=True):
        return self.call('Runtime.evaluate', {
            'expression': expr,
            'awaitPromise': await_promise,
            'returnByValue': True,
        })
```

## Shopify Field-Filling Notes

Shopify Admin uses shadow DOM and TinyMCE-like rich text editors. Normal selectors often miss fields.

Use a recursive shadow-DOM query:

```javascript
const deepQuery = (selector, root = document) => {
  const direct = root.querySelector?.(selector);
  if (direct) return direct;
  const all = root.querySelectorAll ? [...root.querySelectorAll('*')] : [];
  for (const el of all) {
    if (el.shadowRoot) {
      const found = deepQuery(selector, el.shadowRoot);
      if (found) return found;
    }
  }
  return null;
};
```

Use native value setters and dispatch input/change events:

```javascript
const setVal = (el, val) => {
  if (!el) throw new Error('missing element for value ' + val);
  const proto = el.tagName === 'TEXTAREA'
    ? HTMLTextAreaElement.prototype
    : HTMLInputElement.prototype;
  const setter = Object.getOwnPropertyDescriptor(proto, 'value').set;
  setter.call(el, val);
  el.dispatchEvent(new InputEvent('input', {
    bubbles: true,
    composed: true,
    inputType: 'insertText',
    data: val,
  }));
  el.dispatchEvent(new Event('change', {bubbles: true, composed: true}));
  el.dispatchEvent(new Event('blur', {bubbles: true, composed: true}));
};
```

For rich text:

```javascript
if (window.tinymce?.activeEditor) {
  window.tinymce.activeEditor.setContent(html);
  window.tinymce.activeEditor.save();
  window.tinymce.activeEditor.fire('change');
} else {
  setVal(deepQuery('textarea'), html);
}
```

## Product Setup Used in This Launch

### Product 1: Reusable Pet Hair Remover Roller

Suggested fields:

- Title: `Reusable Pet Hair Remover Roller`
- SKU: `PET-HAIR-ROLLER-001`
- Price: `22.99 CAD` in a Canadian Shopify store
- Weight: `0.18 kg`
- Positioning: hero SKU
- Best surfaces: couches, upholstered chairs, car seats, pet beds, blankets, bedding
- Expectation setting: works best on smooth fabric; less effective on deep carpet, textured knits, or deeply embedded hair

### Product 2: Reusable Pet Hair Removal Glove

Suggested fields:

- Title: `Reusable Pet Hair Removal Glove`
- SKU: `PET-HAIR-GLOVE-001`
- Price: `12.99 CAD`
- Weight: `0.08 kg`
- Positioning: add-on / upsell
- Notes: grooming accessory, not a medical product; use gently and stop if pet is uncomfortable

### Product 3: Pet Hair Roller + Grooming Glove Set

Suggested fields:

- Title: `Pet Hair Roller + Grooming Glove Set`
- SKU: `PET-HAIR-BUNDLE-001`
- Price: `34.99 CAD`
- Weight: `0.28 kg`
- Positioning: bundle to increase AOV and give a complete two-step routine
- Includes: roller + glove

## Collection Setup

Create a manual collection:

- Title: `Pet Hair Cleanup Essentials`
- Handle/path: `/collections/pet-hair-cleanup-essentials`
- Description:

```html
<p>Pet hair cleanup tools for couches, car seats, pet beds, blankets, and everyday shedding. Start with the reusable roller, add the grooming glove, or choose the bundle for a complete low-waste cleanup routine.</p>
```

Add these products:

1. Pet Hair Roller + Grooming Glove Set
2. Reusable Pet Hair Removal Glove
3. Reusable Pet Hair Remover Roller

Verify saved state by reopening the collection and checking all three products appear as Active.

## Landing Page Setup

Create an Online Store Page:

- Title: `Pet Hair Cleanup Essentials`
- Handle/path: `/pages/pet-hair-cleanup-essentials`
- CTA link: `/collections/pet-hair-cleanup-essentials`

Landing page structure:

```html
<h2>Clean pet hair from couches, car seats, bedding, and pet beds — without sticky lint roller refills.</h2>
<p>If you live with cats or dogs, loose fur shows up everywhere: sofa cushions, blankets, car interiors, and pet beds. Our Pet Hair Cleanup Essentials collection is built around simple reusable tools that are easy to demonstrate, easy to store, and practical for everyday pet homes.</p>
<h3>Choose your cleanup routine</h3>
<ul>
<li><strong>Reusable Pet Hair Remover Roller:</strong> best first choice for couches, car seats, pet beds, and blankets.</li>
<li><strong>Reusable Pet Hair Removal Glove:</strong> a lightweight grooming add-on to collect loose shedding fur before it spreads.</li>
<li><strong>Roller + Glove Set:</strong> the complete two-step routine for cleaning the pet and the home.</li>
</ul>
<p><a href="/collections/pet-hair-cleanup-essentials">Shop the Pet Hair Cleanup Essentials collection</a></p>
```

## Policies

### Shipping Policy

Use a conservative China-direct policy unless the user has confirmed a faster 3PL/warehouse route:

- Processing time: 1–4 business days
- Delivery estimate: 7–20 business days after shipment
- Tracking may take several days to update
- Address accuracy is the customer's responsibility
- Customs/import fees, if any, are the customer's responsibility

### Return and Refund Policy

Use expectation-setting for personal-use pet grooming/cleanup items:

- Damaged/defective/wrong items: contact within 7 days with photos and order number
- Returns: unused, clean, original packaging, requested within 14 days of delivery
- Non-returnable: used grooming items, pet hair/odor/stained items, misuse, customer address errors
- Shipping fees non-refundable unless store error
- Orders cannot be cancelled after shipment

Warn the user: policy templates are not legal advice. They should review requirements for their selling region, target markets, and Shopify Payments.

## Product Images

Do not add images unless they are legally usable. Acceptable sources:

- User-provided photos
- Supplier photos with explicit permission
- Licensed/stock photos compatible with commercial ecommerce use
- Self-shot sample photos/videos

Avoid:

- Copying Amazon/Temu/SHEIN/AliExpress competitor images without permission
- Using supplier photos that include watermarks, brand marks, or unrelated logos
- Using AI mockups as if they are exact product photos unless clearly validated

## Fulfillment Connections

Do not claim fulfillment apps are connected unless actually authorized.

Common options:

- DSers for AliExpress mapping
- CJ Dropshipping for supplier/fulfillment sourcing
- Zendrop / AutoDS if user already has accounts

Needed from user:

- App installed/authorized in Shopify
- Supplier product URL or selected SKU
- Shipping route and delivery estimate
- Variant mapping
- Cost and shipping quote
- Whether auto-fulfillment is enabled

SHEIN is generally not recommended as a direct fulfillment source because it is a retail marketplace and may cause packaging, invoice, return, resale, and IP/content risks.

## Pixel Setup

Do not set TikTok Pixel or Meta Pixel without:

- TikTok Business/Event Manager access or Pixel ID
- Meta Business Manager/Events Manager access or Pixel ID
- User decision on official Shopify apps vs manual/custom pixel setup

Recommended order:

1. Finish product/collection/page setup
2. Add legal product images
3. Confirm payment + shipping settings
4. Connect DSers/CJ or chosen fulfillment app
5. Install TikTok/Facebook sales channel apps
6. Add pixels and verify events
7. Run a test checkout/event verification

## Homepage / Theme Next Steps

After product, collection, landing page, and policies exist, build the storefront:

- Hero section: pet hair problem + before/after promise
- Featured collection: Pet Hair Cleanup Essentials
- Bundle highlight: Roller + Glove Set
- Short UGC video/demo section
- Benefits: reusable, no batteries, no sticky refills, lightweight
- FAQ: surfaces, shipping time, returns, how to clean, not ideal surfaces
- Policy snippets: shipping estimate and return rules
- Add collection to main navigation/footer

## Verification Checklist

- [ ] Products exist and are Active
- [ ] Titles, prices, SKUs, weights are saved
- [ ] Descriptions are original and expectation-setting is clear
- [ ] Collection exists at `/collections/pet-hair-cleanup-essentials`
- [ ] Collection contains all three products
- [ ] Landing page exists at `/pages/pet-hair-cleanup-essentials`
- [ ] Landing page CTA links to the collection
- [ ] Shipping policy is published and no longer says `No policy set`
- [ ] Return/refund policy is published and no longer says `No policy set`
- [ ] No unlicensed images were uploaded
- [ ] DSers/CJ connection is not claimed unless verified
- [ ] TikTok/Meta pixel is not claimed unless ID/app/event verification is done

## Common Pitfalls

1. **Cloud browser is not the user's browser.** Shopify login cookies may not exist there. Use local CDP if blocked.
2. **Shopify fields hide in shadow DOM.** Use `deepQuery`, not simple selectors only.
3. **TinyMCE textarea value may show length 0 even when editor content exists.** Verify via editor text, page body preview, or saved storefront/admin snippet.
4. **Collection product selection may require checking checkboxes then clicking modal Add, then page Save.** Verify the collection product list after saving.
5. **Policy modal may say saved but list status can lag until refresh.** Reload and verify policy labels no longer show `No policy set`.
6. **Don't overpromise shipping.** For China-direct, say estimated delivery and make clear it is not guaranteed.
7. **Don't upload stolen product photos.** Product images are a common early-store risk.
8. **Do not call policy templates legal advice.** Always recommend user review for Canada/US compliance.

## One-Shot Launch Sequence

1. Research audience and select hero problem/product.
2. Create 3 products: hero, add-on, bundle.
3. Create collection and add all products.
4. Create landing page with CTA to collection.
5. Publish shipping policy and return/refund policy.
6. Add legal product images and homepage sections.
7. Connect fulfillment app and pixels only after user provides authorization/IDs.
