---
token: SPDR S&P 500 ETF (Ondo Tokenized)
ticker: SPYON
network: ethereum
risk_score: 9
status: low
date: 2026-10-10
---

# SPDR S&P 500 ETF (Ondo Tokenized) (SPYON) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/spdr-sp-500-etf-ondo-tokenized-eth)

---

## Audit Summary

The GMToken contract is an upgradeable ERC-20 token utilizing a Beacon proxy pattern. It incorporates AccessControl for managing privileged roles, allowing for features like pausing transfers, setting compliance rules, and minting new tokens. Key findings highlight the ability for a privileged role to mint new tokens, potentially diluting existing holders, and the critical ability for a privileged role to replace external contracts that dictate transfer logic, posing a significant centralization risk.

> **Final Recommendation:** It is critical to implement robust security measures for all privileged roles, especially those with the ability to mint tokens or modify core contract dependencies. This includes multi-signature wallets for sensitive operations, strict key management, and regular audits of role assignments. Establish clear governance procedures for any changes to critical external contracts or token logic. Implement comprehensive monitoring for all privileged function calls to detect unauthorized or suspicious activity promptly.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The GMToken contract is built upon OpenZeppelin's upgradeable ERC-20 and AccessControl standards, ensuring a robust and well-tested foundation (7.1 Architecture, 7.2 Code Security). Access control is… |
| **Governance / Economics** | 9/10 | Low | The economic stability of the GMToken is highly dependent on the integrity of its privileged roles (7.4 Economic). A role can `mint` new tokens, directly increasing total supply and diluting existing… |
| **Upgrades** | 5/10 | Medium | The GMToken contract is deployed using a Beacon proxy pattern, making it upgradeable (7.7 Upgrades). This allows for future enhancements or bug fixes to the token's logic. The… |

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

_⚪ 6 Informational_

### `CP-01` — Centralized Minting Capability  *(Severity: Informational · Status: Unresolved)*

The `mint(address to, uint256 amount)` function allows an address holding the `MINTER_ROLE` to create new tokens and assign them to any address. This increases the total supply of GMToken, which can dilute the value of tokens held by existing token holders without their consent.

**Recommendation:** Token holders should be aware that the supply of GMToken is not fixed and can be increased by the project's administrators. It is recommended that the project clearly communicates its minting policy and any planned minting events to the community. Consider implementing a time-lock or multi-signature requirement for minting operations to add an extra layer of security and transparency.


### `CP-03` — Critical External Dependency Manipulation  *(Severity: Informational · Status: Unresolved)*

The `setCompliance(address _compliance)` and `setTokenPauseManager(address _tokenPauseManager)` functions allow an address holding the `CONFIGURER_ROLE` to change the addresses of external contracts that directly influence how token transfers behave. The `compliance` and `tokenPauseManager` contracts can dictate rules, fees, or even pause transfers. This means that whoever controls the `CONFIGURER_ROLE` can effectively control or disrupt all token transfers by pointing to a malicious or arbitrary contract.

**Recommendation:** Token holders should understand that the project administrators have significant control over the token's transfer mechanics. It is crucial for the project to secure the `CONFIGURER_ROLE` with the highest level of security, such as a multi-signature wallet with a high threshold. Any changes to these critical dependency addresses should be communicated transparently and ideally be subject to a time-lock to allow for community review.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 71.8% of supply. What remains: 32.6% in wallets, 39.2% in other contracts. 2,151 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as SPDR S&P 500 ETF (Ondo Tokenized ETF) (SPYON), market cap $47M, rank #475. Its admin (0x3715…34f1) controls 441 issuer-backed coins CoinGecko lists on ethereum, $1.0B together, among them Circle Internet Group (Ondo Tokenized Stock), Ondo U.S. Dollar Token, iShares Core S&P 500 ETF (Ondo Tokenized ETF): one issuer's programme, read on-chain. 2,151 holders. Verified by: issuer programme.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $185K (DexScreener, all pools). 24h trading volume $2.4M (CoinGecko, all markets, daily snapshot). 24h trading volume $867K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Tokenized Exchange-Traded Funds (ETFs). Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $185K of DEX liquidity across 17 pools. Launch: 399 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

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
