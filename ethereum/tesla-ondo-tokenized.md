---
token: Tesla (Ondo Tokenized)
ticker: TSLAON
network: ethereum
risk_score: 11
status: low
date: 2026-10-16
---

# Tesla (Ondo Tokenized) (TSLAON) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 11/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tesla-ondo-tokenized-eth)

---

## Audit Summary

The GMToken contract is an upgradeable ERC-20 token utilizing a Beacon proxy pattern. It incorporates access control for critical functions such as minting and setting external compliance and pause managers. The audit identified high and medium severity issues related to centralized control over token supply and critical external dependencies, which could significantly impact token holders if misused.

> **Final Recommendation:** It is crucial to implement stringent operational security measures for all privileged roles, especially those with the ability to mint tokens, change critical external dependencies, or initiate contract upgrades. Consider implementing multi-signature wallets for these roles to prevent single points of failure. Additionally, establish clear governance procedures for any changes to critical parameters or contract logic, ensuring transparency and community oversight where appropriate to mitigate the risks associated with centralized control.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The GMToken contract is built upon OpenZeppelin's upgradeable ERC-20 and AccessControl standards, providing a solid foundation for token functionality and role-based permissions (7.1 Architecture).… |
| **Governance / Economics** | 9/10 | Low | The economic model of GMToken is subject to centralized control, as a privileged role can `mint` new tokens at will, directly impacting the total supply and potentially diluting existing token… |
| **Upgrades** | 5/10 | Medium | The GMToken contract is deployed as a Beacon proxy, allowing its implementation logic to be upgraded. This upgradeability provides flexibility for future enhancements or bug fixes (7.7 Upgrades).… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 64.6% |
| **Top-3 Unlocked** | ⚠️ 98.2% |

## Security Findings

_⚪ 6 Informational_

### `CP-01` — A privileged address can mint new tokens  *(Severity: Informational · Status: Unresolved)*

A privileged function increases the total supply, diluting every holder. Functions: mint(address,uint256). Restricted to: role.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `CP-03` — A privileged address can replace a contract every transfer depends on  *(Severity: Informational · Status: Unresolved)*

Transfers call an external contract whose address a privileged function can change. Whoever controls that setting controls what a transfer does. Functions: setCompliance, setTokenPauseManager. Restricted to: role.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 70.6% of supply. What remains: 53.5% in wallets, 17.1% in other contracts. 3,540 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Tesla (Ondo Tokenized Stock) (TSLAON), market cap $20M, rank #819. Its admin (0x3715…34f1) controls 441 issuer-backed coins CoinGecko lists on ethereum, $1.0B together, among them Circle Internet Group (Ondo Tokenized Stock), Ondo U.S. Dollar Token, iShares Core S&P 500 ETF (Ondo Tokenized ETF): one issuer's programme, read on-chain. 3,540 holders. Verified by: issuer programme.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $646K (DexScreener, all pools). 24h trading volume $2.3M (CoinGecko, all markets, daily snapshot). 24h trading volume $1.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Tokenized Stocks. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $646K of DEX liquidity across 29 pools. Launch: 394 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf6b1...103f`](https://etherscan.io/address/0xf6b1117ec07684d3958cad8beb1b302bfd21103f) |
| **Network** | Ethereum |
| **Price** | $375.9500 |
| **24h Volume** | $529.0K |
| **Liquidity** | $145.7K |
| **Volume / Liquidity** | 3.6× |
| **Token Age** | 1y |
| **Top-10 Holders** | 70.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1299 buys / 1135 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x31227b50eccdc9c589826aa2d9e7c5619b1895da)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tesla-ondo-tokenized-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-16*
