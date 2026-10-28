---
token: Ixs Token
ticker: IXS
network: base
risk_score: 45
status: medium
date: 2026-10-28
---

# Ixs Token (IXS) — Smart Contract Security Analysis | Base

> **Risk Score: 45/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ixs-token-base)

---

## Audit Summary

The IxsToken is a standard ERC-20 implementation utilizing OpenZeppelin's upgradeable libraries. The contract features minting, pausing, and role-based access control managed via a multisig wallet. No critical vulnerabilities were identified in the provided code map.

> **Final Recommendation:** Maintain the current multisig security posture for all administrative roles. Ensure that the private keys for the multisig signers are stored in cold storage or hardware security modules to prevent unauthorized access to the minting and pausing functions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The architecture follows standard OpenZeppelin patterns for upgradeable tokens (7.1 Architecture). Code security is robust, utilizing battle-tested libraries for ERC-20, Permit, and Burnable… |
| **Governance / Economics** | 3/10 | High | Economic parameters are controlled by a multisig wallet, ensuring no single point of failure for minting or pausing (7.4 Economic). Governance operations are transparently managed through role… |
| **Upgrades** | 1/10 | High | The contract utilizes the Transparent Proxy pattern, which is the industry standard for upgradeable contracts (7.7 Upgrades). Operations are managed by a dedicated ProxyAdmin multisig, providing a… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 3-of-5 |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 97.2% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 5 Informational_

### `QA-POWERS` — What the token's controller can do  *(Severity: High · Status: Acknowledged)*

The contract lets its controller — a 2-of-3 multisig — mint new supply; pause all transfers. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0x917c…2216 — holds 97.1% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 61% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 43.2% of supply. Of that, 7.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 19.5% in wallets, 15.8% in other contracts. 2,040 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as IXS (IXS), market cap $7M, rank #1432. 2,040 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $86K (DexScreener, all pools). 24h trading volume $821K (CoinGecko, all markets, daily snapshot). 24h trading volume $59K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.831 on 2024-03-31; the price is now 95.3221% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 2-of-3 multisig. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $86K of DEX liquidity across 2 pools. Launch: 768 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfe55...92c5`](https://basescan.org/address/0xfe550bffb51eb645ea3b324d772a19ac449e92c5) |
| **Network** | Base |
| **Price** | $0.04694 |
| **24h Volume** | $34.7K |
| **Liquidity** | $52.6K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 2y |
| **Top-10 Holders** | 43.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 206 buys / 201 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x0bcaebeeee604443feb6d5314a726626a858ebd3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ixs-token-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
