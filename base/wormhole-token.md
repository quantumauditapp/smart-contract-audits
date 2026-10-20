---
token: Wormhole Token
ticker: W
network: base
risk_score: 60
status: medium
date: 2026-10-08
---

# Wormhole Token (W) — Smart Contract Security Analysis | Base

> **Risk Score: 60/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wormhole-token-base)

---

## Audit Summary

The WToken contract implements an ERC-20 token with burnable, voting, and permit functionalities, utilizing OpenZeppelin's UUPS upgradeable and AccessControl standards. The audit found no critical or high-severity vulnerabilities. The contract's design incorporates robust access control for privileged functions such as minting, burning, and upgrades, which are managed by specific roles. While no direct vulnerabilities were identified, the centralized control inherent in these roles presents a governance and upgrade risk.

> **Final Recommendation:** Implement robust multi-signature wallet control for all administrative roles, especially the `DEFAULT_ADMIN_ROLE`, `MINTER_ROLE`, and `SET_DELEGATE_ROLE`, to prevent single points of failure. Establish clear, documented procedures for role management and contract upgrades, including time-locks for critical operations where feasible. Regularly review and audit the access control configurations and the upgrade process to ensure ongoing security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The WToken contract is a well-structured ERC-20 token, incorporating standard functionalities like burning, voting, and EIP-2612 permit. It inherits from OpenZeppelin's… |
| **Governance / Economics** | 1/10 | High | The contract employs AccessControl for managing administrative roles, including the `DEFAULT_ADMIN_ROLE` and specific roles like `MINTER_ROLE`, `BURNER_ROLE`, and `SET_DELEGATE_ROLE`. The… |
| **Upgrades** | 1/10 | High | The WToken contract utilizes the UUPS upgradeable proxy pattern, allowing its logic to be updated via the `upgradeToAndCall(address,bytes)` function. This function is restricted to a specific role… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 93.1% |
| **Top-3 Unlocked** | ⚠️ 98.3% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 5 address(es) other than the owner/deployer. One of them — a contract, 0x9c4d…264f — holds 93.1% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 50% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-POWERS` — What the token's controller can do  *(Severity: Medium · Status: Acknowledged)*

The contract lets its controller — a contract — mint new supply. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 37.5% of supply. What remains: 18.5% in wallets, 19.1% in other contracts. 231,652 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Wormhole (W), market cap $115M, rank #264. Traded on Binance. 231,652 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $127K (DexScreener, all pools). 24h trading volume $46.8M (CoinGecko, all markets, daily snapshot). 24h trading volume $122K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $1.66 on 2024-04-03; the price is now 98.9462% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Governance. Tokenomics — Supply: mintable with no on-chain cap found. Control: a contract. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $127K of DEX liquidity across 12 pools. Launch: 851 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb0ff...2b91`](https://basescan.org/address/0xb0ffa8000886e57f86dd5264b9582b2ad87b2b91) |
| **Network** | Base |
| **Price** | $0.01618 |
| **24h Volume** | $84.1K |
| **Liquidity** | $63.2K |
| **Volume / Liquidity** | 1.3× |
| **Token Age** | 2y |
| **Top-10 Holders** | 37.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1080 buys / 1046 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xf1eef36d55978edfd427e95c3d0c9b9359ef0aef)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wormhole-token-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-08*
