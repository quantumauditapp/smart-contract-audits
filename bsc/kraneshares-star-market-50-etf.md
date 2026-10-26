---
token: KraneShares STAR Market 50 ETF
ticker: KSTRB
network: bsc
risk_score: 12
status: low
date: 2026-10-21
---

# KraneShares STAR Market 50 ETF (KSTRB) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 12/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kraneshares-star-market-50-etf-bsc)

---

## Audit Summary

The SecuritiesToken is a highly configurable, upgradeable ERC-20 token designed for regulated securities. It utilizes a beacon proxy pattern and extensive role-based access control to manage compliance, pause states, and token parameters. While the architecture is modular, the high degree of administrative control over core token logic introduces significant centralization risks.

> **Final Recommendation:** Implement a multi-signature wallet or a time-locked governance contract to manage the administrative roles. This will mitigate the risk of a single compromised key unilaterally altering compliance logic or token parameters.

Ensure that the external contracts linked via setCompliance and setPauseManager are also subject to rigorous security audits and are managed through similar multi-signature or decentralized governance processes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract follows standard OpenZeppelin upgradeable patterns (7.1 Architecture). Code security is robust, utilizing well-audited libraries for access control and ERC-20 compliance (7.2 Code… |
| **Governance / Economics** | 9/10 | Low | Governance is strictly centralized under role-based access control (7.3 Access Control, 7.5 Governance). Administrators have the power to alter token economics, including fees and multipliers (7.4… |
| **Upgrades** | 5/10 | Medium | The protocol uses a Beacon Proxy pattern, allowing for efficient implementation updates (7.7 Upgrades). Operations are managed through standard administrative roles (7.8 Operations). While this… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 50.0% |
| **Top-3 Unlocked** | ⚠️ 95.9% |

## Security Findings

_⚪ 8 Informational_

### `CP-03` — Centralized Control Over Core Token Logic  *(Severity: Informational · Status: Unresolved)*

The functions setPauseManager and setCompliance allow administrators to replace the external contracts that govern token transfers. Because transfers depend on these external contracts, an administrator can effectively halt or redirect the flow of tokens at will.

**Recommendation:** Restrict these functions to a multi-signature wallet or a time-locked governance contract to prevent unilateral changes.


### `CP-07` — Administrative Control Over Transfer Fees  *(Severity: Informational · Status: Unresolved)*

The setUIMultiplier function allows privileged roles to change the fee structure applied to token transfers. This gives administrators the ability to modify the economic cost of using the token without prior notice to users.

**Recommendation:** Implement a delay or a public notification period before fee changes take effect to protect users from sudden economic shifts.


### `CP-08` — Administrative Control Over Transfer Limits  *(Severity: Informational · Status: Unresolved)*

The setUIMultiplier function also controls numeric limits that affect transaction or wallet sizes. Administrators can adjust these thresholds, potentially restricting or enabling specific user behaviors.

**Recommendation:** Document the intended range for these limits and ensure that any changes are communicated transparently to the community.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 99.2% of supply. Of that, 8.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 60.6% in wallets, 30.3% in other contracts. 585 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as KraneShares STAR Market 50 ETF (bStocks Tokenized ETF) (KSTRB), rank #3334. Its admin (0x45e3…679d) controls 100 issuer-backed coins CoinGecko lists on bsc, $1.2B together, among them SpaceX (bStocks Tokenized Stock), Circle Internet Group (bStocks Tokenized Stock), SanDisk (bStocks Tokenized Stock): one issuer's programme, read on-chain. 585 holders. Verified by: issuer programme.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $392K (DexScreener, all pools). 24h trading volume $1.7M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Tokenized Commodity Exchange-Traded Products (ETPs). Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $392K of DEX liquidity across 30 pools. Launch: under a day of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5f16...d80c`](https://bscscan.com/address/0x5f1668b592cdf695b0c8e643a5a0078bb94cd80c) |
| **Network** | BNB Chain |
| **Price** | $19.5600 |
| **24h Volume** | $552.0K |
| **Liquidity** | $159.4K |
| **Volume / Liquidity** | 3.5× |
| **Token Age** | 9h |
| **Top-10 Holders** | 99.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2714 buys / 2804 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x4cc0e86036d751d1d5351b946c1bd6c6fd536cab)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kraneshares-star-market-50-etf-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
