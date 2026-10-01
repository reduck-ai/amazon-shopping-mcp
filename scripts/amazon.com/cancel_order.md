# Cancel Amazon order

Automatically cancel Amazon order on amazon.com. Cancel an Amazon.com order that has not shipped yet, by order number, and confirm the cancellation on the order page. Every item of the order is cancelled; returns the item titles and the order's status afterwards. Orders that already shipped cannot be cancelled this way and fail.

- Site: amazon.com
- Address: `reduck/amazon.com/cancel_order`
- Updated: 2026-09-27 (v2)
- Author: Reduck AI (reduck)

## Run it

Ask an AI agent connected to Reduck over MCP (`https://mcp.reduck.ai/mcp`) to run `reduck/amazon.com/cancel_order`, or run it from a terminal:

```bash
npx @reduck-ai/cli@latest run --script reduck/amazon.com/cancel_order
```

## Input

- `order_id` (string, required): Amazon order number, e.g. 113-1814615-7224222 (as shown in Your Orders).

## Output

- `items` (array, required): Titles of the items the cancellation was requested for.
- `order_id` (string, required)
- `cancelled` (boolean, required): Whether the order page, reloaded after the request, no longer offers to cancel any item.
- `status` (string | null, optional): Shipment status headline on the order page after the request, as displayed (e.g. Cancelled).

## FAQ

### What does "Cancel Amazon order" do?

Cancel an Amazon.com order that has not shipped yet, by order number, and confirm the cancellation on the order page. Every item of the order is cancelled; returns the item titles and the order's status afterwards. Orders that already shipped cannot be cancelled this way and fail.

### How do I automatically cancel Amazon order on amazon.com?

Ask an AI agent connected to Reduck to run reduck/amazon.com/cancel_order, or run it from a terminal with the Reduck CLI: npx @reduck-ai/cli@latest run --script reduck/amazon.com/cancel_order

### Is there a amazon.com API to cancel Amazon order?

You do not need one. "Cancel Amazon order" drives the real amazon.com pages in a browser, so it works whether or not amazon.com offers an API for this.

### What information do I need to provide?

Required: order_id.

### What does it return?

It returns items, status, order_id, cancelled.

### Do I need to be logged in to amazon.com?

Yes. It acts as you on amazon.com: on your own Chrome it reuses your session, and on a Reduck-hosted browser it loads the amazon.com cookies saved by the Reduck extension.

### Does it change anything on amazon.com, or only read data?

It makes changes on amazon.com, like sending, posting, booking or buying something.

### How do I run it?

Ask an AI agent connected to Reduck to run reduck/amazon.com/cancel_order, or run it from a terminal with the Reduck CLI: npx @reduck-ai/cli@latest run --script reduck/amazon.com/cancel_order

### Who maintains it?

It is part of Reduck's official curated catalogue.

Source: https://reduck.ai/explore/scripts/reduck/amazon.com/cancel_order
