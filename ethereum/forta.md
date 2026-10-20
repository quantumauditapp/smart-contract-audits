---
token: Forta
ticker: FORT
network: ethereum
risk_score: 49
status: medium
date: 2026-10-07
---

# Forta (FORT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 49/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/forta-eth)

---

## Audit Summary

The Forta contract is an upgradeable ERC-20 token utilizing the UUPS proxy pattern and OpenZeppelin's AccessControl. The audit, based on the provided code map and key function sources, found no critical or high-severity vulnerabilities. The contract implements standard token functionalities and robust access control for administrative actions.

> **Final Recommendation:** Ensure that the `ADMIN_ROLE` is assigned to a secure, multi-signature wallet or a robust governance mechanism to prevent single points of failure and unauthorized administrative actions. Regularly review and test any proposed upgrades in a staging environment before deploying to production to mitigate risks associated with new logic. Maintain vigilance over external dependencies and ensure proper operational security practices for all privileged accounts.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract is an ERC-20 token (7.1 Architecture) with standard functionalities like `transfer`, `approve`, and `balanceOf`. It inherits from `AccessControlUpgradeable`, providing robust role-based… |
| **Governance / Economics** | 1/10 | High | The contract employs OpenZeppelin's `AccessControlUpgradeable` for managing privileged operations (7.5 Governance). The `ADMIN_ROLE` is used to restrict functions like `setName`, `grantRole`… |
| **Upgrades** | 1/10 | High | The contract utilizes the UUPS (Universal Upgradeable Proxy Standard) pattern (7.7 Upgrades), allowing for future upgrades of its logic contract. Functions like `upgradeTo` and `upgradeToAndCall` are… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.3% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a contract, 0x37b7…1482 — holds 99.3% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 72% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 35.7% of supply. What remains: 24.1% in wallets, 11.6% in other contracts. 5,477 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Forta (FORT), market cap $15M, rank #1054. Traded on Coinbase. 5,477 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $250K (DexScreener, all pools). 24h trading volume $8.9M (CoinGecko, all markets, daily snapshot). 24h trading volume $540K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.965 on 2022-06-15; the price is now 97.6195% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: vote delegation in its code. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $250K of DEX liquidity across 3 pools. Launch: 910 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4154...ec29`](https://etherscan.io/address/0x41545f8b9472d758bb669ed8eaeeecd7a9c4ec29) |
| **Network** | Ethereum |
| **Price** | $0.02146 |
| **24h Volume** | $428.9K |
| **Liquidity** | $179.6K |
| **Volume / Liquidity** | 2.4× |
| **Token Age** | 2y |
| **Top-10 Holders** | 35.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 568 buys / 627 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x1a3fb049c2d88a16b927be6a4cae48ca38d93d4c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/forta-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-07*
