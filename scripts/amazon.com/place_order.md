# Place Amazon order from checkout

Place the order on an open Amazon.com checkout and get its order number(s), to track the order or cancel it. It places the checkout open in the current session as it stands (address, payment, delivery options), so run it in the same session after Buy Amazon product now or Check out Amazon cart stopped at checkout. Returns the order number(s) from Your Orders, the order total that was shown, and whether the card issuer asked for a payment verification (for example in the bank app). This spends money.

- Site: amazon.com
- Address: `reduck/amazon.com/place_order`
- Updated: 2026-09-27 (v5)
- Author: Reduck AI (reduck)

## Run it

Ask an AI agent connected to Reduck over MCP (`https://mcp.reduck.ai/mcp`) to run `reduck/amazon.com/place_order`, or run it from a terminal:

```bash
npx @reduck-ai/cli@latest run --script reduck/amazon.com/place_order
```

## Input

It takes no input.

## Output

- `order_ids` (array, required): Order numbers created by this purchase (one checkout can split into several orders), as shown in Your Orders. Pass one to Cancel Amazon order.
- `confirmation_url` (string, required)
- `payment_verification_required` (boolean, required): True when the card issuer asked the cardholder to verify the payment (for example in their bank app) instead of showing the confirmation page. The order exists but waits for that approval.
- `order_total` (string | null, optional): Order total shown on the checkout page when the order was placed.
- `purchase_id` (string | null, optional): Amazon's id for the checkout itself; not an order number.

## FAQ

### What does "Place Amazon order from checkout" do?

Place the order on an open Amazon.com checkout and get its order number(s), to track the order or cancel it. It places the checkout open in the current session as it stands (address, payment, delivery options), so run it in the same session after Buy Amazon product now or Check out Amazon cart stopped at checkout. Returns the order number(s) from Your Orders, the order total that was shown, and whether the card issuer asked for a payment verification (for example in the bank app). This spends money.

### What information do I need to provide?

Nothing. It takes no input.

### What does it return?

It returns order_ids, order_total, purchase_id, confirmation_url, payment_verification_required.

### Do I need to be logged in to amazon.com?

Yes. It acts as you on amazon.com: on your own Chrome it reuses your session, and on a Reduck-hosted browser it loads the amazon.com cookies saved by the Reduck extension.

### Does it change anything on amazon.com, or only read data?

It makes changes on amazon.com, like sending, posting, booking or buying something.

### How do I run it?

Ask an AI agent connected to Reduck to run reduck/amazon.com/place_order, or run it from a terminal with the Reduck CLI: npx @reduck-ai/cli@latest run --script reduck/amazon.com/place_order

### Who maintains it?

It is part of Reduck's official curated catalogue.

Source: https://reduck.ai/explore/scripts/reduck/amazon.com/place_order
