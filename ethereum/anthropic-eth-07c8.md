---
token: Anthropic
ticker: ANT
network: ethereum
risk_score: 32
status: low
date: 2026-11-05
---

# Anthropic (ANT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 32/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/anthropic-eth-07c8)

---

## Audit Summary

The ANT token is a standard ERC-20 implementation. The audit identified a critical logic flaw regarding transfer validation and return values that deviates from the ERC-20 standard, potentially causing integration issues with decentralized exchanges and automated vaults.

> **Final Recommendation:** The development team should immediately address the return value discrepancy in the transfer functions to ensure full compliance with the ERC-20 standard. Failure to do so will result in failed transactions when interacting with standard DeFi protocols that expect a boolean return value.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract utilizes a standard OpenZeppelin-like ERC-20 structure, ensuring basic compatibility for transfers and approvals. 7.1 Architecture is clean and modular, adhering to established patterns.… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic and 7.5 Governance risks are minimal as the contract is a simple token without staking, minting, or burning capabilities. The token supply is fixed, and there are no centralized… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the contract is not a proxy and lacks upgradeability patterns. The code is immutable, ensuring that the logic cannot be altered post-deployment. This provides high… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Dead Address |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `CD-01` — Non-Compliant ERC-20 Return Values  *(Severity: High · Status: Unresolved)*

The transfer and transferFrom functions contain logic inconsistencies where the internal _transfer execution does not properly validate against the maxWalletLimits, potentially leading to silent failures or incorrect boolean returns that violate the ERC-20 standard.

**Recommendation:** Refactor the _transfer function to ensure that all limit checks are performed before state changes and that the functions explicitly return the correct boolean status as required by the ERC-20 specification.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 21.4% of supply. Of that, 4.9% burned — not holders that can sell, so excluded from the concentration score. What remains: 7.1% in wallets, 9.4% in other contracts. 205 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

205 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $115K (DexScreener, all pools). 24h trading volume $1.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $115K of DEX liquidity across 1 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x60d1...3f71`](https://etherscan.io/address/0x60d1f3ea966a358cff9af0e3caef883634c43f71) |
| **Network** | Ethereum |
| **Price** | $0.001417 |
| **24h Volume** | $1.09M |
| **Liquidity** | $115.0K |
| **Volume / Liquidity** | 9.5× |
| **Token Age** | 1d |
| **Top-10 Holders** | 21.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1001 buys / 833 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x97a0584ba25813f12fec4b359f1a0046d719bc5c4b8babf9263310639b151ccf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/anthropic-eth-07c8)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
