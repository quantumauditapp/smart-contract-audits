---
token: KOTAI
ticker: KTI
network: bsc
risk_score: 59
status: medium
date: 2026-10-29
---

# KOTAI (KTI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 59/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kotai-bsc)

---

## Audit Summary

The KOTAI contract is a standard ERC-20 token implementation with additional administrative functionality for burning unsold tokens via a designated claim contract. The codebase is clean, follows standard OpenZeppelin patterns, and contains no complex logic that would introduce significant attack vectors. No vulnerabilities were identified during the static analysis of the provided source code.

> **Final Recommendation:** The contract is secure and ready for deployment. We recommend that the owner address be transitioned to a multi-signature wallet or a DAO-controlled contract to mitigate the risks associated with a single point of failure for administrative functions.

Ensure that the address designated as the 'claimContract' is thoroughly audited before deployment, as it holds the exclusive privilege to burn tokens from its own balance. No further technical changes are required at this time.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes standard ERC-20 compliance, ensuring compatibility with existing DeFi ecosystems. 7.1 Architecture is robust, relying on established libraries for token transfers and… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance aspects are centralized under the contract owner. The owner has the authority to set the claim contract, which is the only entity permitted to trigger the burnUnsold… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. The implementation is immutable, which provides security against logic-swap attacks but prevents future feature updates. 7.8 Operations… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 97.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 5 Informational_

### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 99.9% in wallets, 0.0% in other contracts. The deployer/owner wallet itself holds 95.0%. A holder that also controls the contract can sell into its own liquidity. 1,222 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0xe009…9421 — holds 97.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as KOTAI (KTI). 1,222 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.7M (GeckoTerminal, all pools). 24h trading volume $76K (CoinGecko, all markets, daily snapshot). 24h trading volume $33K (GeckoTerminal, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.7M of DEX liquidity across 13 pools. Launch: 15 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 15 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 15 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe254...b9d6`](https://bscscan.com/address/0xe254ee6b463807b6f8040797ccd909f5ecddb9d6) |
| **Network** | BNB Chain |
| **Price** | $0.00790914 |
| **24h Volume** | $32.5K |
| **Liquidity** | $1.63M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 15d |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 142 buys / 65 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xe254ee6b463807b6f8040797ccd909f5ecddb9d6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kotai-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
