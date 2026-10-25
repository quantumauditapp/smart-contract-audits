---
token: Inu
ticker: INU
network: solana
risk_score: 21
status: low
date: 2026-10-25
---

# Inu (INU) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/inu-sol-2232)

---

## Audit Summary

The Inu (INU) token is a standard SPL Token-2022 implementation with both mint and freeze authorities successfully revoked. The liquidity pool is fully locked, mitigating risks of rug pulls by the creator. However, the token exhibits signs of potential wash trading, and metadata remains mutable. Holder concentration data was unavailable for this assessment.

> **Final Recommendation:** Investors should monitor the token's trading volume to determine if the high ratio is driven by organic interest or artificial activity. Given the metadata mutability, verify the token's branding and identity through official channels before interacting.

Verify the current mint and freeze authority status on-chain using a block explorer to confirm they remain set to null. No further action is required regarding liquidity, as the 100% lock provides sufficient protection against immediate withdrawal.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program, ensuring modern extension compatibility. 7.1 Architecture and 7.2 Code Security are standard for this program type. 7.3 Access Control is robust, as… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic factors show a volume/liquidity ratio of 38.59, which exceeds the 20x threshold and suggests potential wash trading. 7.6 External market data confirms $18,037 in liquidity, which is… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are limited to metadata, which remains mutable. The mint and freeze authorities are permanently revoked, preventing further supply inflation or account freezing. No other upgradeable… |

## Security Findings

_🟠 1 High · 🟢 1 Low · ⚪ 6 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 38.59, which is significantly above the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Exercise caution and perform independent volume analysis before executing large trades.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

The token metadata (name, symbol, image) is mutable and can be changed by the owner at any time.

**Recommendation:** Verify the token identity against official project sources to ensure the branding has not been altered.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $18K (DexScreener, all pools). 24h trading volume $693K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (inu). Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $18K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2twakg...D62P`](https://solscan.io/account/2twakgqVuuaQ7EL1mmxv8kUBrXvmfkn9KbBA7ejKD62P) |
| **Network** | Solana |
| **Price** | $0.00003811 |
| **24h Volume** | $682.3K |
| **Liquidity** | $17.5K |
| **Volume / Liquidity** | 39.0× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 9926 buys / 7453 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/fsesb8evpy2igsv6sjgz6kad48uu6xaxvdcjlgaqtzmz)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/inu-sol-2232)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
