---
token: GOIF
ticker: GOIF
network: base
risk_score: 62
status: medium
date: 2026-10-21
---

# GOIF (GOIF) — Smart Contract Security Analysis | Base

> **Risk Score: 62/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/goif-base)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with additional governance, voting, and vesting capabilities. The protocol relies on a centralized owner to manage inflation, pool locking, and vesting releases. While the code follows standard OpenZeppelin patterns, the high degree of administrative control over token supply and transferability presents a significant centralization risk to token holders.

> **Final Recommendation:** To improve security and trust, consider transitioning the owner role to a multi-signature wallet or a decentralized DAO governance contract. This would mitigate the risk of a single compromised key performing unauthorized minting or locking of user funds.

Additionally, implementing a timelock for sensitive administrative functions like updateMintRate would provide transparency and allow the community to react to significant changes in tokenomics before they take effect.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for ERC-20, EIP-712, and governance features. 7.1 Architecture is modular, and 7.2 Code Security is high due to the use of standard… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized. The owner has the ability to mint tokens and halt transfers, which directly impacts the economic value and liquidity of the token.… |
| **Upgrades** | 3/10 | High | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are straightforward, relying on the owner to trigger vesting releases and manage pool states. The lack of upgradeability… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to increase the total supply of the token via the updateMintRate and release functions. This allows the owner to dilute the holdings of all existing token holders at their discretion.

**Recommendation:** Implement a multi-signature wallet for the owner address or transition to a decentralized governance model to require community consensus for minting events.


### `CP-05` — Centralized Control Over Token Transfers  *(Severity: Medium · Status: Unresolved)*

The owner can use the lockPool and unlockPool functions to toggle a switch that controls whether transfers are permitted. This gives the owner the power to effectively freeze user assets or halt trading at any time.

**Recommendation:** Remove the ability for the owner to arbitrarily lock transfers, or implement a timelock and public notification period before such drastic changes to token utility can be enacted.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.7% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 4,009 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

4,009 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $51K (DexScreener, all pools). 24h trading volume $136K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $51K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe172...b070`](https://basescan.org/address/0xe172e34970ccd956baccf57029f867a9fec7b070) |
| **Network** | Base |
| **Price** | $0.005107 |
| **24h Volume** | $136.2K |
| **Liquidity** | $51.2K |
| **Volume / Liquidity** | 2.7× |
| **Token Age** | 11h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1094 buys / 1086 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x60b7e591d66a1e85f12e6bbf0d6559c11cf9368168ba65ac3e093d477c068904)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/goif-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
