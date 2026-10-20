---
token: ZEUS
ticker: ZEUS
network: bsc
risk_score: 63
status: medium
date: 2026-10-08
---

# ZEUS (ZEUS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 63/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/zeus-bsc)

---

## Audit Summary

The BurnMintERC20 contract is an ERC-20 token with standard functionalities and additional minting and burning capabilities. It utilizes OpenZeppelin's AccessControl for managing privileged roles. A key finding identifies that a privileged role can mint new tokens, which could dilute existing token holders.

> **Final Recommendation:** It is crucial to establish and maintain stringent access control policies for the roles capable of minting tokens. The address holding the `minter` role should be a highly secure multi-signature wallet or a robust governance mechanism to prevent unauthorized supply inflation. Regular audits of the role assignments and operational procedures are recommended to ensure the integrity of the token supply.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements the ERC-20 standard, providing essential token functionalities like transfers and approvals. It leverages OpenZeppelin's AccessControl for robust role-based permissions… |
| **Governance / Economics** | 1/10 | High | The economic model of the token is primarily influenced by the minting capability. While the `AccessControl` mechanism provides a framework for governance over these roles, the existence of a role… |
| **Upgrades** | 2/10 | High | The BurnMintERC20 contract is not designed as an upgradeable proxy, meaning its logic cannot be changed after deployment (7.7 Upgrades). This eliminates risks associated with upgradeability patterns… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 4 Informational_

### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by the token's owner/deployer (0x4846…8178) — they can pull that liquidity at any moment. This is the rug-pull path. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-01` — A special controller can create new tokens  *(Severity: Medium · Status: Unresolved)*

The `mint(address,uint256)` function allows a specific controller, identified by a special role, to create new tokens out of thin air. This action increases the total number of tokens in circulation, which can reduce the value of tokens held by existing holders.

**Recommendation:** Token holders should be aware that the controller with the minting role has the power to increase the token supply. It is recommended that this role be assigned to a highly secure entity, such as a multi-signature wallet, and that the community understands the policies governing its use.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 91.1% of supply. Of that, 38.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 7.8% in wallets, 44.8% in other contracts. 3,643 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Zeus Network (ZEUS), market cap $13M, rank #1096. 3,643 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $211K (DexScreener, all pools). 24h trading volume $63.0M (CoinGecko, all markets, daily snapshot). 24h trading volume $2.2M (DexScreener, all pools). CoinGecko's record for this coin: all-time high $1.11 on 2024-04-08; the price is now 98.7356% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner key. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $211K of DEX liquidity across 3 pools. Launch: 390 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa2be...beee`](https://bscscan.com/address/0xa2be3e48170a60119b5f0400c65f65f3158fbeee) |
| **Network** | BNB Chain |
| **Price** | $0.01441 |
| **24h Volume** | $2.04M |
| **Liquidity** | $206.9K |
| **Volume / Liquidity** | 9.9× |
| **Token Age** | 1y |
| **Top-10 Holders** | 91.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 9557 buys / 9547 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x5db04ea767d9fa92b9c06d7752226be7bc2e546f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/zeus-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-08*
