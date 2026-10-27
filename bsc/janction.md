---
token: JANCTION
ticker: JCT
network: bsc
risk_score: 67
status: high
date: 2026-10-27
---

# JANCTION (JCT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 67/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/janction-bsc)

---

## Audit Summary

The protocol implements an upgradeable ERC-20 token with minting and burning capabilities managed by a multisig owner. The architecture follows standard UUPS proxy patterns and utilizes OpenZeppelin's Ownable2Step for secure ownership transfers. While the code is well-structured, the centralization of minting authority poses a significant economic risk to token holders.

> **Final Recommendation:** The protocol should implement a timelock controller for all privileged functions, including minting and contract upgrades, to provide transparency and a window for community response. Additionally, consider setting a hard cap on the total supply if not already enforced to mitigate the risk of excessive dilution.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The implementation utilizes robust, battle-tested libraries for proxy management and token standards (7.1 Architecture, 7.2 Code Security). Access control is strictly enforced via modifiers like… |
| **Governance / Economics** | 1/10 | High | The economic model relies on centralized minting authority, which allows for potential supply inflation (7.4 Economic). Governance is managed via a 5-of-7 multisig, providing a reasonable balance… |
| **Upgrades** | 1/10 | High | The contract employs the UUPS proxy pattern, which is the industry standard for upgradeable contracts (7.7 Upgrades). The implementation includes necessary safety checks to prevent bricking the proxy… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 4 Informational_

### `CD-01` — State Variable Shadowing  *(Severity: High · Status: Unresolved)*

The contract contains instances where local variables or inherited state variables shadow existing state, which can lead to unintended logic execution or incorrect state updates during contract interactions.

**Recommendation:** Rename shadowed variables to ensure clarity and prevent accidental overwriting of critical state data.


### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The mint(address,uint256) function allows addresses with the 'minter' role to create new tokens at will. This centralizes control over the total supply and allows for the dilution of existing token holders.

**Recommendation:** Restrict the minting role to a timelocked multisig or a decentralized governance contract to ensure transparency and prevent unilateral supply changes.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x13f6…5e12 — holds 99.9% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 78.2% of supply. What remains: 19.7% in wallets, 58.5% in other contracts. 15,865 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Janction (JCT), market cap $88M, rank #297. 15,865 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $41K (DexScreener, all pools). 24h trading volume $49.6M (CoinGecko, all markets, daily snapshot). 24h trading volume $301K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable, capped at 384.6% of supply per year. Control: a 5-of-7 multisig. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $41K of DEX liquidity across 2 pools. Launch: 351 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xea37...7707`](https://bscscan.com/address/0xea37a8de1de2d9d10772eeb569e28bfa5cb17707) |
| **Network** | BNB Chain |
| **Price** | $0.007405 |
| **24h Volume** | $299.7K |
| **Liquidity** | $40.0K |
| **Volume / Liquidity** | 7.5× |
| **Token Age** | 11mo |
| **Top-10 Holders** | 78.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3524 buys / 3478 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xcec354f641fb46b977c3a1f18b5caf3e2ede4c2c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/janction-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
