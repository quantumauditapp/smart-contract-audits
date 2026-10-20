---
token: XRAY
ticker: XRAY
network: ethereum
risk_score: 72
status: high
date: 2026-10-17
---

# XRAY (XRAY) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 72/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xray-eth)

---

## Audit Summary

The XRay token contract is a standard ERC-20 implementation. A key security feature is that the contract's ownership has been renounced, rendering all owner-privileged functions dormant. This significantly reduces potential centralized control risks, as no single entity can modify transfer rules or reassign ownership.

> **Final Recommendation:** Users should be aware that the XRay token contract is immutable due to renounced ownership, meaning its core functionalities and any initial restrictions are permanently set. While this enhances security by preventing malicious changes, it also means no future modifications or bug fixes can be implemented. Token holders should verify the contract's current state and understand that no administrative actions can alter its behavior.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The XRay contract implements the ERC-20 standard, providing essential token functionalities like `transfer`, `balanceOf`, and `approve`. The contract includes mechanisms to control token transfers… |
| **Governance / Economics** | 1/10 | High | The economic model is based on a standard ERC-20 token. The most significant governance aspect is the renounced ownership, which means no single entity can unilaterally change critical contract… |
| **Upgrades** | 6/10 | Medium | The XRay contract is not designed as an upgradeable proxy contract (7.7 Upgrades). This means its logic is immutable once deployed, providing certainty regarding its long-term behavior but also… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by the token's owner/deployer (0xf75d…0152) — they can pull that liquidity at any moment. This is the rug-pull path. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-05` — A privileged address controls a switch that decides whether transfers go through  *(Severity: Informational · Status: Unresolved)*

An on/off setting checked in the transfer path can be changed by a privileged function; depending on its value, transfers or sales are allowed or refused. Ownership is renounced, so no one can call these functions now. Functions: openTrading. Restricted to: owner.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 52.6% of supply. What remains: 24.8% in wallets, 27.8% in other contracts. The deployer/owner wallet itself holds 4.0%. 96 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

96 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $24K (DexScreener, all pools). 24h trading volume $43K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $24K of DEX liquidity across 6 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa06d...9f00`](https://etherscan.io/address/0xa06dcccf665f887790e3d99b7ee26cb34bde9f00) |
| **Network** | Ethereum |
| **Price** | $0.06172 |
| **24h Volume** | $42.6K |
| **Liquidity** | $24.0K |
| **Volume / Liquidity** | 1.8× |
| **Token Age** | 22h |
| **Top-10 Holders** | 52.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 319 buys / 97 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x5eae1e6c5bed22609186796fe791dc89497226506bf9ea88b370ab2070435e9a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xray-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-17*
