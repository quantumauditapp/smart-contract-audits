---
token: Darkex
ticker: DARKEX
network: bsc
risk_score: 57
status: medium
date: 2026-10-10
---

# Darkex (DARKEX) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/darkex-bsc)

---

## Audit Summary

The Darkex contract is an ERC-20 token with significant owner privileges. The owner can control critical aspects such as token transfer enablement, transaction fees, and fund withdrawals. While the contract implements standard ERC-20 functionality, these centralized controls introduce medium-level risks related to economic manipulation and operational decisions. Three medium-severity findings were identified.

> **Final Recommendation:** For token holders, it is crucial to understand the extensive control the contract owner possesses over token transfers, fees, and treasury operations. Project teams should consider implementing multi-signature wallets for critical administrative functions to distribute control and reduce single points of failure. Additionally, all low-level calls, particularly those involving external interactions like `swapTokensForEth()`, must have their return values thoroughly checked to prevent unexpected behavior and potential loss of funds. Enhancing transparency around administrative actions and their potential impact on the token ecosystem is also highly recommended.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The Darkex contract implements standard ERC-20 token functionalities, including `transfer` and `transferFrom`. The contract owner retains significant control, allowing them to withdraw ETH and tokens… |
| **Governance / Economics** | 4/10 | Medium | The contract's economic parameters are highly centralized under owner control. The owner can set the `treasuryAddress` and exclude accounts from fees using `setTreasuryAddress()` and… |
| **Upgrades** | 7/10 | Low | The Darkex contract is not designed as an upgradeable proxy contract (7.7 Upgrades). This means its logic cannot be modified after deployment, providing immutability but also preventing future bug… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — Null Address, PinkLock02 |

## Security Findings

_🟡 3 Medium · ⚪ 6 Informational_

### `CD-01` — Unchecked Low-Level Call in `manualSwap()`  *(Severity: Medium · Status: Unresolved)*

The `manualSwap()` function, callable by the owner, executes a `swapTokensForEth()` function which might contain an unchecked low-level call. If `swapTokensForEth()` fails for any reason (e.g., insufficient liquidity, reentrancy guard), the transaction might still proceed without reverting, potentially leading to unexpected state inconsistencies or loss of funds.

**Recommendation:** The `swapTokensForEth()` function, especially if it involves external calls, should ensure that all return values from low-level calls are properly checked and handled. This prevents unexpected behavior and potential loss of assets if the external call fails.


### `CP-05` — Owner Can Pause or Block Token Transfers  *(Severity: Medium · Status: Unresolved)*

The contract owner has the ability to enable or disable token swaps and manual swaps using the `toggleSwap()` and `manualSwap()` functions. This means the owner can effectively pause or block the ability for users to transfer or sell their tokens, which could disrupt trading or liquidity.

**Recommendation:** Token holders should be aware that the owner can control the ability to transfer tokens. It is recommended that the project clearly communicates the conditions under which these controls might be exercised and consider implementing a multi-signature wallet for such critical functions to reduce single-point-of-failure risk.


### `CP-07` — Owner Can Change Token Transfer Fees  *(Severity: Medium · Status: Unresolved)*

The contract owner can modify the `reflectionTax` and `treasuryTax` applied to token transfers using the `setFee()` function. This allows the owner to increase or decrease the fees taken from every token transaction, potentially impacting the value and liquidity of the token without prior notice.

**Recommendation:** Token holders should understand that the owner can unilaterally change transfer fees. Transparency regarding fee changes is crucial. Consider decentralizing this control or implementing a time-locked mechanism for fee changes to provide users with advance notice.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 92.1% of supply. Of that, 84.7% locked, 1.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 5.6% in wallets, 0.0% in other contracts. 331 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Darkex (DARKEX), rank #4348. 331 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% is locked in PinkLock02 until 05 Dec 2026 (56 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $52K (DexScreener, all pools). 24h trading volume $56K (CoinGecko, all markets, daily snapshot). 24h trading volume $45K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: 4.5% on buy, 4.5% on sell. Market: $52K of DEX liquidity across 1 pools. Launch: 16 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 16 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 16 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0d0b...03b9`](https://bscscan.com/address/0x0d0b469508d9f30cd481d10d4cd695481ff503b9) |
| **Network** | BNB Chain |
| **Price** | $0.01434 |
| **24h Volume** | $45.0K |
| **Liquidity** | $51.9K |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 16d |
| **Top-10 Holders** | 92.1% of supply |
| **Buy / Sell Tax** | 4.5% / 4.5% |
| **24h Transactions** | 87 buys / 98 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xb2124c5c89cff74dc231a6468ebb8d30de627884)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/darkex-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-10*
