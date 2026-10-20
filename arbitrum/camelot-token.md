---
token: Camelot token
ticker: GRAIL
network: arbitrum
risk_score: 44
status: medium
date: 2026-09-29
---

# Camelot token (GRAIL) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 44/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/camelot-token-arb)

---

## Audit Summary

The GrailTokenV2 contract is an ERC-20 token with owner-controlled administrative functions. It includes mechanisms for token emission and allocation updates. A key finding is the ability of privileged addresses to mint new tokens, which could lead to token dilution for existing holders.

> **Final Recommendation:** It is recommended to implement robust multi-signature controls for the owner address to mitigate the risk of a single point of compromise, especially given the owner's ability to control token supply parameters and trigger minting. Consider implementing time-locks or community governance mechanisms for critical functions that affect token supply or economic parameters to introduce a delay and allow for community oversight. Additionally, ensure clear documentation and transparency regarding the emission schedule and allocation logic to inform token holders about potential supply changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The GrailTokenV2 contract implements the ERC-20 standard, providing standard token functionalities like `transfer`, `balanceOf`, and `approve`. The contract uses `Ownable` for access control… |
| **Governance / Economics** | 5/10 | Medium | The contract's economic model allows for configurable emission rates and allocation percentages, providing flexibility for protocol management (7.4 Economic). The owner can update critical parameters… |
| **Upgrades** | 4/10 | Medium | The GrailTokenV2 contract is not implemented as an upgradeable proxy, meaning its logic cannot be changed after deployment (7.7 Upgrades). This provides immutability and reduces upgrade-related… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · ⚪ 3 Informational_

### `CP-01` — A privileged address can mint new tokens  *(Severity: Medium · Status: Unresolved)*

A privileged function increases the total supply, diluting every holder. Functions: claimMasterRewards(uint256), updateAllocations(uint256,uint256), updateEmissionRate(uint256). Restricted to: master, masteraddress, owner.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x64c6…9ab7 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 12% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $1.3M (DexScreener, all pools). 24h trading volume $69K (CoinGecko, all markets, daily snapshot). 24h trading volume $63K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $4,643.22 on 2023-03-19; the price is now 99.354% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 77.3% of supply. Of that, 8.7% burned — not holders that can sell, so excluded from the concentration score. What remains: 0.0% in wallets, 68.5% in other contracts. The deployer/owner wallet itself holds 6.9%. 46,940 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Camelot Token (GRAIL), rank #3184. 46,940 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 3-of-6 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.3M of DEX liquidity across 28 pools. Launch: 1409 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3d99...82d8`](https://arbiscan.io/address/0x3d9907f9a368ad0a51be60f7da3b97cf940982d8) |
| **Network** | Arbitrum |
| **Price** | $31.7900 |
| **24h Volume** | $37.7K |
| **Liquidity** | $155.5K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 3y |
| **Top-10 Holders** | 77.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 105 buys / 203 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0x8cc8093218bcac8b1896a1eed4d925f6f6ab289f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/camelot-token-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-29*
