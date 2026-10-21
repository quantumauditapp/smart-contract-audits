---
token: Kimchi Wif Hat
ticker: WIFCHI
network: solana
risk_score: 21
status: low
date: 2026-10-21
---

# Kimchi Wif Hat (WIFCHI) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kimchi-wif-hat-sol)

---

## Audit Summary

The Kimchi Wif Hat token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. While liquidity is fully burned, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading. Holder concentration data was unavailable from the provided sources.

> **Final Recommendation:** Investors should be aware that the high volume-to-liquidity ratio may not reflect organic market demand. Monitor the token's price action and liquidity depth on-chain before executing large trades to avoid significant slippage.

Verify the current supply and authority status using a block explorer to confirm that no unauthorized minting or freezing capabilities have been introduced through secondary programs.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the Token-2022 program. 7.1 Architecture is standard for SPL tokens, with 7.2 Code Security relying on the audited native program. 7.3 Access Control is robust as both… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic stability is impacted by a high volume-to-liquidity ratio of 32.10, which exceeds the 20 threshold for wash-trading signals. 7.5 Governance is decentralized as the mint authority is… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to this mint as it is a standard SPL token. 7.8 Operations are transparent with metadata mutability disabled, ensuring the token identity cannot be altered… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 32.10, which is significantly higher than the 20 threshold, indicating potential artificial trade volume.

**Recommendation:** Exercise caution when interpreting volume metrics and account for potential liquidity constraints.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $36K (DexScreener, all pools). 24h trading volume $1.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (wif); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $36K of DEX liquidity across 3 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8uWftz...pump`](https://solscan.io/account/8uWftzVoVBqyPJj6Xq9kRUtnz54W5GP4pd4smwZHpump) |
| **Network** | Solana |
| **Price** | $0.0001699 |
| **24h Volume** | $1.13M |
| **Liquidity** | $35.6K |
| **Volume / Liquidity** | 31.7× |
| **Token Age** | 2h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 21996 buys / 3666 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/afpgdkhfswvwkkcp6a3knwsbl4ltybpg5zgsxa2bzuqt)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kimchi-wif-hat-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
