---
token: PHP2SHELL
ticker: PHP2SHELL
network: solana
risk_score: 21
status: low
date: 2026-10-22
---

# PHP2SHELL (PHP2SHELL) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/php2shell-sol-7a22)

---

## Audit Summary

The PHP2SHELL token is a Token-2022 asset with both mint and freeze authorities successfully revoked, ensuring supply immutability and preventing account freezing. However, the token exhibits a high volume-to-liquidity ratio of 65.62, which is a strong indicator of wash trading. Holder concentration data is currently unavailable, and while liquidity is fully burned, the trading activity warrants caution.

> **Final Recommendation:** Investors should monitor the token's trading volume on decentralized exchanges to determine if the high volume-to-liquidity ratio persists, as this may indicate artificial market activity. Given the lack of holder concentration data, users should exercise caution regarding potential price volatility caused by large, undisclosed positions.

Verify the current supply and authority status directly via a block explorer to ensure no changes have occurred since this audit. Avoid interacting with the token if the volume-to-liquidity ratio continues to deviate significantly from standard market norms.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program, which provides advanced extension capabilities. 7.1 Architecture and 7.2 Code Security are standard for this program, with no custom transfer hooks or… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic and 7.5 Governance metrics show 100% of liquidity is burned, protecting against rug pulls via liquidity withdrawal. However, 7.6 External market data indicates a volume/liquidity ratio… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades and 7.8 Operations are effectively locked for this asset. Metadata is immutable, and there are no upgradeable extensions or balance-mutating authorities present. The token state is fixed… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 65.62, which exceeds the 20x threshold, indicating a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when trading; monitor for sustained, organic volume growth.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $20K (DexScreener, all pools). 24h trading volume $1.7M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $20K of DEX liquidity across 7 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Bo61v4...pump`](https://solscan.io/account/Bo61v44TWErCNGF4qzu2nEWyGgPWeNrNpu1FsV8dpump) |
| **Network** | Solana |
| **Price** | $0.00005368 |
| **24h Volume** | $1.57M |
| **Liquidity** | $20.0K |
| **Volume / Liquidity** | 78.7× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 13706 buys / 10683 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/6zf6wxhysvxa6ourz4nk2dhwg7ggjkpfnnxuujj7je9p)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/php2shell-sol-7a22)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
