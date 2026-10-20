---
token: Minpentai
ticker: PENTA
network: ethereum
risk_score: 78
status: high
date: 2026-10-03
---

# Minpentai (PENTA) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 78/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/minpentai-eth)

---

## Audit Summary

The PentaToken contract implements an ERC-20 token with additional functionality for managing a treasury and tax exemptions. The audit found no critical, high, medium, or low severity vulnerabilities. The contract's design includes owner-controlled functions that allow for dynamic adjustment of transfer rules and treasury address.

> **Final Recommendation:** Given the owner's significant control over the token's economic parameters, it is crucial to ensure the owner's private key is secured with multi-signature wallets or robust access control mechanisms. Transparency regarding the use of `setTreasury` and `setTaxExempt` functions should be maintained to foster community trust. Consider renouncing ownership if the centralized control is not intended for long-term operation, or transfer ownership to a well-governed DAO.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The PentaToken contract is an ERC-20 compliant token, inheriting from OpenZeppelin's Ownable and ERC20. It correctly implements standard token functionalities such as `transfer` and `transferFrom`… |
| **Governance / Economics** | 1/10 | High | The contract retains ownership, granting significant control to the deployer. The owner can modify economic parameters by calling `setTreasury(address)` to change the recipient of collected taxes and… |
| **Upgrades** | 5/10 | Medium | The PentaToken contract is not implemented as an upgradeable proxy (7.7 Upgrades). This means its logic is immutable once deployed, preventing any future modifications or bug fixes without a complete… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by the token's owner/deployer (0x1ad2…62f1) — they can pull that liquidity at any moment. This is the rug-pull path. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 87.6% of supply. What remains: 24.6% in wallets, 63.0% in other contracts. The deployer/owner wallet itself holds 5.8%. 79 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

79 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $19K (DexScreener, all pools). 24h trading volume $46K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: 0.49% on buy, 0.49% on sell. Market: $19K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x07db...1c91`](https://etherscan.io/address/0x07db563340c60ba421b9802aa0369dc5b70a1c91) |
| **Network** | Ethereum |
| **Price** | $0.0000435 |
| **24h Volume** | $46.4K |
| **Liquidity** | $19.3K |
| **Volume / Liquidity** | 2.4× |
| **Token Age** | 16h |
| **Top-10 Holders** | 87.6% of supply |
| **Buy / Sell Tax** | 0.5% / 0.5% |
| **24h Transactions** | 221 buys / 114 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xf0293c18e57ee354b204025096251b30e277aa9ccf6c3b05d8710f479a1cf263)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/minpentai-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-03*
