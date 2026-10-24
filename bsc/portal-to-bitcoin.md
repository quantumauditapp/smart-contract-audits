---
token: Portal To Bitcoin
ticker: PTB
network: bsc
risk_score: 67
status: high
date: 2026-10-24
---

# Portal To Bitcoin (PTB) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 67/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/portal-to-bitcoin-bsc)

---

## Audit Summary

PortalToken is a standard ERC-20 token implementation with bridge-based minting capabilities. The contract utilizes OpenZeppelin's Ownable and ERC20 standards, ensuring robust base functionality. The primary security consideration is the centralized control over token supply via the bridge address.

> **Final Recommendation:** The protocol should ensure that the bridge address is secured by a multi-signature wallet or a time-locked contract to prevent single-point-of-failure risks. Regular monitoring of the bridge address activity is recommended to detect any anomalous minting events.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows standard ERC-20 patterns with 7.1 Architecture and 7.2 Code Security adhering to industry best practices. 7.3 Access Control is implemented via Ownable, restricting… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic risks are centered on the minting authority held by the bridge. 7.5 Governance is currently centralized under a multisig wallet, providing a balance between security and operational… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are straightforward, with the owner having the ability to rotate the bridge address if necessary. No complex upgrade… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 85.4% |
| **Top-3 Unlocked** | ⚠️ 96.4% |

## Security Findings

_🟡 3 Medium · ⚪ 3 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The mint(address,uint256) function allows a privileged bridge address to create new tokens at will. This capability can lead to the dilution of existing token holder value if the bridge address is compromised or acts maliciously.

**Recommendation:** Implement a multi-signature requirement or a time-lock mechanism for the bridge address to restrict the ability to mint tokens. Additionally, consider setting a hard cap on the total supply to limit potential inflationary impact.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 99.1% is held, unlocked, by 10 address(es) other than the owner/deployer. One of them — a wallet, 0xf949…0298 — holds 85.4% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 62% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $37K (DexScreener, all pools). 24h trading volume $8.7M (CoinGecko, all markets, daily snapshot). 24h trading volume $156K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.0816 on 2025-09-08; the price is now 99.6552% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 73.8% of supply. Of that, 4.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 39.1% in wallets, 30.0% in other contracts. 35,046 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Portal to Bitcoin (PTB), rank #3468. 35,046 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 2-of-3 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $37K of DEX liquidity across 5 pools. Launch: 417 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x95c9...9201`](https://bscscan.com/address/0x95c9b514566fbd224dc2037f5914eb8ab91c9201) |
| **Network** | BNB Chain |
| **Price** | $0.0001505 |
| **24h Volume** | $119.9K |
| **Liquidity** | $22.6K |
| **Volume / Liquidity** | 5.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 73.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1520 buys / 1513 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x28b7c347a58c9c30b21e51e732ee9723d910f605)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/portal-to-bitcoin-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
