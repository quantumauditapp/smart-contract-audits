---
token: Clankdexer
ticker: CLANKDEXER
network: base
risk_score: 61
status: medium
date: 2026-11-05
---

# Clankdexer (CLANKDEXER) — Smart Contract Security Analysis | Base

> **Risk Score: 61/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/clankdexer-base)

---

## Audit Summary

The ClankerToken is an ERC-20 compliant token designed for cross-chain interoperability via the Superchain Token Bridge. The architecture relies on standard OpenZeppelin libraries for voting and permit functionality. While the core token logic is robust, the protocol grants significant power to the bridge contract, which can mint or burn tokens at will. 7.1 Architecture: Standard ERC-20 with cross-chain extensions. 7.2 Code Security: High, utilizing battle-tested OpenZeppelin contracts. 7.3 Access Control: Restricted to bridge and admin. 7.4 Economic: High risk due to mint/burn capabilities. 7.5 Governance: Centralized admin control. 7.6 External: Dependency on Superchain Bridge. 7.7 Upgrades: N/A (immutable). 7.8 Operations: Standard.

> **Final Recommendation:** The protocol should implement a multi-signature wallet or a timelock for the admin address to mitigate risks associated with centralized control. Additionally, users should monitor the Superchain Token Bridge activity, as it holds the authority to alter token balances and total supply.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin standards for ERC-20, Votes, and Permit functionality. The code is clean and follows standard patterns for cross-chain token bridging. The… |
| **Governance / Economics** | 1/10 | High | The economic model is heavily dependent on the Superchain Token Bridge's integrity. The admin role has the authority to update metadata and images, which could be used for social engineering. Token… |
| **Upgrades** | 5/10 | Medium | The contract is not upgradeable and does not utilize proxy patterns. This ensures immutability of the core logic, which is a strength for security. No upgrade-related risks are present in the current… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 7 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xffa3…0762 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-01` — Privileged Minting Capability  *(Severity: Informational · Status: Unresolved)*

The crosschainMint function allows the Superchain Token Bridge to create new tokens at any time, which can dilute the value of existing holdings. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Ensure that the bridge contract is secured by a multi-signature or decentralized governance mechanism to prevent unauthorized minting.


### `CP-02` — Privileged Balance Manipulation  *(Severity: Informational · Status: Unresolved)*

The crosschainBurn function allows the Superchain Token Bridge to remove tokens from any user's balance, effectively acting as a force-transfer or burn mechanism. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Implement strict circuit breakers or monitoring on the bridge to detect and alert on anomalous burn transactions.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 56.0% of supply. What remains: 23.8% in wallets, 32.2% in other contracts. 195 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

195 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $20K (DexScreener, all pools). 24h trading volume $139K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $20K of DEX liquidity across 4 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x134b...0b07`](https://basescan.org/address/0x134ba967d5973baafcd5abbf459b91eff34e0b07) |
| **Network** | Base |
| **Price** | $0.0000004 |
| **24h Volume** | $138.7K |
| **Liquidity** | $20.4K |
| **Volume / Liquidity** | 6.8× |
| **Token Age** | 6h |
| **Top-10 Holders** | 56.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1043 buys / 2078 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x14d56b39e943bf3435896ea8ce2f54384a388cf8bbfdcddbc44b1e2b07bd3be9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/clankdexer-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
