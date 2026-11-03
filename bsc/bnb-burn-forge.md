---
token: Bnb Burn Forge
ticker: BBF
network: bsc
risk_score: 47
status: medium
date: 2026-11-03
---

# Bnb Burn Forge (BBF) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 47/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bnb-burn-forge-bsc)

---

## Audit Summary

The WbnbTransferTaxToken is a highly centralized ERC-20 token with complex transfer logic tied to external oracle and router contracts. The controller holds significant power to modify tokenomics, mint supply, and halt transfers. While the architecture is modular, the reliance on privileged administrative functions creates a high trust requirement for token holders.

> **Final Recommendation:** Investors should be aware that the controller has the authority to mint tokens, change tax rates, and potentially halt transfers. We recommend transitioning to a multi-signature wallet or a decentralized governance contract to manage these privileged functions to reduce single-point-of-failure risks.

Ensure that the external contracts bound via bindPriceOracle and bindRouter are audited and verified, as the security of the token's transfer logic is entirely dependent on the behavior of these external components.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements standard ERC-20 functionality with custom hooks for tax processing and liquidity management. 7.1 Architecture is modular, separating price logic and routing into external… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic and 7.5 Governance aspects are entirely controlled by the contract owner. The ability to mint tokens and adjust tax parameters allows for arbitrary dilution of holders. There are no… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not implemented via proxy patterns; the contract is immutable. However, the logic is effectively 'upgradable' through the binding of new external oracle and router contracts. This… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.5% (≈ permanent lock) |
| **LP Locked** | 99.5% — Null Address |

## Security Findings

_🟠 1 High · 🟡 3 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `CP-03` — Arbitrary External Dependency Replacement  *(Severity: High · Status: Unresolved)*

The controller can change the price oracle contract address. Since transfers rely on this oracle, a malicious or compromised controller could redirect transfer logic or manipulate price data.

**Recommendation:** Restrict the ability to change the oracle address after the market has opened, or require a multi-step governance process for such changes.


### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The controller can mint new tokens at will using the mint function, which directly increases the total supply and dilutes the value of existing holdings.

**Recommendation:** Implement a hard cap on the total supply or move the minting authority to a time-locked governance contract.


### `CP-05` — Transfer Control Switch  *(Severity: Medium · Status: Unresolved)*

The controller can influence internal flags that determine whether transfers are allowed, effectively enabling a 'pause' or 'block' mechanism on token movement.

**Recommendation:** Document the specific conditions under which these switches are toggled and provide transparency to the community regarding their usage.


### `CP-07` — Dynamic Fee Manipulation  *(Severity: Medium · Status: Unresolved)*

The controller can modify tax parameters via the mint and releaseTaxTokens functions, allowing them to change the cost of transferring tokens for all users.

**Recommendation:** Set a maximum limit on the tax rate that can be configured to protect users from excessive fees.


### `CP-08` — Adjustable Transaction Limits  *(Severity: Low · Status: Unresolved)*

The controller can change transaction or wallet limits, which may impact the liquidity and trading behavior of the token.

**Recommendation:** Establish a clear policy for how and when these limits are adjusted to ensure predictability for holders.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 41.8% of supply. Of that, 7.1% burned, 23.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 10.1% in wallets, 1.1% in other contracts. 1,962 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,962 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.5% of the pool's LP is burned or time-locked. 99.5% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 0.5% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $65K (DexScreener, all pools). 24h trading volume $354K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: controller — a contract; officialpair — a contract; router — a contract. Code: not upgradeable (no proxy). Fees: 1% on buy, 1% on sell. Market: $65K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6fde...5232`](https://bscscan.com/address/0x6fde01375dee314c56193e177512767f88545232) |
| **Network** | BNB Chain |
| **Price** | $0.00000709 |
| **24h Volume** | $354.3K |
| **Liquidity** | $64.7K |
| **Volume / Liquidity** | 5.5× |
| **Token Age** | 18h |
| **Top-10 Holders** | 41.8% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 2802 buys / 6259 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x7e293f99d738a25c528f457224815506d7bf7290)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bnb-burn-forge-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
