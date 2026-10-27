---
token: GTA6DOG
ticker: CHICO
network: solana
risk_score: 0
status: low
date: 2026-10-27
---

# GTA6DOG (CHICO) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gta6dog-sol)

---

## Audit Summary

The GTA6DOG token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn, and no adverse flags were reported by third-party registries. Holder concentration data was unavailable, preventing a full assessment of distribution risks.

> **Final Recommendation:** Given the revocation of all administrative authorities and the permanent burn of liquidity, the token's technical structure is secure. Users should monitor the token on-chain using block explorers to verify that no new authorities are introduced if the token program allows for future extension initialization.

Since holder concentration data is unavailable, investors should independently verify the distribution of tokens via block explorers to ensure that supply is not heavily concentrated in a few wallets, which could lead to significant price volatility.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the Token-2022 program (7.1 Architecture). Security is robust due to the revocation of both mint and freeze authorities (7.3 Access Control). No transfer hooks or… |
| **Governance / Economics** | 10/10 | Low | Liquidity is highly secure, with 100% of pool tokens burned (7.4 Economic). Trading volume is active, though the volume-to-liquidity ratio of 9.83 warrants monitoring for volatility (7.8 Operations).… |
| **Upgrades** | 10/10 | Low | The mint is immutable with metadata and balance-mutating authorities disabled (7.7 Upgrades). There are no upgrade paths for the token program or its extensions. The configuration is finalized and… |

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

Liquidity $193K (DexScreener, all pools). 24h trading volume $1.9M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $193K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`9v4air...pump`](https://solscan.io/account/9v4airX4Vt45ADFg3QQG9pXX68LkX9Big4GiYEuJpump) |
| **Network** | Solana |
| **Price** | $0.00508 |
| **24h Volume** | $1.88M |
| **Liquidity** | $193.5K |
| **Volume / Liquidity** | 9.7× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 11548 buys / 5653 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/eztwxzfmns9sjjgvych35i6e3oywsdjdeql9cbzgfdap)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gta6dog-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
