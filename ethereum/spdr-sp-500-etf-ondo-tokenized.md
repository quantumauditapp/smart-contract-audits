---
token: SPDR S&P 500 ETF (Ondo Tokenized)
ticker: SPYON
network: ethereum
risk_score: 73
status: high
date: 2026-10-10
---

# SPDR S&P 500 ETF (Ondo Tokenized) (SPYON) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 73/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/spdr-sp-500-etf-ondo-tokenized-eth)

---

## Audit Summary

The GMToken contract is an upgradeable ERC-20 token utilizing a Beacon proxy pattern. It incorporates AccessControl for managing privileged roles, allowing for features like pausing transfers, setting compliance rules, and minting new tokens. Key findings highlight the ability for a privileged role to mint new tokens, potentially diluting existing holders, and the critical ability for a privileged role to replace external contracts that dictate transfer logic, posing a significant centralization risk.

> **Final Recommendation:** It is critical to implement robust security measures for all privileged roles, especially those with the ability to mint tokens or modify core contract dependencies. This includes multi-signature wallets for sensitive operations, strict key management, and regular audits of role assignments. Establish clear governance procedures for any changes to critical external contracts or token logic. Implement comprehensive monitoring for all privileged function calls to detect unauthorized or suspicious activity promptly.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The GMToken contract is built upon OpenZeppelin's upgradeable ERC-20 and AccessControl standards, ensuring a robust and well-tested foundation (7.1 Architecture, 7.2 Code Security). Access control is… |
| **Governance / Economics** | 2/10 | High | The economic stability of the GMToken is highly dependent on the integrity of its privileged roles (7.4 Economic). A role can `mint` new tokens, directly increasing total supply and diluting existing… |
| **Upgrades** | 1/10 | High | The GMToken contract is deployed using a Beacon proxy pattern, making it upgradeable (7.7 Upgrades). This allows for future enhancements or bug fixes to the token's logic. The… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 22.5% |
| **Top-3 Unlocked** | 57.3% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 4 Informational_

### `CP-03` — Critical External Dependency Manipulation  *(Severity: High · Status: Unresolved)*

The `setCompliance(address _compliance)` and `setTokenPauseManager(address _tokenPauseManager)` functions allow an address holding the `CONFIGURER_ROLE` to change the addresses of external contracts that directly influence how token transfers behave. The `compliance` and `tokenPauseManager` contracts can dictate rules, fees, or even pause transfers. This means that whoever controls the `CONFIGURER_ROLE` can effectively control or disrupt all token transfers by pointing to a malicious or arbitrary contract.

**Recommendation:** Token holders should understand that the project administrators have significant control over the token's transfer mechanics. It is crucial for the project to secure the `CONFIGURER_ROLE` with the highest level of security, such as a multi-signature wallet with a high threshold. Any changes to these critical dependency addresses should be communicated transparently and ideally be subject to a time-lock to allow for community review.


### `CP-01` — Centralized Minting Capability  *(Severity: Medium · Status: Unresolved)*

The `mint(address to, uint256 amount)` function allows an address holding the `MINTER_ROLE` to create new tokens and assign them to any address. This increases the total supply of GMToken, which can dilute the value of tokens held by existing token holders without their consent.

**Recommendation:** Token holders should be aware that the supply of GMToken is not fixed and can be increased by the project's administrators. It is recommended that the project clearly communicates its minting policy and any planned minting events to the community. Consider implementing a time-lock or multi-signature requirement for minting operations to add an extra layer of security and transparency.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 94.0% is held, unlocked, by 10 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 59% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 71.8% of supply. What remains: 32.6% in wallets, 39.2% in other contracts. 2,151 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as SPDR S&P 500 ETF (Ondo Tokenized ETF) (SPYON), market cap $47M, rank #507. 2,151 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $185K (DexScreener, all pools). 24h trading volume $2.4M (CoinGecko, all markets, daily snapshot). 24h trading volume $867K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $185K of DEX liquidity across 17 pools. Launch: 399 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfedc...2c08`](https://etherscan.io/address/0xfedc5f4a6c38211c1338aa411018dfaf26612c08) |
| **Network** | Ethereum |
| **Price** | $787.8600 |
| **24h Volume** | $496.8K |
| **Liquidity** | $109.8K |
| **Volume / Liquidity** | 4.5× |
| **Token Age** | 1y |
| **Top-10 Holders** | 71.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 787 buys / 670 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x5638bbde046ec2efc7c8f3fd8dc5a9a1016f7eeb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/spdr-sp-500-etf-ondo-tokenized-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-10*
