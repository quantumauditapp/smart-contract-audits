---
token: American Trust Fund System
ticker: ATFS
network: base
risk_score: 62
status: medium
date: 2026-10-21
---

# American Trust Fund System (ATFS) — Smart Contract Security Analysis | Base

> **Risk Score: 62/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/american-trust-fund-system-base-7bee)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with additional governance and vesting capabilities. The protocol relies on a centralized owner to manage token supply inflation and pool liquidity status. While the code follows standard OpenZeppelin patterns, the high degree of administrative control over token economics and transferability presents a significant centralization risk.

> **Final Recommendation:** It is recommended to transition ownership to a multi-signature wallet or a decentralized DAO to mitigate the risks associated with centralized control. Additionally, implementing a timelock on administrative functions like updateMintRate and lockPool would provide transparency and protection for token holders against sudden economic changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes robust OpenZeppelin standards (7.1 Architecture, 7.2 Code Security). The implementation of ERC-20, ERC-20Votes, and EIP-712 is standard and well-tested (7.3 Access Control).… |
| **Governance / Economics** | 2/10 | High | The economic model is controlled entirely by the owner, who can mint tokens up to a 2% annual cap (7.4 Economic). Governance is currently centralized, lacking a decentralized voting mechanism for… |
| **Upgrades** | 3/10 | High | The contract is not upgradeable (7.7 Upgrades). Logic is immutable, which provides security against malicious proxy updates. Future changes would require a migration to a new contract address. |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to mint new tokens via the updateMintRate and release functions. This allows the owner to increase the total supply, which directly dilutes the value of existing holdings.

**Recommendation:** Consider implementing a timelock for minting operations or moving control to a decentralized governance contract to ensure community oversight.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can toggle the isPoolUnlocked switch using the lockPool and unlockPool functions. This allows the owner to unilaterally halt or enable token transfers, effectively freezing user assets or liquidity.

**Recommendation:** Restrict the ability to lock/unlock pools to a decentralized governance process or remove the functionality entirely to ensure the token remains censorship-resistant.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.7% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.3% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 2,016 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,016 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $52K (DexScreener, all pools). 24h trading volume $145K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $52K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3287...3a37`](https://basescan.org/address/0x32872755e7d3b63ef2e695d33d301946ba823a37) |
| **Network** | Base |
| **Price** | $0.005192 |
| **24h Volume** | $144.6K |
| **Liquidity** | $51.5K |
| **Volume / Liquidity** | 2.8× |
| **Token Age** | 11h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1101 buys / 1092 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x2fda82afa5c4cf0e589f991d6b2eca06591ead9e582c29390d05a14dee7f17ec)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/american-trust-fund-system-base-7bee)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
