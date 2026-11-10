# Check out Amazon cart

Automatically check out Amazon cart on amazon.com. Check out your Amazon.com shopping cart in two steps: review the checkout, then order exactly what you reviewed. It checks out the selected cart items with the account's default delivery address, payment method and delivery option, or with the address, card (payment) and delivery_option you pass. With place_order false (the default) it orders nothing and returns the whole checkout: recipient, delivery address, payment method, each item with its ASIN, quantity and price, the delivery options, the order summary, and a review_hash. To order, run it again with place_order true, that review_hash and the same choices: it opens the checkout again and orders only if the recipient, address, payment method, items, selected delivery options and total are still the same. If one changed, it orders nothing and fails with the checkout as it is now, so you can check it and pass its new review_hash. Returns the order number(s), which Cancel Amazon order takes. Fails on an empty cart.

- Site: amazon.com
- Address: `reduck/amazon.com/checkout_cart`
- Updated: 2026-11-02 (v10)
- Author: Reduck AI (reduck)

## Run it

Ask an AI agent connected to Reduck over MCP (`https://mcp.reduck.ai/mcp`) to run `reduck/amazon.com/checkout_cart`, or run it from a terminal:

```bash
npx @reduck-ai/cli@latest run --script reduck/amazon.com/checkout_cart
```

## Input

- `address` (string, optional): The delivery address as the account lists it: the recipient's name, then the address line (for example Jane Doe, 12 Main Street). It must match exactly one of the account's addresses; otherwise nothing is ordered and the run fails with the list. Omit it to keep Amazon's choice. Pass the same value to the review and to the order.
- `payment` (string, optional): The last 4 digits of the card to pay with. It must match exactly one card of the account; otherwise nothing is ordered and the run fails with the cards. Omit it to keep Amazon's choice. Pass the same value to the review and to the order.
- `place_order` (boolean, optional): false: order nothing and return the checkout with its review_hash. true: place the order, which needs review_hash.
- `review_hash` (string, optional): Required with place_order true. The review_hash of the checkout you reviewed. The order is placed only if the checkout still has the same hash (same recipient, address, payment method, items, delivery options and total); otherwise nothing is ordered and the run fails with the checkout as it is now.
- `delivery_option` (string, optional): The id of a delivery option from delivery_options of a review (for example premium-next-fr), chosen in every delivery group. If a group does not offer it, nothing is ordered and the run fails with the options offered. Omit it to keep Amazon's choice. Pass the same value to the review and to the order.

## Output

- `url` (string, required): Checkout page URL (stage checkout), or the confirmation or payment verification page URL (stage ordered).
- `stage` (string, required)
- `groups` (array, required): The checkout's delivery groups: the items that ship together, with their delivery options.
- `totals` (array, required): Order summary lines in page order; the last one is the order total. type is Amazon's own line code (for example ITEMS_TAX_EXCLUSIVE), null for the total.
- `order_ids` (array, required): Order numbers created by this purchase (one checkout can split into several orders), as shown in Your Orders. Pass one to Cancel Amazon order.
- `review_hash` (string, required): Hash of the recipient, address, payment method, items, selected delivery options and order total shown. Pass it to place the order: the order is placed only while the checkout has the same hash.
- `checkout_url` (string, required): URL of the checkout page that was read.
- `payment_verification_required` (boolean, required): True when the card issuer asked the cardholder to verify the payment (for example in their bank app) instead of showing the confirmation page. The order exists but waits for that approval.
- `address` (string | null, optional): Delivery address the checkout uses.
- `payment` (string | null, optional): Payment method the checkout uses, as displayed (for example Paying with Mastercard 1234).
- `recipient` (string | null, optional): Who receives the order, as the checkout shows it (for example Deliver to Jane Doe).
- `order_total` (string | null, optional)
- `purchase_id` (string | null, optional): Amazon's id for the checkout itself; not an order number.

## FAQ

### What does "Check out Amazon cart" do?

Check out your Amazon.com shopping cart in two steps: review the checkout, then order exactly what you reviewed. It checks out the selected cart items with the account's default delivery address, payment method and delivery option, or with the address, card (payment) and delivery_option you pass. With place_order false (the default) it orders nothing and returns the whole checkout: recipient, delivery address, payment method, each item with its ASIN, quantity and price, the delivery options, the order summary, and a review_hash. To order, run it again with place_order true, that review_hash and the same choices: it opens the checkout again and orders only if the recipient, address, payment method, items, selected delivery options and total are still the same. If one changed, it orders nothing and fails with the checkout as it is now, so you can check it and pass its new review_hash. Returns the order number(s), which Cancel Amazon order takes. Fails on an empty cart.

### How do I automatically check out Amazon cart on amazon.com?

Ask an AI agent connected to Reduck to run reduck/amazon.com/checkout_cart, or run it from a terminal with the Reduck CLI: npx @reduck-ai/cli@latest run --script reduck/amazon.com/checkout_cart

### Is there a amazon.com API to check out Amazon cart?

You do not need one. "Check out Amazon cart" drives the real amazon.com pages in a browser, so it works whether or not amazon.com offers an API for this.

### What information do I need to provide?

Optional: address, payment, place_order, review_hash, delivery_option.

### What does it return?

It returns url, stage, groups, totals, address, payment, order_ids, recipient, order_total, purchase_id, review_hash, checkout_url, payment_verification_required.

### Do I need to be logged in to amazon.com?

Yes. It acts as you on amazon.com: on your own Chrome it reuses your session, and on a Reduck-hosted browser it loads the amazon.com cookies saved by the Reduck extension.

### Does it change anything on amazon.com, or only read data?

It makes changes on amazon.com, like sending, posting, booking or buying something.

### How do I run it?

Ask an AI agent connected to Reduck to run reduck/amazon.com/checkout_cart, or run it from a terminal with the Reduck CLI: npx @reduck-ai/cli@latest run --script reduck/amazon.com/checkout_cart

### Who maintains it?

It is part of Reduck's official curated catalogue.

Source: https://reduck.ai/explore/scripts/reduck/amazon.com/checkout_cart
