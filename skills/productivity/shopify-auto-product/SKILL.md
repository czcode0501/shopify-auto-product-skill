---
name: shopify-auto-product
description: "Use when the user wants an end-to-end Shopify auto-product workflow: research current markets, find audiences and pain points, score product ideas, then produce or execute Shopify product, collection, page, policy, fulfillment, image, and pixel setup steps based on the latest available evidence."
version: 1.1.0
author: Hermes Agent
license: MIT
metadata:
  hermes:
    tags: [shopify, ecommerce, dropshipping, product-research, product-launch, cdp]
    related_skills: [shopify-store-operations, industry-dissection-template, agent-reach]
---

# Shopify Auto Product Workflow

## Overview

This skill is an open, reusable workflow for Shopify product research and launch execution. It is **not tied to any one store, niche, product, country, or prior project**. Use it whenever the user wants to find a Shopify test product, validate the opportunity with current evidence, and turn the result into concrete Shopify launch assets.

The workflow has two modes:

1. **Research mode** — discover audiences, pain points, keywords, social proof, competitors, suppliers, pricing, and risks using the latest available data.
2. **Execution mode** — create or update Shopify products, collections, landing pages, policies, navigation, images, fulfillment mappings, and pixel setup when the user has provided access and approvals.

Always adapt the output to the user's current market, budget, fulfillment model, and risk tolerance. Do not reuse a previous project's products, prices, SKUs, or store-specific details unless the user explicitly asks for that exact project.

## When to Use

Use this skill when the user asks to:

- Find Shopify product ideas automatically
- Research a niche or audience for ecommerce testing
- Build a low-budget dropshipping or China-direct test plan
- Score product ideas and choose what to test first
- Turn research into Shopify products, collections, landing pages, or policies
- Operate Shopify Admin through the user's logged-in browser session
- Prepare DSers, CJ Dropshipping, AliExpress, 1688, supplier, image, TikTok Pixel, or Meta Pixel next steps
- Produce a reusable execution plan that can be run again with fresh data

Do **not** use this skill to:

- Recommend regulated or high-risk products without warning
- Copy another store's product images or descriptions
- Pretend a fulfillment app, supplier, pixel, or Shopify setting is connected when it has not been verified
- Reuse historical project details as if they are generic best practice
- Give only abstract advice when the user asked for a working Shopify artifact

## Core Principles

1. **Current evidence first.** Search and verify current market signals before recommending products.
2. **Audience before product.** Start with people and pain points, then find products that solve them.
3. **Low-risk product filters.** Prefer lightweight, non-sensitive, non-fragile, non-regulated items suitable for direct fulfillment or later 3PL/warehouse migration.
4. **Short-form content fit.** Prefer products whose value can be shown in a 3–10 second TikTok/Reels demo.
5. **Execution over inspiration.** If the user asks to build in Shopify and access is available, create the actual artifact and verify it saved.
6. **No project leakage.** Keep the skill generic. Examples must be clearly labeled as examples, not embedded as the user's current product line.
7. **No false verification.** Mark evidence as insufficient when data is weak or access is missing.

## Default User Assumptions to Confirm or Override

If the user gives no extra context, assume:

- They want to start with low budget
- They do not want to hold inventory at first
- They prefer lightweight, non-sensitive products
- They are testing with Shopify first
- They may source from China and ship to overseas customers
- Main target markets are the US and Canada unless stated otherwise

Override these defaults whenever the user provides a different market, budget, fulfillment method, or risk preference.

## Product Risk Filters

Automatically reject or heavily penalize:

- Food, medicine, supplements, cosmetics, medical devices
- Products with strong certification or compliance requirements
- Weapons, self-defense items, adult products, tobacco, alcohol, CBD
- Large, heavy, fragile, or high-breakage products
- Clothing or shoes where sizing drives high returns
- Trademarked, branded, character, sports-team, or lookalike products
- Products with weak margins after ad spend and shipping
- Products that depend on exaggerated, medical, safety, or guaranteed-performance claims

Prefer products that are:

- Small and lightweight
- Non-fragile
- Manual or simple electronics only
- Easy to explain visually
- Easy to source from multiple suppliers
- Usable across US/Canada/UK/Australia without complex compliance
- Sellable as hero SKU + add-on + bundle
- Reasonably priced for paid social testing

## Research Workflow

### 1. Find audiences first

Research at least 10 potential audiences before choosing products. Example audience categories include:

- Pet owners
- Car owners
- Fitness beginners
- Small apartment renters
- Desk/office workers
- Travelers
- Outdoor users
- Students
- Gamers
- Home organization buyers
- Parents
- Beauty tool buyers
- Hobbyists and craft users
- Remote workers

For each audience, evaluate:

- Who they are
- Their specific repeated pain points
- Whether the pain is urgent, frequent, embarrassing, costly, or visually obvious
- Whether they already spend money on solutions
- Whether the problem is easy to demonstrate in short-form content
- Whether paid social traffic can convert without heavy education

### 2. Find demand and keywords

For each promising audience, gather current evidence from available sources:

- Google Search / SEO results
- Google Trends or comparable trend signals when available
- TikTok / Instagram / YouTube Shorts content patterns
- Reddit, Quora, forum, and review complaints
- Amazon, Etsy, eBay, TikTok Shop, Temu, AliExpress, 1688, or other marketplace demand
- Pinterest or visual-search demand where relevant
- Meta Ad Library / TikTok Creative Center / ad spy signals where accessible

For each audience/product cluster, record:

- Main search terms
- Long-tail search terms
- Pain-point phrases in the user's language
- Review complaints
- Competitor promises
- Common objections
- Existing products users buy
- Evidence gaps

### 3. Find product candidates

For each audience, identify products that solve the pain. For each candidate, collect:

- Product name / generic category name
- Pain solved
- Likely target buyer
- Marketplace demand signals
- Social-media content angles
- Competitor stores and offers
- China sourcing feasibility
- Estimated supplier cost
- Estimated shipping weight and dimensions
- Estimated overseas selling price
- Estimated gross margin before ad spend
- Compliance, IP, platform, and return-risk notes

### 4. Score candidates

Use this 100-point model:

| Criterion | Points |
|---|---:|
| Pain intensity | 20 |
| Search demand | 15 |
| Social content potential | 15 |
| Existing purchase demand | 15 |
| China supply feasibility | 10 |
| Low logistics difficulty | 10 |
| Margin potential | 10 |
| Competitor weakness clarity | 5 |

Output a scored table and mark each product as:

- **Test now** — strong enough for a first Shopify test
- **Watchlist** — promising but needs more data or better supplier validation
- **Reject** — risk, margin, demand, compliance, or differentiation is too weak

## Output Format for Product Research

When the user asks for research, return a concise but evidence-backed Markdown report:

### A. Best audiences

For each top audience:

- Audience profile
- Main pain points
- Search keywords
- Social content directions
- Product types that fit
- Evidence level: strong / medium / weak

### B. Best product candidates

For each product:

- Product name/category
- Corresponding audience
- Pain solved
- Likely overseas selling price
- Estimated sourcing cost
- Logistics difficulty
- Content/ad hook
- Main keywords
- Competitor weaknesses
- Risks
- Score out of 100
- Test recommendation

### C. Final recommendations

For the top 3:

- Why choose it
- Why it fits low-budget Shopify testing
- How to test with Shopify
- First TikTok/Reels ad concept
- Product page messaging
- China-direct suitability
- When to upgrade to overseas warehouse

### D. Today's action plan

Give a practical 7-step plan the user can execute today.

## Shopify Execution Workflow

Only perform live Shopify changes when the user asks for execution and access is available.

### 1. Access Shopify Admin

First try the browser tool. If blocked by Shopify login, Cloudflare, or a separate browser session, use the user's local Chrome/Edge via CDP.

Chrome on Windows Git Bash:

```bash
"/c/Program Files/Google/Chrome/Application/chrome.exe" \
  --remote-debugging-port=9222 \
  --user-data-dir="$HOME/.hermes/chrome-debug" \
  --no-first-run \
  --no-default-browser-check
```

Edge on Windows Git Bash:

```bash
"/c/Program Files (x86)/Microsoft/Edge/Application/msedge.exe" \
  --remote-debugging-port=9222 \
  --user-data-dir="$HOME/.hermes/edge-debug" \
  --no-first-run \
  --no-default-browser-check
```

Verify:

```bash
curl -sS http://127.0.0.1:9222/json/version
curl -sS http://127.0.0.1:9222/json/list
```

Find an `admin.shopify.com` page and use its `webSocketDebuggerUrl`.

### 2. CDP Python pattern

Use `suppress_origin=True` for recent Chromium builds:

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

### 3. Shopify field filling

Shopify Admin often uses shadow DOM and rich-text editors. Use recursive querying and native setters:

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

const setVal = (el, val) => {
  if (!el) throw new Error('missing element for value ' + val);
  const proto = el.tagName === 'TEXTAREA'
    ? HTMLTextAreaElement.prototype
    : HTMLInputElement.prototype;
  Object.getOwnPropertyDescriptor(proto, 'value').set.call(el, val);
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

## Generic Shopify Product Structure

For a first test, prefer this structure:

1. **Hero SKU** — the main product solving the clearest pain
2. **Add-on SKU** — cheap accessory or complementary item
3. **Bundle SKU** — hero + add-on to raise AOV
4. **Collection** — a focused collection around the problem/solution
5. **Landing page** — pain, solution, product choice, FAQ, CTA
6. **Policies** — shipping and returns aligned with real fulfillment

Do not hard-code product names, SKUs, prices, or weights from a past project. Generate them from the current research and supplier data.

### Product page sections

A strong generic product page should include:

- Clear headline focused on the pain solved
- Short subheadline explaining the outcome
- 3–5 benefit bullets
- Best-for section
- Not-ideal-for or expectation-setting section
- How it works
- Product details/specs
- Shipping/returns expectations
- FAQ
- SEO title and meta description

### Collection page sections

A focused collection should include:

- One-sentence problem/solution description
- The products included
- How to choose between them
- Link from homepage and navigation when ready

### Landing page sections

A launch landing page should include:

- Problem hook
- Why existing solutions are frustrating
- Product solution explanation
- Hero/add-on/bundle choice guide
- Before/after or demo section placeholder
- Benefits and objection handling
- FAQ
- CTA to product or collection

## Shipping Policy Template Logic

Generate the exact policy from the current fulfillment model. For China-direct testing, include:

- Processing time range
- Estimated delivery range
- Tracking update delay warning
- Address accuracy warning
- Customs/import fee responsibility
- Clear statement that delivery estimates are not guarantees

Do not say “fast shipping” unless the user has verified a fast route or overseas warehouse.

## Return and Refund Policy Template Logic

Generate from the product category and risk profile. Include:

- Damaged/defective/wrong item process
- Return request window
- Condition requirements
- Non-returnable conditions
- Refund method
- Cancellation cutoff
- Contact method

Warn that policy templates are not legal advice and should be reviewed for the user's region and target markets.

## Product Images and Media

Do not add images unless they are legally usable.

Acceptable:

- User-provided product photos
- Supplier photos with explicit permission
- Licensed commercial-use images
- Self-shot sample photos and videos
- Verified brand-owned creative

Avoid:

- Copying Amazon, Temu, SHEIN, Etsy, TikTok Shop, or competitor images
- Using watermarked supplier images
- Using logos, characters, trademarks, or brand marks without rights
- Presenting AI mockups as exact product photos without validation

Recommend a simple content plan:

1. Order or borrow a sample
2. Shoot vertical phone demos
3. Capture before/after scenes
4. Photograph packaging and product details
5. Use real customer-style UGC angles before paid ads

## Fulfillment Setup

Do not claim fulfillment is connected until verified.

Common paths:

- AliExpress + DSers
- CJ Dropshipping
- 1688 supplier + agent/3PL
- Zendrop / AutoDS / other fulfillment apps
- Manual orders during validation
- Overseas warehouse only after stable demand

Before mapping products, collect:

- Supplier URL
- SKU/variant data
- Cost and MOQ
- Shipping route and delivery estimate
- Destination countries
- Tracking availability
- Return/defect process
- Whether packaging has supplier branding

## Pixel Setup

Do not claim pixels are set until verified.

Needed:

- TikTok Pixel ID or TikTok app authorization
- Meta Pixel ID or Facebook & Instagram app authorization
- Business Manager / Events Manager access
- Domain/checkout constraints understood
- Test event verification after setup

Recommended event checks:

- PageView
- ViewContent
- AddToCart
- InitiateCheckout
- Purchase, when test checkout is possible

## Verification Checklist

Before reporting completion, verify the actual saved state:

- [ ] Research sources were current and cited or summarized honestly
- [ ] Rejected products and risks are documented
- [ ] Final product recommendations have scores
- [ ] Shopify products were saved, if execution was requested
- [ ] Product copy is original and not copied from competitors
- [ ] Collections contain the intended products
- [ ] Landing pages link to the intended products/collections
- [ ] Policies match the actual fulfillment model
- [ ] No unlicensed images were uploaded
- [ ] Fulfillment app connection is verified before claiming it
- [ ] Pixel events are tested before claiming they work
- [ ] No prior user's private project details are embedded in generic deliverables

## Common Pitfalls

1. **Embedding a past project as generic skill content.** Keep public skills general and use examples only when clearly labeled.
2. **Skipping current research.** A good product last month may be saturated now.
3. **Over-trusting marketplace sales.** Verify with reviews, complaints, ad creatives, and supplier economics.
4. **Ignoring ad economics.** Low product cost does not mean profitable after CAC, shipping, returns, and payment fees.
5. **Overpromising delivery.** China-direct shipping needs conservative delivery language.
6. **Using copyrighted images.** This creates avoidable store and ad-account risk.
7. **Assuming Shopify UI selectors are stable.** Verify fields after every save.
8. **Claiming integrations are done without event/API/app verification.** Always test.

## One-Shot Workflow

1. Gather user constraints: market, budget, inventory preference, fulfillment, risk limits.
2. Research 10 audiences and shortlist the strongest pain points.
3. Gather keyword, social, review, marketplace, competitor, and supplier evidence.
4. Score product candidates and choose the top 3.
5. Build a Shopify test plan: hero SKU, add-on, bundle, collection, landing page, policies.
6. Execute in Shopify if authorized and verify saved artifacts.
7. Prepare next steps for images, fulfillment, pixels, ads, and overseas warehouse timing.
