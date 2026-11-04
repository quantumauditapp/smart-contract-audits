---
token: WSOS
ticker: WSOS
network: base
risk_score: 67
status: high
date: 2026-11-04
---

# WSOS (WSOS) — Smart Contract Security Analysis | Base

> **Risk Score: 67/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wsos-base)

---

## Audit Summary

ClankerToken is an ERC-20 compliant token designed for cross-chain interoperability on the Base network. The contract utilizes standard OpenZeppelin libraries for governance and permit functionality. While the core token logic is robust, the protocol relies on a privileged bridge contract for cross-chain operations, which introduces centralized control over token supply and individual user balances.

> **Final Recommendation:** The protocol should implement a multi-signature wallet or a decentralized governance contract to manage the administrative functions, reducing the risk of a single point of failure. Additionally, ensure that the SuperchainTokenBridge address is monitored for any anomalous activity that could impact token supply or user balances.

Users should be aware that the cross-chain bridge holds significant authority over the token's state. Regular audits of the bridge contract are recommended to ensure the integrity of the cross-chain minting and burning processes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows standard ERC-20 and ERC-7802 patterns, ensuring compatibility with cross-chain bridges. 7.1 Architecture: Modular design using standard libraries. 7.2 Code Security… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic: The token supply is elastic due to cross-chain minting/burning capabilities. 7.5 Governance: Administrative functions allow for metadata updates by a single admin. 7.8 Operations: The… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades: The contract is not currently implemented as a proxy, meaning logic is immutable. No upgrade mechanisms are present in the source code. Future changes would require a full contract… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 6 Informational_

### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 97.9% of supply. What remains: 28.8% in wallets, 69.1% in other contracts. The deployer/owner wallet itself holds 21.8%. A holder that also controls the contract can sell into its own liquidity. 1,024 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xffa3…0762 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-01` — Centralized Minting Authority  *(Severity: Informational · Status: Unresolved)*

The crosschainMint function allows the designated bridge contract to increase the total supply of tokens at any time. This can lead to the dilution of existing token holders' value if the bridge is compromised or misconfigured. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Implement a hard cap on the total supply or introduce a governance-based delay for large minting operations to mitigate the risk of sudden inflation.


### `CP-02` — Bridge-Controlled Balance Manipulation  *(Severity: Informational · Status: Unresolved)*

The crosschainBurn function grants the bridge contract the ability to burn tokens directly from any user's address. If the bridge contract is compromised, an attacker could drain funds from any user holding the token. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Restrict the burn functionality to only allow users to burn their own tokens, or implement a multi-step approval process for cross-chain transfers that requires user authorization.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,024 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $282K (DexScreener, all pools). 24h trading volume $49K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $282K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x09b5...ea9e`](https://basescan.org/address/0x09b5cb12fadc6dfa39cc2aa569b05dd3c9b6ea9e) |
| **Network** | Base |
| **Price** | $0.00000338 |
| **24h Volume** | $49.3K |
| **Liquidity** | $281.7K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 4h |
| **Top-10 Holders** | 97.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2391 buys / 513 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xbc21587aa28a32b36385595eedf2b13e2c3fc801cf3934d90c6b4b1edea21f8a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wsos-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
