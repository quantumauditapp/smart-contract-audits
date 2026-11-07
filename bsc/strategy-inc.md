---
token: Strategy Inc.
ticker: MSTRB
network: bsc
risk_score: 9
status: low
date: 2026-11-07
---

# Strategy Inc. (MSTRB) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/strategy-inc-bsc)

---

## Audit Summary

The SecuritiesToken is an upgradeable ERC-20 implementation designed for regulated asset issuance. It utilizes a robust role-based access control system and external compliance/pause modules. While the architecture is modular, the high degree of centralized control over core logic and transfer parameters introduces significant trust requirements for token holders.

> **Final Recommendation:** Implement a multi-signature wallet or a time-locked governance contract to manage the privileged roles. This will mitigate the risk of a single compromised key performing unauthorized changes to compliance, pause, or fee settings.

Ensure that all external compliance and pause contracts are audited and their source code is verified. Regularly monitor the state of these external dependencies to ensure they continue to function as intended within the token's transfer flow.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The architecture (7.1) follows standard UUPS/Beacon proxy patterns, ensuring upgradeability. Code security (7.2) is high, utilizing OpenZeppelin libraries for standard ERC-20 and AccessControl.… |
| **Governance / Economics** | 9/10 | Low | Economic parameters (7.4) such as UI multipliers and minting are fully controlled by privileged roles. Governance (7.5) is currently centralized, meaning token holders have no direct influence over… |
| **Upgrades** | 5/10 | Medium | Upgrades (7.7) are managed via the Beacon proxy pattern, allowing for seamless logic updates. Operations (7.8) are supported by pause and compliance modules that can be swapped. The primary risk is… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 38.4% |
| **Top-3 Unlocked** | 79.0% |

## Security Findings

_⚪ 7 Informational_

### `CP-03` — Centralized Control Over Core Logic  *(Severity: Informational · Status: Unresolved)*

The functions setPauseManager and setCompliance allow a privileged address to replace the contracts that govern token transfers. This means an administrator can unilaterally change the rules of the token, including pausing all transfers or altering compliance requirements.

**Recommendation:** Transition the administrative role to a multi-signature wallet or a decentralized governance contract to prevent single-point-of-failure risks.


### `CP-07` — Administrative Control Over Transfer Fees  *(Severity: Informational · Status: Unresolved)*

The setUIMultiplier function allows a privileged address to modify the transfer fee structure. This gives the controller the ability to change the cost of moving tokens at any time.

**Recommendation:** Consider implementing a maximum fee cap or a time-lock mechanism for fee changes to provide transparency and protection to token holders.


### `CP-08` — Administrative Control Over Transfer Limits  *(Severity: Informational · Status: Unresolved)*

The setUIMultiplier function also influences numeric limits checked during transfers. A privileged address can adjust these thresholds, potentially restricting or enabling specific transaction sizes.

**Recommendation:** Document the intended range for these limits and provide public visibility into any changes made to these parameters.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 95.2% of supply. What remains: 95.2% in wallets, 0.0% in other contracts. 9,948 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Strategy (bStocks Tokenized Stock) (MSTRB), market cap $47M, rank #454. Its admin (0x45e3…679d) controls 105 issuer-backed coins CoinGecko lists on bsc, $1.2B together, among them SpaceX (bStocks Tokenized Stock), Circle Internet Group (bStocks Tokenized Stock), Alphabet (bStocks Tokenized Stock): one issuer's programme, read on-chain. 9,948 holders. Verified by: issuer programme.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $382K (DexScreener, all pools). 24h trading volume $25.2M (CoinGecko, all markets, daily snapshot). 24h trading volume $324K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Tokenized Stocks. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $382K of DEX liquidity across 13 pools. Launch: 88 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe87a...6a14`](https://bscscan.com/address/0xe87afb3076aeb0f9b14e368de8145ae6a2826a14) |
| **Network** | BNB Chain |
| **Price** | $129.4600 |
| **24h Volume** | $314.8K |
| **Liquidity** | $310.6K |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 95.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 827 buys / 846 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x692081209619735f25700557078ab084d3e5d007)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/strategy-inc-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
