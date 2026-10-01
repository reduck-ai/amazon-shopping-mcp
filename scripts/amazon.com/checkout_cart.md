# Check out Amazon cart

Automatically check out Amazon cart on amazon.com. Check out your Amazon.com shopping cart: stop at checkout to review it first, or place the order at once. It checks out the selected cart items with the account's default delivery address and payment method, confirming the preselected address when Amazon asks for one. By default it stops on the checkout page without ordering and returns the order total, address and payment method; to review and then place that checkout, run it in a session and follow with Get Amazon checkout information and Place Amazon order. With place_order set to true it places the order at once and returns the order number(s), which Cancel Amazon order takes. Fails on an empty cart.

- Site: amazon.com
- Address: `reduck/amazon.com/checkout_cart`
- Updated: 2026-09-27 (v4)
- Author: Reduck AI (reduck)

## Run it

Ask an AI agent connected to Reduck over MCP (`https://mcp.reduck.ai/mcp`) to run `reduck/amazon.com/checkout_cart`, or run it from a terminal:

```bash
npx @reduck-ai/cli@latest run --script reduck/amazon.com/checkout_cart
```

## Input

- `place_order` (boolean, optional): false: stop on the checkout page without ordering. To review and then place that checkout, run this inside a session (start_session, then pass its sessionId to this run and to Get Amazon checkout information and Place Amazon order); without a session the checkout page closes with the run. true: place the order immediately.

## Output

- `url` (string, required): Checkout page URL (stage checkout), or the confirmation or payment verification page URL (stage ordered).
- `stage` (string, required)
- `order_ids` (array, required): Order numbers created by this purchase (stage ordered), as shown in Your Orders. Pass one to Cancel Amazon order.
- `payment_verification_required` (boolean, required): True when the card issuer asked the cardholder to verify the payment (for example in their bank app) instead of showing the confirmation page. The order exists but waits for that approval.
- `address` (string | null, optional): Delivery address the checkout uses.
- `payment` (string | null, optional): Payment method the checkout uses, as displayed (e.g. Paying with Mastercard 1234).
- `order_total` (string | null, optional)
- `purchase_id` (string | null, optional): Amazon's id for the checkout itself (stage ordered); not an order number.

## FAQ

### What does "Check out Amazon cart" do?

Check out your Amazon.com shopping cart: stop at checkout to review it first, or place the order at once. It checks out the selected cart items with the account's default delivery address and payment method, confirming the preselected address when Amazon asks for one. By default it stops on the checkout page without ordering and returns the order total, address and payment method; to review and then place that checkout, run it in a session and follow with Get Amazon checkout information and Place Amazon order. With place_order set to true it places the order at once and returns the order number(s), which Cancel Amazon order takes. Fails on an empty cart.

### How do I automatically check out Amazon cart on amazon.com?

Ask an AI agent connected to Reduck to run reduck/amazon.com/checkout_cart, or run it from a terminal with the Reduck CLI: npx @reduck-ai/cli@latest run --script reduck/amazon.com/checkout_cart

### Is there a amazon.com API to check out Amazon cart?

You do not need one. "Check out Amazon cart" drives the real amazon.com pages in a browser, so it works whether or not amazon.com offers an API for this.

### What information do I need to provide?

Optional: place_order.

### What does it return?

It returns url, stage, address, payment, order_ids, order_total, purchase_id, payment_verification_required.

### Do I need to be logged in to amazon.com?

Yes. It acts as you on amazon.com: on your own Chrome it reuses your session, and on a Reduck-hosted browser it loads the amazon.com cookies saved by the Reduck extension.

### Does it change anything on amazon.com, or only read data?

It makes changes on amazon.com, like sending, posting, booking or buying something.

### How do I run it?

Ask an AI agent connected to Reduck to run reduck/amazon.com/checkout_cart, or run it from a terminal with the Reduck CLI: npx @reduck-ai/cli@latest run --script reduck/amazon.com/checkout_cart

### Who maintains it?

It is part of Reduck's official curated catalogue.

Source: https://reduck.ai/explore/scripts/reduck/amazon.com/checkout_cart
