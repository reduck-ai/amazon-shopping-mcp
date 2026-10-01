# Amazon Shopping MCP

An Amazon shopping MCP server that shops as you. Let Claude, ChatGPT or any MCP client add to cart, review the checkout, place the order and cancel it, in your own Chrome, with no API key.

## Overview

An AI agent can already compare products for you. The part it usually cannot do is the last one: put the item in your Amazon cart, go through checkout with your address and card, and place the order, while you keep the last word.

## Why it's hard

Amazon has no API for shoppers. The Product Advertising API is for affiliates, and its checkout stops at a link you finish yourself. The community Amazon MCP servers drive a browser that you must log in to separately, and many stop at the cart. Checkout also changes from one order to the next: Amazon can ask you to choose a delivery address, delivery options change the price, import fees appear, and your bank can ask you to approve the payment. An MCP server that ignores those steps fails on a real account.

## How Reduck does it

Reduck is an MCP server whose Amazon scripts run in your own Chrome, where you are already signed in. Your agent works with your real cart, your saved addresses and your payment methods. It opens the checkout and stops there by default, so it can show you what Amazon shows before anything is bought. When you say yes, it places the order and returns the order number, which it can also use to cancel the order before it ships.

There are two ways to buy. The fast way places the order in one call. The review way keeps one browser open across calls: open the checkout, read it, then place it.

## What your agent does

- Add a product to your cart, list what is in it, and remove a line
- Buy one product now, or check out the whole cart, including pre-orders
- Stop on the checkout page and read the address, payment method, delivery options and total
- Place the order when you confirm, and return the order number
- Tell you when your bank asks to approve the payment
- Cancel an order that has not shipped, and confirm it on the order page

## API-based, browser MCP or Reduck

| | API-based Amazon MCP | Browser Amazon MCP | Reduck |
|---|---|---|---|
| Setup | Affiliate credentials | A separate browser you log in to | Stay signed in to Amazon in Chrome |
| Places the order | No, gives a checkout link | Varies | Yes, after a checkout you can review |
| Cancels an order | No | Not documented | Yes |
| Address and bank approval steps | Not reached | Not documented | Handled and reported |
| Acts as | An affiliate app | A logged-in automation | You |

## Who it's for

- Developers who give Claude Code, Cursor or their own agent the ability to buy
- Anyone who wants their assistant to order for them, with a review step first
- Ops and office managers who reorder supplies from one Amazon account

## FAQ

### Is there an official Amazon MCP server for shoppers?

No. Amazon publishes an MCP server for Amazon Business procurement and a connector for sellers, not one for a personal shopping account. The Amazon shopping MCP servers on GitHub and in MCP directories are community projects. Reduck is an MCP server too, and its Amazon scripts run in your own signed-in Chrome.

### Can it actually place an order, or only fill the cart?

It places real orders. By default your agent stops on the checkout page and shows you the address, the payment method, the delivery options and the total. It places the order when you confirm, and returns the order number.

### Can my agent cancel an order?

Yes. While the order has not shipped, the Cancel order script cancels it from Your Orders and reads the order page back to confirm the status.

### What if my bank asks me to approve the payment?

Some banks ask for an approval in their app (3-D Secure). The order exists but waits for that approval. The scripts say so in their result and give you the order number, so you can approve it or cancel the order.

### Do I need an Amazon API key or my password?

No. There is no API key, no Associates account and no password to give. You stay signed in to Amazon in your own Chrome, and the Reduck extension runs each script there, with your saved addresses and payment methods.

### Does it work with Claude Code, Cursor and ChatGPT?

Yes. Reduck connects to Claude, Claude Code, ChatGPT, Codex and any other MCP client. You ask in plain words, and the agent picks the Amazon scripts it needs.

### What about Amazon's rules on shopping agents?

Each script runs only when you or your agent asks for it, one at a time, in your own browser, signed in as you, and every order goes through a checkout you can review first. Amazon's Conditions of Use apply to you as they do when you shop yourself; decide whether that fits how you use your account.

Source: https://reduck.ai/use-cases/amazon-shopping-mcp
