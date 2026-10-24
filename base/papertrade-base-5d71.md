---
token: Papertrade
ticker: PAPER
network: base
risk_score: 60
status: medium
date: 2026-10-24
---

# Papertrade (PAPER) — Smart Contract Security Analysis | Base

> **Risk Score: 60/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/papertrade-base-5d71)

---

## Audit Summary

ClankerToken is an ERC-20 compliant token on the Base network designed for cross-chain interoperability via the Superchain Token Bridge. The contract implements standard OpenZeppelin libraries for voting and burning. The primary risks involve centralized control over token supply and the ability of the bridge contract to modify user balances.

> **Final Recommendation:** Token holders should be aware that the Superchain Token Bridge holds the authority to mint and burn tokens as part of its cross-chain functionality. This is a standard requirement for bridge-enabled assets but represents a centralized point of failure.

Ensure that the admin address is managed via a multi-signature wallet or a decentralized governance contract to mitigate the risk of unauthorized metadata or admin changes. No further code changes are required as the current implementation correctly follows the intended cross-chain bridge architecture.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows standard ERC-20 and ERC-7802 patterns, ensuring compatibility with cross-chain infrastructure. 7.1 Architecture is robust, utilizing well-audited OpenZeppelin components for… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance risks are centered on the centralized authority granted to the bridge and the admin role. While the bridge is a system-level component, its ability to burn tokens from… |
| **Upgrades** | 5/10 | Medium | The contract does not utilize a proxy pattern, meaning 7.7 Upgrades are not applicable in the traditional sense. The logic is immutable, providing transparency to token holders. Future changes would… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 6 Informational_

### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 1.0% in wallets, 99.0% in other contracts. The deployer/owner wallet itself holds 100.0%. A holder that also controls the contract can sell into its own liquidity. 3,254 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xffa3…0762 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-01` — Centralized Minting Authority  *(Severity: Informational · Status: Unresolved)*

The crosschainMint function allows the bridge contract to increase the total supply of the token at any time. This can lead to the dilution of existing token holders' value if the bridge is compromised or misconfigured. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Monitor the bridge contract's activity and ensure that the bridge governance is sufficiently decentralized or secured by a multi-signature mechanism.


### `CP-02` — Bridge-Controlled Balance Manipulation  *(Severity: Informational · Status: Unresolved)*

The crosschainBurn function grants the bridge contract the authority to remove tokens from any user's balance. While intended for cross-chain transfers, this function provides the bridge with the capability to unilaterally reduce any holder's balance. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Verify that the bridge contract's logic is audited and that access to the bridge's administrative functions is strictly controlled to prevent unauthorized burning of user assets.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

3,254 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10.3M (DexScreener, all pools). 24h trading volume $53.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10.3M of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xbec0...3b07`](https://basescan.org/address/0xbec0c62384de58cd1336897236cf71bfd6883b07) |
| **Network** | Base |
| **Price** | $0.000102 |
| **24h Volume** | $53.38M |
| **Liquidity** | $10.31M |
| **Volume / Liquidity** | 5.2× |
| **Token Age** | 1h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1182 buys / 960 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xad195e49efe118d79b68d653037dd8f6f047dcdd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/papertrade-base-5d71)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
