# 📘 Order Books

**Date:** 2026-08-27
**Topic:** Market microstructure — the order book

---

## 1. What Is an Order Book?

An **order book** is the real-time list of all outstanding buy and sell orders for an instrument (a stock, FX pair, crypto asset, futures contract, etc.), organized by price level. It's maintained by the exchange or broker and updates continuously as traders submit, cancel, or fill orders.

Think of it as the live, transparent record of *who wants to buy at what price* and *who wants to sell at what price*, before any trade actually happens. Every executed trade in a market is the result of two orders meeting on the order book.

An order book is usually visualized as two stacked columns:

```
        BUY SIDE (Bids)          |          SELL SIDE (Asks)
   Price      Size                |    Price      Size
   -----      ----                |    -----      ----
   1923.40    12 lots             |    1923.60    9 lots
   1923.35    20 lots             |    1923.65    15 lots
   1923.30    8 lots              |    1923.70    22 lots
```

---

## 2. The Two Sides: Bid and Ask

- **Bid** — the price and quantity a buyer is willing to pay. The **best bid** is the *highest* price someone is currently offering to buy at.
- **Ask (offer)** — the price and quantity a seller is willing to accept. The **best ask** is the *lowest* price someone is currently willing to sell at.

Key intuition: bids are stacked from highest to lowest as you move away from the current price, and asks are stacked from lowest to highest. The "top of book" is the best bid and best ask — the two prices closest to each other.

- If you want to **buy immediately**, you pay the ask.
- If you want to **sell immediately**, you hit the bid.

---

## 3. The Spread

The **spread** is the gap between the best bid and the best ask:

```
Spread = Best Ask − Best Bid
```

Using the example above: `1923.60 − 1923.40 = 0.20` → a 20-point (or 20-pip-equivalent, depending on instrument) spread.

**Why the spread exists:**
- It's the compensation market makers/liquidity providers earn for standing ready to buy and sell at any moment.
- A **tight spread** usually signals a liquid, actively traded market (many participants, small gap between buyers and sellers).
- A **wide spread** usually signals low liquidity, high uncertainty, or a fast-moving/volatile market where liquidity providers widen quotes to protect themselves.

The spread is also a direct, real trading cost — every round-trip trade pays it, which is why spread cost matters a lot when backtesting anything with tight profit targets.

---

## 4. How Orders Are Executed

Two basic order types interact with the book differently:

- **Limit order** — specifies a price. It sits *in* the order book (adds to bid or ask depth) until a matching order arrives, or until it's cancelled. This is called being a **maker** (you provide liquidity).
- **Market order** — has no price; it says "fill me now at the best available price." It immediately consumes the best-priced orders sitting on the opposite side of the book. This is called being a **taker** (you remove liquidity).

**Matching logic — price-time priority:**
1. Orders are first matched by **best price** (highest bid meets lowest ask).
2. Among orders at the *same* price, the order that arrived **first in time** gets filled first (FIFO within a price level).

**Execution walkthrough:**
- Suppose the book looks like the example above (best bid 1923.40, best ask 1923.60).
- A trader sends a **market buy order for 5 lots**.
- It immediately matches against the best ask (1923.60), consuming 5 of the 9 lots resting there.
- The best ask price stays 1923.60 (4 lots now remain at that level) — the price only moves to the next level once a level is fully consumed.
- If the market order had been for 15 lots, it would consume all 9 lots at 1923.60, then "walk the book" and fill the remaining 6 lots at 1923.65 — this is **slippage**: the larger the order relative to visible depth, the worse the average fill price.

---
 ###  
-for more understanding view js_financials the orderbook

#####


## 🔑 Key Takeaways

- The order book is the mechanism, not just a display — it *is* the market.
- Bid = buyers, Ask = sellers, Spread = the cost of immediacy.
- Limit orders build the book (makers); market orders consume it (takers).
- Depth at each price level determines how much size can trade before price moves — this directly matters for slippage modeling in any execution-sensitive strategy.

## ❓ Open Questions for Next Session

- the impact of making a bid or ask in the market 
- liquidity:what is liquidity 
-differenciate between volume and liquidity
