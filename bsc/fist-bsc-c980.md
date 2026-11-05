---
token: FIST
ticker: FIST
network: bsc
risk_score: 42
status: medium
date: 2026-11-05
---

# FIST (FIST) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 42/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fist-bsc-c980)

---

## Audit Summary

The FlapDirectTaxToken is an EIP-1167 minimal clone implementing a tax-on-transfer token with migration-based state transitions. While the core ERC-20 logic is standard, the contract contains centralized control mechanisms that allow the owner to modify tax and anti-sniper parameters. The contract is not upgradeable, but it suffers from trapped ETH and reliance on tx.origin for authorization logic.

> **Final Recommendation:** The owner should exercise extreme caution when calling finalizeMigration, as it permanently sets the anti-sniper window and tax expiration times. We recommend implementing a multi-signature wallet or a time-lock contract as the owner to mitigate the risks associated with centralized control.

Furthermore, the team should consider adding a rescue function to recover any ETH or ERC-20 tokens accidentally sent to the contract address. The reliance on tx.origin should be refactored to use msg.sender to align with best security practices and prevent potential cross-contract interaction issues.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes a minimal clone pattern, ensuring the implementation logic remains immutable post-deployment. Code security is generally robust, adhering to standard ERC-20 patterns for… |
| **Governance / Economics** | 7/10 | Low | The protocol relies on a single owner to trigger migration phases and finalize tax parameters. This centralization allows the owner to unilaterally change transfer fees and anti-sniper constraints… |
| **Upgrades** | 8/10 | Low | The contract is deployed as an EIP-1167 minimal clone, which is inherently immutable. There are no proxy upgrade mechanisms present, meaning the logic cannot be altered after deployment. This… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CD-01` — ETH trapped in contract  *(Severity: Medium · Status: Unresolved)*

The contract can receive ETH but lacks any function to withdraw or transfer it, resulting in any sent ETH being permanently locked.

**Recommendation:** Implement a withdrawal function restricted to the owner to allow for the recovery of accidentally sent funds.


### `CD-02` — Use of tx.origin for authorization  *(Severity: Medium · Status: Unresolved)*

The _getTaxWithPoolState function uses tx.origin to determine tax rules, which is vulnerable to phishing attacks where a user is tricked into interacting with a malicious contract.

**Recommendation:** Replace tx.origin with msg.sender to ensure that the authorization logic is tied to the immediate caller.


### `CP-07` — Owner can modify transfer fees  *(Severity: Medium · Status: Unresolved)*

The owner has the ability to change the tax fee structure through the finalizeMigration function, which directly impacts the amount of tokens deducted during transfers.

**Recommendation:** Document the fee structure clearly for users and consider implementing a timelock for any changes to tax parameters to provide transparency.


### `CP-08` — Owner can modify transfer and wallet limits  *(Severity: Low · Status: Unresolved)*

The finalizeMigration function allows the owner to set numeric limits that govern transaction sizes and wallet holdings, potentially restricting user activity.

**Recommendation:** Ensure these limits are set to reasonable defaults and communicate any changes to the community in advance.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 50.7% of supply. Of that, 27.1% burned, 12.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 8.3% in wallets, 3.1% in other contracts. 1,142 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,142 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $29K (DexScreener, all pools). 24h trading volume $285K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a role-controlled contract. Code: not upgradeable (no proxy). Fees: 3% on buy, 3% on sell. Market: $29K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xaa6c...7777`](https://bscscan.com/address/0xaa6c55ef9af28799d32108fdef84db01adfd7777) |
| **Network** | BNB Chain |
| **Price** | $0.1138 |
| **24h Volume** | $284.9K |
| **Liquidity** | $29.4K |
| **Volume / Liquidity** | 9.7× |
| **Token Age** | 9h |
| **Top-10 Holders** | 50.7% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 2779 buys / 2392 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xbf20ae4ca340ed8ad3ad01d162a0f7b420c13a65)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fist-bsc-c980)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
