---
token: Aegis
ticker: ATH
network: polygon
risk_score: 75
status: high
date: 2026-10-30
---

# Aegis (ATH) — Smart Contract Security Analysis | Polygon

> **Risk Score: 75/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/aegis-poly)

---

## Audit Summary

The ATH token is a standard ERC-20 implementation utilizing OpenZeppelin's upgradeable library. The architecture relies on a Transparent Proxy pattern managed by a 3-of-3 multisig. While the code follows established standards, the centralization of minting and pausing capabilities introduces significant trust requirements for token holders.

> **Final Recommendation:** The protocol should consider implementing a timelock controller for all privileged functions, including minting and pausing, to provide transparency and a window for community response. Additionally, ensure that the keys for the multisig are stored in geographically distributed hardware security modules (HSMs).

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes robust, battle-tested OpenZeppelin libraries for all core functionality. 7.1 Architecture is sound, employing a standard proxy pattern. 7.2 Code Security is high due to the use… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance risks are centered on the minting authority. The ability to increase total supply allows for potential dilution of existing holders. 7.6 External dependencies are… |
| **Upgrades** | 1/10 | High | 7.7 Upgrades are managed via a Transparent Proxy pattern controlled by a multisig. 7.8 Operations are transparent, with the proxy admin being a multisig wallet. This structure provides a secure… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 2-of-3 |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · ⚪ 4 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The mint(address,uint256) function allows privileged addresses to create new tokens at will, which can dilute the value of existing holdings.

**Recommendation:** Implement a hard cap on the total supply or transition to a DAO-governed minting process with a timelock.


### `CP-04` — Centralized Pause Control  *(Severity: Medium · Status: Unresolved)*

The pause and unpause functions allow privileged addresses to halt all token transfers, effectively freezing user assets.

**Recommendation:** Restrict the pause functionality to emergency scenarios only and require a multi-signature approval process for activation.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x3322…6004 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 99.6% of supply. What remains: 0.4% in wallets, 99.2% in other contracts. 25,708 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

25,708 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $42.1M (GeckoTerminal, all pools). 24h trading volume $110K (GeckoTerminal, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $42.1M of DEX liquidity across 4 pools. Launch: 183 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6b99...0de8`](https://polygonscan.com/address/0x6b998441f7349a7bfdbb2a6d61a6d5f9acb90de8) |
| **Network** | Polygon |
| **Price** | $20.8869 |
| **24h Volume** | $109.9K |
| **Liquidity** | $42.08M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 6mo |
| **Top-10 Holders** | 99.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 580 buys / 559 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/polygon/0x6b998441f7349a7bfdbb2a6d61a6d5f9acb90de8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/aegis-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
