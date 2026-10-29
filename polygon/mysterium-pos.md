---
token: Mysterium (PoS)
ticker: MYST
network: polygon
risk_score: 60
status: medium
date: 2026-10-29
---

# Mysterium (PoS) (MYST) — Smart Contract Security Analysis | Polygon

> **Risk Score: 60/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mysterium-pos-poly)

---

## Audit Summary

The UChildERC20 contract serves as a bridge-compatible token on Polygon. It utilizes standard OpenZeppelin AccessControl for role management and supports meta-transactions. The architecture is robust for its intended purpose, though it contains centralized minting capabilities and minor asset handling inefficiencies.

> **Final Recommendation:** The protocol should ensure that the DEPOSITOR_ROLE is held by a multi-signature wallet or a time-locked contract to mitigate the risk of unauthorized minting. Additionally, implement a sweep function to recover any accidentally sent ETH to the contract address.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract implements standard ERC20 functionality with secure OpenZeppelin libraries. 7.1 Architecture follows a standard proxy pattern, while 7.2 Code Security is maintained through well-audited… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic risk is centered on the minting authority held by the bridge role. 7.5 Governance is centralized, allowing privileged roles to increase supply at will. This is a design requirement for… |
| **Upgrades** | 1/10 | High | 7.7 Upgrades are handled via a proxy pattern, allowing for logic updates. 7.8 Operations are stable, with no recent changes to the implementation contract. The upgradeability mechanism is standard… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · ⚪ 4 Informational_

### `CD-01` — Stuck ETH in Contract  *(Severity: Medium · Status: Unresolved)*

The contract can receive ETH via meta-transactions or direct transfers, but it lacks a function to withdraw or transfer these funds out of the contract.

**Recommendation:** Add an administrative function to withdraw any ETH accidentally sent to the contract address.


### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The deposit function allows an address with the DEPOSITOR_ROLE to mint new tokens at any time. This increases the total supply and dilutes the value of existing holdings.

**Recommendation:** Restrict the DEPOSITOR_ROLE to a multi-signature wallet or a secure bridge contract to prevent unauthorized supply inflation.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x3804…0bc6 — holds 99.9% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 34.0% of supply. Of that, 7.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 13.6% in wallets, 12.5% in other contracts. 538,091 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Mysterium (MYST), market cap $3M, rank #2230. 538,091 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $145K (DexScreener, all pools). 24h trading volume $13K (CoinGecko, all markets, daily snapshot). 24h trading volume $43K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $3.86 on 2018-01-08; the price is now 97.9903% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $145K of DEX liquidity across 10 pools. Launch: 2030 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1379...d9f3`](https://polygonscan.com/address/0x1379e8886a944d2d9d440b3d88df536aea08d9f3) |
| **Network** | Polygon |
| **Price** | $0.09345 |
| **24h Volume** | $42.5K |
| **Liquidity** | $139.2K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 5y |
| **Top-10 Holders** | 34.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 130 buys / 207 sells |

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

- [View on DexScreener](https://dexscreener.com/polygon/0x7e2eaa9514c7a56b4d556ff0d1009cb9c7f2b89d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mysterium-pos-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
