---
token: SpaceX (Ondo Tokenized)
ticker: SPCXON
network: ethereum
risk_score: 12
status: low
date: 2026-10-05
---

# SpaceX (Ondo Tokenized) (SPCXON) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 12/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/spacex-ondo-tokenized-eth)

---

## Audit Summary

The GMToken contract is an upgradeable ERC-20 token utilizing a Beacon Proxy pattern. It incorporates compliance and pause management features, with administrative roles controlling key functionalities. The audit identified that privileged roles can mint new tokens, potentially diluting existing holders, and critically, can replace external contracts that dictate transfer rules, posing a significant risk to token operations and security.

> **Final Recommendation:** To mitigate the identified risks, it is paramount to implement robust governance procedures around the privileged roles. Specifically, the roles capable of minting tokens and changing critical external contract addresses (`compliance`, `tokenPauseManager`) should be secured with multi-signature wallets or time-locks.

Additionally, thorough due diligence must be performed on any external contract addresses set for `compliance` and `tokenPauseManager` to ensure they are secure and operate as expected, as these contracts directly control token transfer logic. Consider implementing a timelock for changes to these critical addresses to allow for community review and reaction time.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The GMToken contract implements the ERC-20 standard with additional features for compliance and pausing transfers, inheriting from `ERC20Upgradeable` and `AccessControlUpgradeable`. The architecture… |
| **Governance / Economics** | 9/10 | Low | The economic model of the GMToken is subject to significant control by privileged roles. The ability for a designated role to `mint` new tokens at will (CP-01) introduces inflationary risk and can… |
| **Upgrades** | 5/10 | Medium | The GMToken is deployed as a Beacon Proxy, enabling future upgrades to its logic contract. This upgradeability is managed through `AccessControlUpgradeable` roles, meaning that only authorized… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 29.5% |
| **Top-3 Unlocked** | 48.9% |

## Security Findings

_⚪ 6 Informational_

### `CP-01` — Privileged Address Can Mint New Tokens  *(Severity: Informational · Status: Unresolved)*

A designated role has the ability to call the `mint(address,uint256)` function, which increases the total supply of GMToken. This means that whoever controls this role can create new tokens at any time, potentially diluting the value of tokens held by other users.

**Recommendation:** The role with minting capabilities should be controlled by a robust governance mechanism, such as a multi-signature wallet, to prevent unilateral and unauthorized token creation. Consider if minting is truly necessary post-deployment or if a fixed supply is preferable.


### `CP-03` — Privileged Address Can Replace Critical External Contracts  *(Severity: Informational · Status: Unresolved)*

A designated role can call `setCompliance(address)` and `setTokenPauseManager(address)` to change the addresses of external contracts that dictate how GMToken transfers behave. These external contracts can impose rules, fees, or even halt transfers. Whoever controls this role can effectively redirect or alter the core logic of all token transfers by pointing to a malicious or compromised contract.

**Recommendation:** The role capable of changing these critical external contract addresses should be secured with the highest level of governance, such as a multi-signature wallet with a significant number of signers and a timelock. Any new compliance or token pause manager contract should undergo rigorous security audits and community review before being set.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 85.4% of supply. Of that, 1.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 77.5% in wallets, 6.4% in other contracts. 2,587 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as SpaceX (Ondo Tokenized Stock) (SPCXON), market cap $12M, rank #1081. Its admin (0x3715…34f1) controls 441 issuer-backed coins CoinGecko lists on ethereum, $1.0B together, among them Circle Internet Group (Ondo Tokenized Stock), Ondo U.S. Dollar Token, iShares Core S&P 500 ETF (Ondo Tokenized ETF): one issuer's programme, read on-chain. 2,587 holders. Verified by: issuer programme.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $694K (DexScreener, all pools). 24h trading volume $4.4M (CoinGecko, all markets, daily snapshot). 24h trading volume $4.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Tokenized Stocks. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $694K of DEX liquidity across 30 pools. Launch: 114 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc9ee...5581`](https://etherscan.io/address/0xc9eef266834730340a55b6cc24621b31baf55581) |
| **Network** | Ethereum |
| **Price** | $160.4400 |
| **24h Volume** | $2.17M |
| **Liquidity** | $307.1K |
| **Volume / Liquidity** | 7.1× |
| **Token Age** | 3mo |
| **Top-10 Holders** | 85.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5084 buys / 4656 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x0461c60ad5fc24cb1fc075b7f202095819de6944)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/spacex-ondo-tokenized-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-05*
