---
token: ChatApex AI
ticker: CAAI
network: polygon
risk_score: 73
status: high
date: 2026-10-22
---

# ChatApex AI (CAAI) — Smart Contract Security Analysis | Polygon

> **Risk Score: 73/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/chatapex-ai-poly)

---

## Audit Summary

The ChatApexAI contract is a standard ERC-20 token with additional administrative controls for minting, tax management, and transaction limits. While ownership has been renounced, the contract maintains separate administrative roles for the treasury and tax management, which retain significant influence over the token's economic parameters. The architecture is straightforward, but the presence of centralized minting and parameter adjustment capabilities introduces inherent risks for token holders.

> **Final Recommendation:** Token holders should monitor the addresses assigned to the 'treasery' and 'admin' roles, as these entities possess the power to alter the token's economic landscape. Since the contract is immutable, no further security patches can be applied; users should exercise caution regarding the potential for supply inflation or sudden changes to transaction limits.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract implements standard ERC-20 functionality with secure arithmetic operations. 7.1 Architecture follows a centralized control pattern for administrative tasks. 7.2 Code Security is… |
| **Governance / Economics** | 6/10 | Medium | Economic parameters are highly centralized, allowing the treasury and admin roles to modify supply and transaction constraints. 7.4 Economic risks include potential dilution via the mint function and… |
| **Upgrades** | 6/10 | Medium | The contract is not upgradeable, which eliminates 7.7 Upgrades risks related to proxy patterns. 7.8 Operations are fixed by the immutable bytecode. No further changes to the contract logic are… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.9% (≈ permanent lock) |
| **LP Locked** | 99.9% — Null Address |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Capability  *(Severity: Medium · Status: Unresolved)*

The 'mint' function allows the address designated as the 'treasery' to create new tokens at any time, which can dilute the holdings of existing token holders.

**Recommendation:** Consider implementing a hard cap on the total supply or transitioning to a decentralized governance model for minting events.


### `CP-08` — Administrative Control Over Transaction Limits  *(Severity: Low · Status: Unresolved)*

The 'admin' role can modify the 'Min_Buy_Limit' via the 'setMinBuyLimit' function, allowing them to restrict or enable buying activity at their discretion.

**Recommendation:** Document the intended use of these limits and ensure the admin address is secured with multi-signature requirements.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 99.5% of supply. Of that, 7.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.2% in wallets, 92.0% in other contracts. 2,371 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,371 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.9% of the pool's LP is burned or time-locked. 99.9% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 0.1% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.1M (DexScreener, all pools). 24h trading volume $33K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.1M of DEX liquidity across 1 pools. Launch: 70 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xca51...d0a6`](https://polygonscan.com/address/0xca518ba0ef1fff5cfe8845e347afdfa3519dd0a6) |
| **Network** | Polygon |
| **Price** | $0.8886 |
| **24h Volume** | $32.8K |
| **Liquidity** | $1.05M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 99.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 85 buys / 244 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/polygon/0x31ec7b008fb6312c09762df775984135e41d0bac)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/chatapex-ai-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
