---
token: Papertrade
ticker: PAPER
network: base
risk_score: 54
status: medium
date: 2026-11-03
---

# Papertrade (PAPER) — Smart Contract Security Analysis | Base

> **Risk Score: 54/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/papertrade-base-fed7)

---

## Audit Summary

ClankerToken is an ERC-20 compliant token designed for cross-chain interoperability on the Base network. The architecture relies on the SuperchainTokenBridge for cross-chain minting and burning operations. While the implementation follows standard OpenZeppelin patterns for voting and permit functionality, the centralization of mint/burn authority poses significant risks to token holders.

> **Final Recommendation:** The protocol should implement a multi-signature wallet or a timelock for any administrative functions that modify metadata or admin roles to mitigate centralization risks. Additionally, users should be aware that the cross-chain bridge holds the technical capability to burn tokens from any address, which is a standard requirement for cross-chain bridges but represents a trust assumption.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin libraries for ERC-20, Votes, and Permit functionality, ensuring 7.1 Architecture and 7.2 Code Security compliance. 7.3 Access Control is implemented via a… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance risks are centered on the bridge's authority to modify supply. While necessary for cross-chain functionality, the ability to burn tokens from any address creates a… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades are not currently implemented as the contract is not a proxy. 7.8 Operations are handled via the immutable bridge address. No upgrade paths exist for the token logic itself. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xffa3…0762 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-01` — Privileged Minting Capability  *(Severity: Informational · Status: Unresolved)*

The crosschainMint function allows the designated bridge address to create new tokens at will, which can dilute the value of existing holdings. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Ensure the bridge contract is secured by a multi-signature wallet and monitor minting events for anomalous activity.


### `CP-02` — Privileged Balance Manipulation  *(Severity: Informational · Status: Unresolved)*

The crosschainBurn function allows the bridge address to remove tokens from any user's balance, effectively granting it the power to seize assets. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Restrict the burn functionality to only allow users to burn their own tokens, or implement a transparent, audited process for any bridge-initiated burns.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 1.0% in wallets, 99.0% in other contracts. 5,629 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

5,629 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10.3M (DexScreener, all pools). 24h trading volume $53.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10.3M of DEX liquidity across 1 pools. Launch: 365 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2fd3...4276`](https://basescan.org/address/0x2fd3f789fe25984295c8fa032be2485c5c7e4276) |
| **Network** | Base |
| **Price** | $0.000102 |
| **24h Volume** | $53.51M |
| **Liquidity** | $10.32M |
| **Volume / Liquidity** | 5.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1732 buys / 1657 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x0143fc5189a7022aa0c4157677fe3fcdc0861885)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/papertrade-base-fed7)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
