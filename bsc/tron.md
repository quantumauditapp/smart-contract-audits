---
token: TRON
ticker: TRX
network: bsc
risk_score: 32
status: low
date: 2026-10-30
---

# TRON (TRX) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 32/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tron-bsc)

---

## Audit Summary

The TRX contract is a standard ERC-20 implementation with meta-transaction support and role-based access control. The architecture is robust for standard token operations, but the presence of an unrestricted minting capability and trapped ETH in the meta-transaction handler presents moderate risks to token holders.

> **Final Recommendation:** Implement a withdrawal function restricted to the owner to recover any ETH accidentally sent to the contract. Additionally, consider implementing a timelock or a multi-signature wallet for the PREDICATE_ROLE to mitigate the risk of unauthorized or excessive token minting.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin libraries for ERC-20 and AccessControl, ensuring 7.1 Architecture and 7.2 Code Security standards are met. 7.3 Access Control is correctly implemented via… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic risks are present due to the minting function, which allows for supply inflation. 7.5 Governance is centralized under the PREDICATE_ROLE, which can unilaterally alter the token supply.… |
| **Upgrades** | 2/10 | High | 7.7 Upgrades are not applicable as the contract is not a proxy. The logic is immutable, providing certainty to users regarding the token's behavior. No upgrade path exists, which eliminates risks… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 68.0% |
| **Top-3 Unlocked** | ⚠️ 83.7% |

## Security Findings

_🟡 3 Medium · ⚪ 4 Informational_

### `CD-01` — Trapped ETH in Contract  *(Severity: Medium · Status: Unresolved)*

The contract includes meta-transaction functionality which may lead users to send ETH to the contract address. There is no mechanism to withdraw these funds, resulting in permanent loss of any ETH sent to the contract.

**Recommendation:** Add a function to allow the contract owner to withdraw any accidentally sent ETH or native tokens from the contract balance.


### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The mint(address,uint256) function allows any address with the PREDICATE_ROLE to create new tokens at will. This can lead to significant supply inflation and dilution of existing token holder value if the role is compromised or misused.

**Recommendation:** Restrict the minting capability to a multi-signature wallet or a governance contract with a timelock to ensure transparency and prevent unilateral supply changes.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 98.5% is held, unlocked, by 10 address(es) other than the owner/deployer. One of them — a contract, 0xb81d…185c — holds 68.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 7% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 90.8% of supply. Of that, 85.1% burned, 0.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 2.9% in wallets, 2.7% in other contracts. 109,329 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as TRON (BSC) (TRX). Traded on Binance. 109,329 holders. Verified by: exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $4.6M (DexScreener, all pools). 24h trading volume $189K (CoinGecko, all markets, daily snapshot). 24h trading volume $1.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $4.6M of DEX liquidity across 30 pools. Launch: 1655 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xce7d...12e3`](https://bscscan.com/address/0xce7de646e7208a4ef112cb6ed5038fa6cc6b12e3) |
| **Network** | BNB Chain |
| **Price** | $0.3659 |
| **24h Volume** | $158.6K |
| **Liquidity** | $304.0K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 4y |
| **Top-10 Holders** | 90.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 997 buys / 1303 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x1f7df58c60a56bc8322d3e42d7d37a0383d42746)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tron-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
