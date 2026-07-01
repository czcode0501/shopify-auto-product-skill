# shopify-auto-product skill

`shopify-auto-product` is an open-source Hermes Agent skill for end-to-end Shopify product research and launch workflows.

It is intentionally **generic**. It is not tied to one product, niche, store, or past project. Each time it is used, the agent should research the latest market evidence and generate a fresh plan based on the user's current situation.

## What it does

The skill helps an agent:

- research audiences before products
- identify pain points, keywords, reviews, competitors, ads, and marketplace demand
- score product ideas with a reusable 100-point framework
- reject high-risk products such as regulated, IP-risk, heavy, fragile, or low-margin items
- produce Shopify test plans with hero SKU, add-on, bundle, collection, and landing page structure
- operate Shopify Admin via browser/CDP when authorized
- draft shipping and refund policy logic aligned with actual fulfillment
- prepare image, supplier, DSers/CJ/AliExpress, TikTok Pixel, and Meta Pixel next steps

## Skill path

```text
skills/productivity/shopify-auto-product/SKILL.md
```

## How to use

Copy the `skills/productivity/shopify-auto-product` folder into a Hermes-compatible skills directory, or keep this repository as a shareable skill source.

In Hermes, refer to it as:

```text
shopify-auto-product
```

Example prompt:

```text
Use the shopify-auto-product skill to research the latest Shopify product opportunities for a low-budget test store and give me an execution plan.
```

## Important notes

- The skill should not reuse private project details as generic examples.
- It should use current research whenever product recommendations are requested.
- Policy templates are operational ecommerce drafts, not legal advice.
- Images, fulfillment apps, and pixels should only be marked complete after actual authorization and verification.

## License

MIT
