---
token: 共建
ticker: 共建
network: bsc
risk_score: 44
status: medium
date: 2026-11-03
---

# 共建 (共建) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 44/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-c96fcc-bsc)

---

## Audit Summary

The BuildNBuildToken is a standard ERC-20 implementation with additional minting capabilities. While ownership has been renounced, the contract retains a 'minter' role that allows for supply expansion. The architecture is standard, though the centralization of minting power remains a notable economic consideration for token holders.

> **Final Recommendation:** The protocol should ensure that the address assigned to the 'minter' role is secured via a multi-signature wallet or a time-locked contract to prevent unauthorized supply expansion. Holders should monitor the minter address for any unexpected activity.

Since ownership is renounced, no further administrative changes can be made to the contract's core logic. Users should verify the current minter address on-chain to understand the potential for future supply increases.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin-like patterns for ERC-20 functionality. 7.1 Architecture is clean and follows established standards, while 7.2 Code Security is robust due to the use of… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic risk is centered on the minting function, which allows for supply inflation. 7.5 Governance is currently limited as ownership is renounced, meaning the minter role cannot be changed by… |
| **Upgrades** | 7/10 | Low | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are stable and fixed. The contract logic is immutable, providing certainty to users regarding the code's behavior. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The 'mint' function allows a designated minter address to create new tokens, which increases the total supply and dilutes the value of existing holdings. This function is restricted to the address stored in the 'minter' variable.

**Recommendation:** Ensure the minter role is held by a secure, multi-signature wallet. If minting is no longer required, consider renouncing the minter role or setting it to the zero address to permanently cap the supply.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 92.9% of supply. Of that, 87.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 5.0% in wallets, 0.8% in other contracts. 341 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

341 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $35K (DexScreener, all pools). 24h trading volume $337K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 2% on buy, 2% on sell. Market: $35K of DEX liquidity across 1 pools. Launch: 2 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4606...d8dd`](https://bscscan.com/address/0x460610467e2ef0ea96642ae379764d268081d8dd) |
| **Network** | BNB Chain |
| **Price** | $0.00000001 |
| **24h Volume** | $336.8K |
| **Liquidity** | $34.9K |
| **Volume / Liquidity** | 9.6× |
| **Token Age** | 2d |
| **Top-10 Holders** | 92.9% of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 4035 buys / 6321 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xecf8f1d98f9aa2e3d069a960e11aded56130aa95)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-c96fcc-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
