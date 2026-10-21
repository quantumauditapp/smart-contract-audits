---
token: test
ticker: TEST
network: ethereum
risk_score: 58
status: medium
date: 2026-10-21
---

# test (TEST) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 58/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/test-eth)

---

## Audit Summary

The WrappedTest contract functions as a wrapper for a native asset. The architecture is straightforward, utilizing standard ERC-20 transfer patterns. However, the contract lacks essential standard functions like totalSupply() and balanceOf(), which limits interoperability with standard DeFi interfaces. The primary risk involves the centralized control over token minting and supply management.

> **Final Recommendation:** Implement the missing standard ERC-20 functions (totalSupply, balanceOf) to ensure compatibility with wallets and decentralized exchanges. Consider adding a timelock or multi-signature requirement for the native contract controller to mitigate the risk of unauthorized minting.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements standard transfer and transferFrom logic with proper allowance checks. 7.1 Architecture is simple but lacks standard ERC-20 view functions. 7.2 Code Security is generally… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance risks are concentrated in the native contract controller. The ability to mint tokens via receiveApproval and wrap functions allows for potential supply inflation.… |
| **Upgrades** | 2/10 | High | 7.7 Upgrades are not supported as the contract is not a proxy. This ensures the logic remains immutable post-deployment. 7.8 Operations are limited to the defined wrap/unwrap flow. |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The functions receiveApproval, wrap, and unwrap allow the native contract controller to mint new tokens. This grants the controller the ability to increase the total supply at will, which could lead to the dilution of existing token holders' value.

**Recommendation:** Restrict minting capabilities to a decentralized governance contract or implement a hard cap on the total supply to prevent arbitrary inflation.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 48.0% of supply. What remains: 19.2% in wallets, 28.8% in other contracts. 240 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

240 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $19K (DexScreener, all pools). 24h trading volume $105K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $19K of DEX liquidity across 3 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8675...9eae`](https://etherscan.io/address/0x867585caf0a877db3f88a2303120f8de77629eae) |
| **Network** | Ethereum |
| **Price** | $0.00001113 |
| **24h Volume** | $72.7K |
| **Liquidity** | $11.6K |
| **Volume / Liquidity** | 6.3× |
| **Token Age** | 11h |
| **Top-10 Holders** | 48.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 275 buys / 237 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x6ffee8245e97fe742b8facb6f74b502692274a7b3ca77fa4ac85e5b7920a5f47)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/test-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
