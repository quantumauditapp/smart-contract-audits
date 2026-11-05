---
token: Fluid
ticker: FLUID
network: arbitrum
risk_score: 43
status: medium
date: 2026-11-05
---

# Fluid (FLUID) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 43/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fluid-arb)

---

## Audit Summary

The protocol implements a standard Burn-and-Mint ERC-20 token with UUPS proxy upgradeability and pausable functionality. The architecture relies on OpenZeppelin's battle-tested libraries for access control and proxy management. No critical vulnerabilities were identified in the provided code map. The protocol is highly centralized, granting significant power to the DEFAULT_ADMIN_ROLE and MINTER_ROLE.

> **Final Recommendation:** The protocol is well-structured and follows secure coding standards. To further enhance security, consider implementing a multi-signature wallet or a DAO-based governance structure for the DEFAULT_ADMIN_ROLE to mitigate the risks associated with a single point of failure.

Regularly monitor the minting activity and administrative role changes to ensure transparency for token holders. Ensure that the private keys associated with the administrative roles are stored in secure, cold-storage environments.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract utilizes standard OpenZeppelin libraries for 7.1 Architecture and 7.2 Code Security. 7.3 Access Control is robust, utilizing role-based permissions for minting, pausing, and… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic risk is present due to the minting capability, which allows for significant supply dilution. 7.5 Governance is centralized under the DEFAULT_ADMIN_ROLE, which controls all administrative… |
| **Upgrades** | 1/10 | High | 7.7 Upgrades are managed via the UUPS pattern, which is the industry standard for gas-efficient proxy upgrades. The implementation includes 7.8 Operations safeguards such as the DEFAULT_ADMIN_ROLE… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 5 Informational_

### `QA-POWERS` — What the token's controller can do  *(Severity: High · Status: Acknowledged)*

The contract lets its controller — a ProxyAdmin contract — mint new supply; pause all transfers. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xe875…e34f — holds 99.9% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 86.8% of supply. Of that, 2.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 3.8% in wallets, 80.8% in other contracts. 2,845 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Fluid (FLUID), market cap $226M, rank #156. Traded on Coinbase. 2,845 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $69K (DexScreener, all pools). 24h trading volume $17.8M (CoinGecko, all markets, daily snapshot). 24h trading volume $93K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable, capped at 19669.4% of supply per year. Control: a ProxyAdmin contract. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $69K of DEX liquidity across 2 pools. Launch: 442 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x61e0...49cd`](https://arbiscan.io/address/0x61e030a56d33e8260fdd81f03b162a79fe3449cd) |
| **Network** | Arbitrum |
| **Price** | $2.5500 |
| **24h Volume** | $93.3K |
| **Liquidity** | $69.3K |
| **Volume / Liquidity** | 1.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 86.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 126 buys / 80 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/arbitrum/0x6ce19e5b05c0a0416feb963bcd754c8d99c02248)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fluid-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
