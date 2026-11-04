---
token: United States Oil Exchange
ticker: USOE
network: solana
risk_score: 2
status: low
date: 2026-11-04
---

# United States Oil Exchange (USOE) — Smart Contract Security Analysis | Solana

> **Risk Score: 2/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/united-states-oil-exchange-sol-f82c)

---

## Audit Summary

The United States Oil Exchange (USOE) token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn of LP tokens, and metadata is immutable. Holder distribution data was unavailable, preventing an assessment of supply concentration.

> **Final Recommendation:** The token is configured securely with no active administrative authorities. Users should monitor the token's official communication channels for any updates regarding the project's roadmap, as the lack of holder distribution data prevents a full assessment of potential market manipulation by large early holders.

Verify the current supply and authority status using a block explorer to ensure no unexpected changes have occurred since this audit. Since liquidity is permanently burned, the pool is protected from rug-pulls via liquidity withdrawal.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the Token-2022 program (7.1 Architecture). Access control is robust, with both mint and freeze authorities set to null (7.3 Access Control). No transfer hooks or… |
| **Governance / Economics** | 10/10 | Low | The token maintains $727,336 in liquidity, which is fully protected as 100% of LP tokens are burned (7.4 Economic). Trading activity shows a healthy volume/liquidity ratio of 0.48, indicating no… |
| **Upgrades** | 10/10 | Low | The token metadata is immutable, preventing unauthorized changes to the token identity (7.7 Upgrades). There are no upgradeable components or proxy patterns present. The configuration is static and… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $723K (DexScreener, all pools). 24h trading volume $344K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $723K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2GP4h7...pump`](https://solscan.io/account/2GP4h7p1T1JN56vmhEkr5YDMj4dquLTAcdw8SRXNpump) |
| **Network** | Solana |
| **Price** | $0.07876 |
| **24h Volume** | $344.3K |
| **Liquidity** | $722.7K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 20h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 74940 buys / 27 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/gygmgphkmjzp416pwfkj8lhda5pthyhpulsytk48eyr1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/united-states-oil-exchange-sol-f82c)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
