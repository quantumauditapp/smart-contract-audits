---
token: DIME
ticker: DIME
network: ethereum
risk_score: 62
status: medium
date: 2026-10-11
---

# DIME (DIME) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 62/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dime-eth)

---

## Audit Summary

The DIME contract is an upgradeable ERC-20 token utilizing the UUPS proxy pattern and OpenZeppelin's standard libraries for features like minting, burning, pausing, and access control. The analysis did not identify any specific technical vulnerabilities in the provided code. However, the contract design centralizes significant control in specific roles, such as the ability to mint new tokens, pause transfers, and upgrade the contract logic.

> **Final Recommendation:** To mitigate the risks associated with centralized control, consider implementing a multi-signature wallet or a decentralized autonomous organization (DAO) for managing critical roles such as `MINTER_ROLE`, `PAUSER_ROLE`, and the `DEFAULT_ADMIN_ROLE`. Introduce timelocks for sensitive operations, especially for upgrades and changes to role assignments, to provide users with a window to react to impending changes. Ensure a transparent and well-defined governance process for all administrative actions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The DIME contract leverages robust and widely audited OpenZeppelin libraries for its core ERC-20 functionality, pausing mechanism, and access control (7.1 Architecture). Functions like `transfer`… |
| **Governance / Economics** | 1/10 | High | The contract's economic and governance model is highly centralized, relying on `AccessControlUpgradeable` to manage critical functions (7.3 Access Control, 7.4 Economic, 7.5 Governance). The… |
| **Upgrades** | 1/10 | High | DIME is implemented as an upgradeable UUPS proxy, allowing the contract's logic to be modified in the future (7.7 Upgrades). The `upgradeToAndCall(address,bytes)` function, which facilitates… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `QA-POWERS` — What the token's controller can do  *(Severity: High · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply; pause all transfers. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 97.7% of supply. What remains: 0.0% in wallets, 97.7% in other contracts. 40 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Paradex (DIME), market cap $45M, rank #521. 40 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $186K (DexScreener, all pools). 24h trading volume $282K (CoinGecko, all markets, daily snapshot). 24h trading volume $255K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $186K of DEX liquidity across 4 pools. Launch: 208 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb32e...0fa7`](https://etherscan.io/address/0xb32e10022ffbedfe10bc818a1c7e67d9d87e0fa7) |
| **Network** | Ethereum |
| **Price** | $0.08329 |
| **24h Volume** | $238.9K |
| **Liquidity** | $166.6K |
| **Volume / Liquidity** | 1.4× |
| **Token Age** | 6mo |
| **Top-10 Holders** | 97.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 106 buys / 101 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x2c84182ba1002fb2e4276967c9918d8709431f95a8c287da9a554a503775fa25)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dime-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-11*
