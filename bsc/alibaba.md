---
token: Alibaba
ticker: BABAB
network: bsc
risk_score: 81
status: high
date: 2026-10-15
---

# Alibaba (BABAB) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 81/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/alibaba-bsc)

---

## Audit Summary

The SecuritiesToken is an upgradeable ERC-20 token designed with extensive administrative control. Key functionalities like transfer rules, fees, and external compliance/pause mechanisms are centrally managed by a privileged role. While this allows for flexibility and regulatory compliance, it introduces significant centralization risks, as a compromise of the controlling address could lead to manipulation of token behavior or funds.

> **Final Recommendation:** It is crucial to secure the DEFAULT_ADMIN_ROLE with the highest possible standards, ideally using a robust multi-signature wallet solution with a high threshold for execution. All changes to critical parameters, especially those affecting transfer logic, fees, or external contract addresses, should be communicated transparently to token holders. Consider implementing a time-lock mechanism for sensitive administrative actions to provide a window for review and reaction.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The SecuritiesToken is an upgradeable ERC-20 token leveraging OpenZeppelin's AccessControlEnumerableUpgradeable for robust role-based access management (7.3 Access Control). It integrates external… |
| **Governance / Economics** | 1/10 | High | The token's economic model and governance are highly centralized, with a DEFAULT_ADMIN_ROLE controlling critical functions (7.5 Governance). This role can enable/disable minting and burning, set the… |
| **Upgrades** | 1/10 | High | The SecuritiesToken is deployed via a Beacon Proxy pattern, enabling future upgrades to its logic (7.7 Upgrades). This design allows for bug fixes and feature enhancements without redeploying the… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 70.8% |
| **Top-3 Unlocked** | ⚠️ 88.4% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `CP-03` — Centralized Control Over Critical External Contracts  *(Severity: High · Status: Unresolved)*

A privileged address, specifically the one holding the `DEFAULT_ADMIN_ROLE`, has the ability to replace the `PauseManager` and `Compliance` contracts. These external contracts are called during token transfers to determine if a transfer is allowed or paused. If the controlling address is compromised, it could redirect token logic to a malicious contract, potentially blocking all transfers or imposing arbitrary rules.

**Recommendation:** Token holders should be aware that the administrator can change the core logic governing transfers by updating the `PauseManager` (via `setPauseManager` function) and `Compliance` (via `setCompliance` function) contract addresses. This power should be secured by a multi-signature wallet and any changes should be publicly announced with sufficient lead time.


### `CP-07` — Administrator Can Change Transfer Fees  *(Severity: Medium · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE` has the power to modify the `_uiMultiplier` parameter using the `setUIMultiplier` function. This parameter directly influences the fees or amounts deducted during token transfers. A malicious or compromised administrator could set excessively high fees, impacting the economic viability of token transactions for users.

**Recommendation:** Token holders should understand that the administrator can change the fees associated with transfers using the `setUIMultiplier` function. It is recommended that any changes to transfer fees are communicated transparently and that the controlling role is secured with a multi-signature wallet to prevent unauthorized modifications.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 94.2% is held, unlocked, by 10 address(es) other than the owner/deployer. One of them — a wallet, 0x5b0d…a9b9 — holds 70.8% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 89% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-08` — Administrator Can Change Transfer Limits  *(Severity: Low · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE` can adjust numeric limits checked during the transfer process, such as those related to the UI multiplier, via the `setUIMultiplier` function. While not directly a "fee," changes to this multiplier could indirectly affect perceived transfer amounts or introduce unexpected behavior related to how amounts are scaled or validated.

**Recommendation:** Token holders should be aware that the administrator can modify certain numeric parameters that might affect how transfers are processed, using the `setUIMultiplier` function. While this might not directly impose a fee, it could alter how amounts are calculated or validated. This control should be managed responsibly and transparently.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 92.1% of supply. Of that, 22.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 66.2% in wallets, 3.0% in other contracts. 35,218 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Alibaba (bStocks Tokenized Stock) (BABAB), market cap $9M, rank #1308. 35,218 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $2.9M (DexScreener, all pools). 24h trading volume $13.8M (CoinGecko, all markets, daily snapshot). 24h trading volume $4.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Tokenized Stocks. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $2.9M of DEX liquidity across 30 pools. Launch: 73 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4ef9...f4ec`](https://bscscan.com/address/0x4ef9d3062c7f6eba4aae4990c5036598c6eff4ec) |
| **Network** | BNB Chain |
| **Price** | $108.9800 |
| **24h Volume** | $2.50M |
| **Liquidity** | $2.53M |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 92.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4306 buys / 5139 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xfd95cb1391999006eb91797a7c62acfe88b20292)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/alibaba-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-15*
