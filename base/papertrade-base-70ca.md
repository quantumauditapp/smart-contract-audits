---
token: Papertrade
ticker: PAPER
network: base
risk_score: 62
status: medium
date: 2026-10-25
---

# Papertrade (PAPER) — Smart Contract Security Analysis | Base

> **Risk Score: 62/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/papertrade-base-70ca)

---

## Audit Summary

The ClankerToken is an ERC-20 compliant token with cross-chain capabilities integrated via the Superchain Token Bridge. The architecture relies on standard OpenZeppelin libraries for voting and permit functionality. While the core token logic is robust, the protocol grants significant power to the bridge contract to mint and burn tokens, which introduces centralized risks regarding supply control and user balance integrity.

> **Final Recommendation:** The protocol should implement a multi-signature wallet or a timelock controller for the admin address to mitigate risks associated with centralized metadata and role management. Additionally, users should be aware that the Superchain Token Bridge holds the authority to burn and mint tokens, which is a necessary design choice for cross-chain functionality but represents a significant trust assumption.

Regular monitoring of the bridge contract's activity is recommended to ensure that mint/burn events align with expected cross-chain traffic. No further code changes are required for the current functionality, but future iterations should consider decentralizing the admin role to improve trust transparency.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin standards for ERC-20, Votes, and Permit functionality, ensuring high interoperability. 7.1 Architecture is modular, separating administrative metadata… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic risk is present due to the minting capabilities, which can lead to supply inflation if the bridge is compromised. 7.5 Governance is centralized under an admin address that can update… |
| **Upgrades** | 2/10 | High | 7.7 Upgrades are not implemented via proxy patterns in this contract, meaning the logic is immutable. 7.8 Operations are straightforward, with administrative functions limited to metadata and role… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 4 Informational_

### `CP-02` — Privileged Balance Modification  *(Severity: High · Status: Unresolved)*

The crosschainBurn function allows the bridge contract to directly remove tokens from any user's balance. This grants the bridge the power to effectively seize or destroy user assets.

**Recommendation:** Restrict the burn functionality to only allow users to burn their own tokens, or implement a multi-step verification process for cross-chain burns to prevent unauthorized asset removal.


### `CP-01` — Privileged Minting Capability  *(Severity: Medium · Status: Unresolved)*

The crosschainMint function allows the bridge contract to increase the total token supply at any time. This can lead to the dilution of existing token holders' value if the bridge is compromised or misused.

**Recommendation:** Ensure the bridge contract is secured with robust access controls and consider implementing a supply cap if the tokenomics require protection against excessive inflation.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xffa3…0762 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10.2M (DexScreener, all pools). 24h trading volume $33.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner key. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10.2M of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb056...6b07`](https://basescan.org/address/0xb05696b8cd42671809b62ffc0843a7eda4e56b07) |
| **Network** | Base |
| **Price** | $0.000101 |
| **24h Volume** | $33.13M |
| **Liquidity** | $10.21M |
| **Volume / Liquidity** | 3.2× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1066 buys / 887 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xda242d618299a99d1369f8eb8ae0d34689532e51)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/papertrade-base-70ca)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
