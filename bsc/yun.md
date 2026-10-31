---
token: YUN
ticker: YUN
network: bsc
risk_score: 79
status: high
date: 2026-10-31
---

# YUN (YUN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 79/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/yun-bsc)

---

## Audit Summary

The YUN token is a standard ERC-20 implementation with added centralized controls for taxes, blacklisting, and trading status. While the core token logic follows standard patterns, the contract grants the owner significant power to restrict user activity and modify economic parameters. 7.1 Architecture: Standard ERC-20 with custom hooks. 7.2 Code Security: Standard implementation. 7.3 Access Control: Centralized owner control. 7.4 Economic: Owner-defined tax rates. 7.5 Governance: None. 7.6 External: No external integrations. 7.7 Upgrades: None. 7.8 Operations: Owner-managed.

> **Final Recommendation:** Token holders should be aware that the contract owner possesses absolute control over the ability to trade and the economic cost of transfers. It is recommended that the owner renounce ownership or transition to a multi-signature wallet or decentralized governance model to mitigate the risk of unilateral actions.

Users should monitor the contract for any changes to the tax rates or trading status, as these can be modified at any time by the owner. No further technical changes are required for the current logic, but the centralization of power remains a significant concern for long-term holders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes a standard OpenZeppelin-style ERC-20 structure, ensuring compatibility with common DeFi protocols. The code is clean and follows established patterns for token transfers.… |
| **Governance / Economics** | 1/10 | High | The economic model is entirely controlled by the contract owner, who can adjust buy/sell taxes at will. This creates a high risk for token holders, as the owner could theoretically set taxes to 100%… |
| **Upgrades** | 6/10 | Medium | The contract is not upgradeable, meaning the logic is immutable once deployed. This eliminates risks associated with proxy-based upgrade vulnerabilities. However, it also means that any errors in the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 6.9% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | ⚠️ 93.1% |
| **Top-3 Unlocked** | ⚠️ 93.1% |

## Security Findings

_🟡 4 Medium · ⚪ 5 Informational_

### `CP-05` — Centralized Control Over Trading Status  *(Severity: Medium · Status: Unresolved)*

The owner can use the setCanBuy and setCanSell functions to completely halt trading for all users. This allows the owner to prevent any buying or selling activity at their discretion.

**Recommendation:** Implement a time-lock or a decentralized voting mechanism for these functions to prevent sudden, unilateral trading halts.


### `CP-06` — Arbitrary Blacklisting of Holders  *(Severity: Medium · Status: Unresolved)*

The setBlacklisted function allows the owner to prevent specific addresses from transferring or selling their tokens. This effectively gives the owner the power to freeze user assets.

**Recommendation:** Remove the blacklist functionality or restrict its use to a transparent, community-voted process for addressing malicious activity only.


### `CP-07` — Owner-Controlled Transfer Fees  *(Severity: Medium · Status: Unresolved)*

The setTaxes function allows the owner to change the buy and sell tax rates at any time. This could be used to extract value from users or make the token effectively untradeable.

**Recommendation:** Set a hard cap on the maximum tax rate that can be set by the owner and implement a time-lock for any changes to the tax parameters.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

6.9% of the pool's LP is burned or time-locked. 3.0% is locked in PinkLock02 until 26 Oct 2027 (359 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. 3.0% is locked in PinkLock02 until 27 Oct 2027 (360 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. 0.9% is locked in PinkLock02 until 30 Oct 2027 (363 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. 93.1% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x8c6b…6c27 — holds 93.1% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 0.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 99.8% in wallets, 0.0% in other contracts. 1,577 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,577 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $2.4M (DexScreener, all pools). 24h trading volume $863K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: 3% on buy, 3% on sell. Market: $2.4M of DEX liquidity across 1 pools. Launch: 5 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 5 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 5 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf2d1...a050`](https://bscscan.com/address/0xf2d11c1bbfd249f7107d5b0ef4378a87b286a050) |
| **Network** | BNB Chain |
| **Price** | $0.7155 |
| **24h Volume** | $862.8K |
| **Liquidity** | $2.40M |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 5d |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 6721 buys / 6765 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xed54f0a0c7b4fa14a1971ceb72853f741c5e197c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/yun-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
