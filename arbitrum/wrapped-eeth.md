---
token: Wrapped eETH
ticker: WEETH
network: arbitrum
risk_score: 9
status: low
date: 2026-10-01
---

# Wrapped eETH (WEETH) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wrapped-eeth-arb)

---

## Audit Summary

This audit covers a StandardArbERC20 token contract, deployed as a Beacon proxy on Arbitrum. The contract implements standard ERC-20 functionality and includes specific bridging mechanisms. Key findings highlight significant control held by designated `gateway` and `l2gateway` addresses, allowing them to mint new tokens and directly manipulate user balances.

> **Final Recommendation:** It is crucial to implement robust security measures for the `gateway` and `l2gateway` addresses, as they possess significant control over token supply and user balances. Consider multi-signature wallets or time-locks for these privileged roles to mitigate the risk of single points of failure or compromise. Additionally, ensure that the Beacon controller responsible for upgrades is secured with similar high-assurance practices to prevent unauthorized changes to the contract's logic. Regular security reviews of the privileged addresses' operational security are highly recommended.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The StandardArbERC20 contract provides standard ERC-20 token functionalities (7.2 Code Security). It includes `bridgeMint` and `bridgeBurn` functions, restricted to `gateway` and `l2gateway`… |
| **Governance / Economics** | 9/10 | Low | The economic model of this token is heavily reliant on the integrity and security of the `gateway` and `l2gateway` addresses (7.4 Economic). These addresses have the power to mint an unlimited supply… |
| **Upgrades** | 5/10 | Medium | The contract is deployed using a Beacon proxy pattern (7.1 Architecture), which allows for its implementation logic to be upgraded (7.7 Upgrades). This provides flexibility for bug fixes and feature… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 36.6% |
| **Top-3 Unlocked** | 79.2% |

## Security Findings

_⚪ 6 Informational_

### `CP-01` — Centralized Control: Unlimited Token Minting  *(Severity: Informational · Status: Unresolved)*

The `gateway` and `l2gateway` addresses have the ability to call the `bridgeMint` function, which allows them to create an unlimited number of new tokens. This means that these controllers can increase the total supply of the token at any time, potentially diluting the value of tokens held by other users.

**Recommendation:** Token holders should be aware that the value of their tokens can be diluted by the `gateway` and `l2gateway` controllers. It is critical that these addresses are secured with the highest possible standards, such as multi-signature wallets, to prevent unauthorized minting.


### `CP-02` — Critical Control: Arbitrary Token Burning from Any Account  *(Severity: Informational · Status: Unresolved)*

The `gateway` and `l2gateway` addresses can execute the `bridgeBurn` function, which allows them to remove tokens from *any* token holder's balance. This means that these controllers have the power to unilaterally reduce or eliminate any user's token holdings, posing a severe risk to individual ownership and trust in the token.

**Recommendation:** Token holders must understand that the `gateway` and `l2gateway` controllers possess the ability to directly burn their tokens. The security of these controlling addresses is paramount. It is strongly recommended that these addresses are managed through highly secure mechanisms, such as multi-signature wallets with strict operational procedures, to prevent any misuse or compromise.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 98.2% of supply. What remains: 4.5% in wallets, 93.7% in other contracts. 18,885 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Arbitrum Bridged Wrapped eETH (Arbitrum) (WEETH), market cap $145M. 18,885 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $245K (DexScreener, all pools). 24h trading volume $39K (CoinGecko, all markets, daily snapshot). 24h trading volume $727K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Wrapped-Tokens. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $245K of DEX liquidity across 6 pools. Launch: 967 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3575...4dbe`](https://arbiscan.io/address/0x35751007a407ca6feffe80b3cb397736d2cf4dbe) |
| **Network** | Arbitrum |
| **Price** | $2,968.0140 |
| **24h Volume** | $656.7K |
| **Liquidity** | $155.0K |
| **Volume / Liquidity** | 4.2× |
| **Token Age** | 2y |
| **Top-10 Holders** | 98.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 84 buys / 78 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0x293dfd996d5cd72bed712b0eeab96dbe400c0416)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wrapped-eeth-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-01*
