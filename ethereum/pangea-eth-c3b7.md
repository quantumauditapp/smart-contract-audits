---
token: Pangea
ticker: PANGEA
network: ethereum
risk_score: 38
status: medium
date: 2026-10-22
---

# Pangea (PANGEA) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 38/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pangea-eth-c3b7)

---

## Audit Summary

The contract is a standard ERC-20 token with additional tax, limit, and trading control features. Ownership has been renounced, effectively locking the administrative functions and preventing further changes to the tokenomics or transfer rules. The code is functional, though it contains minor arithmetic and authorization patterns that are common in this token category.

> **Final Recommendation:** The contract is currently in a secure, immutable state due to the renouncement of ownership. No further administrative actions can be taken, which protects users from rug-pull scenarios involving fee or limit changes. 

Users should be aware that the existing logic, including the use of tx.origin and potential rounding errors, is permanently baked into the contract. No further security patches can be applied, so users should perform their own due diligence on the current fee structure and transfer constraints.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements standard ERC-20 functionality with custom logic for automated market maker (AMM) interactions. 7.1 Architecture is straightforward, utilizing OpenZeppelin's Ownable and ERC20… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic parameters such as buy/sell fees and transaction limits are currently fixed. 7.5 Governance is non-existent as the owner address is set to zero. This prevents any future adjustments to… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not supported by this contract. The logic is immutable, which eliminates risks associated with proxy-based upgrade patterns. 7.8 Operations are stable as the contract is fully… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 9 Informational_

### `CD-02` — Use of tx.origin for Authorization  *(Severity: Medium · Status: Unresolved)*

The contract uses tx.origin in the transfer path. This is a risky pattern as it can be exploited if users are tricked into interacting with malicious contracts that initiate transfers on their behalf.

**Recommendation:** Use msg.sender instead of tx.origin for all authorization and rule-based logic.


### `CD-01` — Rounding Loss in Transfers  *(Severity: Low · Status: Unresolved)*

The _transfer function performs division before multiplication, which can lead to minor rounding errors in fee calculations.

**Recommendation:** Ensure multiplication is performed before division to maintain precision.


### `CP-05` — Dormant Administrative Switches  *(Severity: Informational · Status: Unresolved)*

Functions like enableTrading and removeLimits control critical transfer switches. Since ownership is renounced, these functions are now inaccessible, rendering the switches permanently locked in their current state.

**Recommendation:** No action required as the renouncement provides a security guarantee against future changes.


### `CP-07` — Dormant Fee Configuration  *(Severity: Informational · Status: Unresolved)*

The functions updateSellFees and updateBuyFees allow for the modification of transaction taxes. These are currently locked and cannot be adjusted by any party.

**Recommendation:** None.


### `CP-08` — Dormant Transaction Limits  *(Severity: Informational · Status: Unresolved)*

Functions controlling max transaction and wallet amounts are locked. The current limits are immutable.

**Recommendation:** None.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The holder list from the security indexer adds up to 127.5% of supply, so it does not describe real balances. That happens with rebasing and reflection tokens, whose balances change without transfers, and with contracts that report balances they do not hold. Concentration is unknown and priced as an unknown — neither a whale nor safe.

**Recommendation:** Check the largest holders on the block explorer, which reads current balances.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

226 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $41K (DexScreener, all pools). 24h trading volume $247K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $41K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfde7...6f9f`](https://etherscan.io/address/0xfde7c90c5da4b761dfb20db69f43b3171fa76f9f) |
| **Network** | Ethereum |
| **Price** | $0.0001615 |
| **24h Volume** | $247.4K |
| **Liquidity** | $41.0K |
| **Volume / Liquidity** | 6.0× |
| **Token Age** | 4h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 420 buys / 348 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x0a91e5808dde9cfe7fb8f72e065e22041532f429)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pangea-eth-c3b7)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
