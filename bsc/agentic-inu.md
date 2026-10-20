---
token: Agentic Inu
ticker: .AI
network: bsc
risk_score: 81
status: high
date: 2026-10-20
---

# Agentic Inu (.AI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 81/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/agentic-inu-bsc)

---

## Audit Summary

The NftGatedBondingCurve contract implements a bonding curve mechanism restricted to specific NFT holders. The architecture relies on a mathematical curve to determine token pricing and supply. While the core logic is protected against reentrancy, the protocol grants significant power to NFT holders to mint and burn tokens, which introduces economic dilution risks.

> **Final Recommendation:** The protocol should implement a hard cap on the total supply to prevent excessive dilution by privileged NFT holders. Additionally, consider introducing a time-lock or multi-signature requirement for any future changes to the bonding curve parameters to increase transparency and trust.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract utilizes OpenZeppelin's ReentrancyGuard to prevent common reentrancy attacks during buy/sell operations. 7.1 Architecture follows a standard bonding curve model, while 7.2 Code Security… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance aspects are tightly coupled to NFT ownership. The ability for privileged users to mint tokens via buy/sell functions creates a risk of supply inflation. This design… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. The logic is immutable, which provides security against malicious logic updates but prevents patching if vulnerabilities are discovered.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `CP-01` — Privileged Minting and Dilution Risk  *(Severity: Medium · Status: Unresolved)*

The functions buy(uint256), buyWithBNB(), and sell(uint256) allow specific NFT holders to mint or burn tokens, directly impacting the circulating supply. Because these functions are restricted to a specific group, they can effectively dilute the holdings of other participants by increasing the total supply at will.

**Recommendation:** Implement a global supply cap that cannot be exceeded by these functions. Consider adding a governance mechanism or a community-voting process to adjust supply-related parameters rather than allowing individual NFT holders to trigger minting events.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 21.3% of supply. Of that, 5.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 9.1% in wallets, 6.7% in other contracts. 1,204 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,204 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $95K (DexScreener, all pools). 24h trading volume $1.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (inu). Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $95K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7ffc...15dc`](https://bscscan.com/address/0x7ffcf7b3b52adcc00c76f50ce2e37bf3c7e215dc) |
| **Network** | BNB Chain |
| **Price** | $0.0008409 |
| **24h Volume** | $1.42M |
| **Liquidity** | $94.6K |
| **Volume / Liquidity** | 15.0× |
| **Token Age** | 2h |
| **Top-10 Holders** | 21.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6072 buys / 4627 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xcbc77d857d11d9a8407b6e580010540d885b0b40)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/agentic-inu-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
