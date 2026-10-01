# Remove Amazon product from cart

Automatically remove Amazon product from cart on amazon.com. Remove a product from your Amazon.com shopping cart by ASIN, whatever its quantity, and return what is left in the cart. A product that is not in the cart is reported as not present rather than failing.

- Site: amazon.com
- Address: `reduck/amazon.com/remove_from_cart`
- Updated: 2026-09-27 (v2)
- Author: Reduck AI (reduck)

## Run it

Ask an AI agent connected to Reduck over MCP (`https://mcp.reduck.ai/mcp`) to run `reduck/amazon.com/remove_from_cart`, or run it from a terminal:

```bash
npx @reduck-ai/cli@latest run --script reduck/amazon.com/remove_from_cart
```

## Input

- `asin` (string, required): ASIN of the cart line to delete.

## Output

- `asin` (string, required)
- `remaining` (array, required)
- `was_present` (boolean, required)
- `removed_quantity` (integer | null, optional)

## FAQ

### What does "Remove Amazon product from cart" do?

Remove a product from your Amazon.com shopping cart by ASIN, whatever its quantity, and return what is left in the cart. A product that is not in the cart is reported as not present rather than failing.

### How do I automatically remove Amazon product from cart on amazon.com?

Ask an AI agent connected to Reduck to run reduck/amazon.com/remove_from_cart, or run it from a terminal with the Reduck CLI: npx @reduck-ai/cli@latest run --script reduck/amazon.com/remove_from_cart

### Is there a amazon.com API to remove Amazon product from cart?

You do not need one. "Remove Amazon product from cart" drives the real amazon.com pages in a browser, so it works whether or not amazon.com offers an API for this.

### What information do I need to provide?

Required: asin.

### What does it return?

It returns asin, remaining, was_present, removed_quantity.

### Do I need to be logged in to amazon.com?

Yes. It acts as you on amazon.com: on your own Chrome it reuses your session, and on a Reduck-hosted browser it loads the amazon.com cookies saved by the Reduck extension.

### Does it change anything on amazon.com, or only read data?

It makes changes on amazon.com, like sending, posting, booking or buying something.

### How do I run it?

Ask an AI agent connected to Reduck to run reduck/amazon.com/remove_from_cart, or run it from a terminal with the Reduck CLI: npx @reduck-ai/cli@latest run --script reduck/amazon.com/remove_from_cart

### Who maintains it?

It is part of Reduck's official curated catalogue.

Source: https://reduck.ai/explore/scripts/reduck/amazon.com/remove_from_cart
