# Market Fundamentals — Work Log

**Date:** 2026-09-07
**Session focus:** map of the market system — WHO trades, WHAT they trade, and HOW price actually forms. 
---

## The Framework

Markets are easiest to reason about as three interacting layers:

1. **Participants** — the agents in the system, each with different objectives, constraints, information, and time horizons.
2. **Instruments** — what's actually being traded.
3. **Market mechanics / price formation** — the process by which a price gets set.

**Key insight to hold onto:** *the instrument is not necessarily the market.* The same underlying asset can trade through completely different structures. Gold, for example, trades as physical bullion OTC in London, as a standardized future on COMEX (exchange-traded, clearing-house-guaranteed), and as a CFD OTC through a retail broker — three different market structures, three different participant sets, three different price-formation processes, for the *same* underlying asset. This is why "what am I trading" and "where/how am I trading it" have to be answered separately.

Each section below tracks the full map from the original outline, with what's actually been covered marked off — so this file also works as a running checklist for what's left.

---

## 1. Market Participants — WHO is Acting

- [ ] Clearing houses
- [ ] Brokers
- [ ] Dealers / market makers
- [ ] Hedge funds
- [ ] Exchanges (as an institution — partially touched via OTC/exchange distinction, not yet covered in its own right)
- [ ] Banks
- [ ] Asset managers
- [ ] Pension funds
- [ ] Governments / central banks
- [ ] Corporations
- [ ] Retail traders and investors
- [ ] Arbitrageurs
- [ ] High-frequency / algorithmic traders

### 

**Clearing houses** — Sit between the two sides of a trade *after* it's agreed and become the counterparty to both, through a process called novation. Instead of Party A facing Party B directly, both now face the clearing house. This is what eliminates bilateral counterparty risk on exchange-traded instruments — backed by daily mark-to-market, margin requirements, and a mutualized guarantee fund. Historically an exchange-traded-market feature, though OTC swaps have increasingly moved to central clearing since the 2008 financial crisis.

**Brokers** — Act as an *agent* on behalf of a client, executing trades for a commission. Critically, a broker does not take the other side of your trade — they don't carry principal risk on the position itself. This is the core distinction from a dealer.

**Dealers / market makers** — Take the *other side* of a trade as principal, profiting from the bid-ask spread while carrying inventory risk (the risk of holding a position they didn't necessarily want, until it can be offloaded). This connects directly back to the order book session — market makers are the ones typically resting limit orders on both sides of the book.

**Hedge funds** — Pooled investment vehicles, generally for institutional/accredited investors, employing a wide strategy range (long/short equity, macro, quant/systematic, event-driven, arbitrage). Typically use leverage, are lighter-regulated than mutual funds, and charge a performance-based fee structure (classically "2 and 20" — 2% management fee, 20% of profits).

---

## 2. Financial Instruments — WHAT is Being Traded

- [x] Stocks / equities
- [x] Bonds
- [x] Futures
- [x] Forwards
- [x] Swaps (interest rate, commodity, currency, debt-equity)
- [ ] Options
- [ ] ETFs
- [ ] Currencies (as an instrument class in its own right)
- [ ] Commodities
- [ ] Indices
- [ ] Credit instruments
- [ ] Structured products

### 

**Stocks / equities** — Ownership claims on a company; a residual claim on earnings and assets after all debt obligations are satisfied. Returns come from capital appreciation and dividends.

**Bonds** — Debt instruments: the issuer borrows from the bondholder and commits to periodic coupon payments plus return of principal at maturity. Price and yield move inversely — this relationship is fundamental to how bond markets react to interest rate changes.

**Futures** — Standardized, exchange-traded contracts to buy or sell an asset at a future date for an agreed price. Marked-to-market daily and margined, with a clearing house guaranteeing performance on both sides. (Full mechanics — rolling, basis, contango/backwardation, and the gold-specific case — are the dedicated focus of Phase 3 Week 3.)

**Forwards** — The OTC counterpart to a future: customized, bilaterally negotiated between two counterparties, typically settled only at maturity rather than marked-to-market daily. Because there's no clearing house standing behind most forwards, counterparty risk is borne directly by both sides.

**Swaps** — An agreement between two counterparties to exchange cash flows over time. Four variants covered:
- **Interest rate swap** — exchanging fixed-rate payments for floating-rate payments (or vice versa) on a notional principal that itself never changes hands.
- **Commodity swap** — exchanging a fixed price for a floating (market) price of a commodity, used to hedge commodity price exposure without taking physical delivery.
- **Currency swap** — exchanging principal and interest payments denominated in one currency for principal and interest in another.
- **Debt-equity swap** — exchanging a debt claim for an equity stake, typically used in corporate restructuring when a lender converts what it's owed into ownership.

---

## 3. Market Mechanics & Price Formation — HOW Price Actually Moves

- [ ] Order book
- [ ] Bid / ask
- [ ] Spread
- [ ] OTC vs. exchange-traded distinction
- [ ] Order flow, liquidity, volume, volatility, market depth, imbalances, inventory, dealer positioning (partially implied by market maker notes above, not yet formally covered)
- [ ] Information arrival, expectations, interest rates, inflation, economic data, corporate earnings, monetary policy, fiscal policy
- [ ] Risk sentiment, positioning, leverage, forced liquidations
- [ ] Arbitrage, cross-market relationships

### 

**Order book, bid/ask, spread, execution** — Covered in full in `orderbook.md`: the book as the live record of resting orders, bid = buyers/ask = sellers, spread as the cost of immediacy, and how market orders consume resting liquidity (with slippage as size exceeds visible depth at the best price).

**OTC vs. exchange-traded structure** — The other major structural distinction, sitting one level up from any single order book:

| | Exchange-traded | OTC / dealer market |
|---|---|---|
| Order book | Single, centralized, publicly visible | No central book — bilateral quotes |
| Contract terms | Standardized | Customized between counterparties |
| Price formation | Price-time priority matching | Dealer quotes, negotiated |
| Counterparty | Clearing house (post-novation) | The dealer/broker itself, unless centrally cleared |
| Example | GC=F gold futures on COMEX | XAUUSD gold CFD via a retail broker |

This is the distinction that reframes everything else: a retail XAUUSD position isn't sitting in a public order book at all — it's a bilateral position against the broker, priced off the broker's own liquidity sourcing.

---

## How the Three Layers Interact

A concrete example ties the whole map together: a **hedge fund** (participant) might express a gold view either by buying a **gold future** (instrument) on **COMEX** (exchange-traded structure, clearing-house-guaranteed) — or by entering an OTC **gold forward** (instrument) directly with a **bank** (participant) acting as dealer, with no clearing house involved. Same underlying view, same asset class, entirely different risk, counterparty, and price-formation picture depending on which combination of layers is chosen. Every instrument you study going forward is worth placing on all three axes, not just understanding in isolation.

---


## Open Questions

- How does central clearing actually get implemented for OTC swaps post-2008 — is it universal now, or only for certain standardized swap types?
- For a retail XAUUSD CFD, is the broker acting purely as principal/dealer (B-book), or passing trades through to a liquidity provider (A-book) — and does this actually change anything for me as the end trader?