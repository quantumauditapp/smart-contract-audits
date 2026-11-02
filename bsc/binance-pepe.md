---
token: Binance Pepe
ticker: BEPE
network: bsc
risk_score: 51
status: medium
date: 2026-11-02
---

# Binance Pepe (BEPE) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 51/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/binance-pepe-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is an EIP-1167 minimal clone token contract. The ownership of the contract has been renounced, effectively locking the administrative functions. The architecture is immutable, and the token follows standard ERC-20 patterns with additional tax and migration logic. No vulnerabilities were identified in the provided code map.

> **Final Recommendation:** As the contract ownership is renounced and the architecture is immutable, no further action is required for the current deployment. Users should verify the contract address against official documentation to ensure they are interacting with the intended clone instance.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes a standard EIP-1167 minimal clone pattern, ensuring consistent logic deployment. Code security is robust, adhering to OpenZeppelin standards for ERC-20 and permit functionality.… |
| **Governance / Economics** | 1/10 | High | Governance is effectively decentralized through the renunciation of ownership. 7.4 Economic: The migration and tax logic are now immutable. 7.5 Governance: No active administrative control exists.… |
| **Upgrades** | 8/10 | Low | The contract is deployed as an EIP-1167 minimal clone, which is inherently immutable. 7.7 Upgrades: No upgrade path exists for the logic or state. The contract is permanently locked in its current… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x5722…6512 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $404K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 64.5% of supply. What remains: 10.7% in wallets, 53.8% in other contracts. 283 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

283 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (pepe). Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 0% on buy, 0.99% on sell. Market: $9K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8cb6...7777`](https://bscscan.com/address/0x8cb6be67aaab6cdd9116fbd02f370cf494ca7777) |
| **Network** | BNB Chain |
| **Price** | $0.00000844 |
| **24h Volume** | $376.6K |
| **Liquidity** | $8.6K |
| **Volume / Liquidity** | 43.7× |
| **Token Age** | 10h |
| **Top-10 Holders** | 64.5% of supply |
| **Buy / Sell Tax** | 0.0% / 1.0% |
| **24h Transactions** | 3841 buys / 3651 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xaacac80ac5ed082cef2ba9ff765217514de9a740)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/binance-pepe-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
