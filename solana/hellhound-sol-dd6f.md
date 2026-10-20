---
token: Hellhound
ticker: HELL
network: solana
risk_score: 0
status: low
date: 2026-10-20
---

# Hellhound (HELL) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/hellhound-sol-dd6f)

---

## Audit Summary

The Hellhound (HELL) token utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn, mitigating risks associated with pool withdrawal. Holder concentration data is currently unavailable, and a third-party registry flags high holder correlation, which warrants caution regarding potential market manipulation.

> **Final Recommendation:** Investors should monitor the token's market activity given the third-party registry flag regarding high holder correlation. Since holder distribution data is unavailable, users should verify the current top holder addresses via block explorers before executing large trades to ensure they are not interacting with a single concentrated entity.

Verify the current mint and freeze authority status periodically on-chain to ensure no unexpected state changes occur, although the current revocation is permanent. No further technical action is required as the core security parameters are correctly configured.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented on the SPL Token-2022 program, ensuring modern extension support. 7.1 Architecture is standard for SPL mints, with 7.2 Code Security relying on the audited core program. 7.3… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by $255,298 in liquidity, which is 100% burned. 7.5 Governance is decentralized due to the lack of minting capabilities. 7.6 External signals indicate high holder… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to this mint as it is a standard SPL token. Metadata is immutable, and no transfer fee or hook upgrades are enabled. The token configuration is static and cannot be… |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `M-01` — High Holder Correlation Flag  *(Severity: Medium · Status: Unresolved)*

A third-party risk registry has flagged the token for high holder correlation, suggesting that a significant portion of the supply may be controlled by a small group of related entities.

**Recommendation:** Perform due diligence on the top token accounts to identify potential concentration risks before committing capital.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $255K (DexScreener, all pools). 24h trading volume $206K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $255K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`BYgXaw...pump`](https://solscan.io/account/BYgXawj9okdtqqkjZpVsesHE7BBH9AMoQ5HaWNwvpump) |
| **Network** | Solana |
| **Price** | $0.008755 |
| **24h Volume** | $205.9K |
| **Liquidity** | $254.9K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 9h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 22825 buys / 377 sells |

## Security Flags (4/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/5tbmyklidanuds4bo4nsxrjh2h2kdh8a9jknwte57ugs)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/hellhound-sol-dd6f)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
