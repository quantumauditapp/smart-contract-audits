---
token: PEPEween
ticker: PEPEWEEN
network: solana
risk_score: 29
status: low
date: 2026-10-28
---

# PEPEween (PEPEWEEN) — Smart Contract Security Analysis | Solana

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pepeween-sol)

---

## Audit Summary

The PEPEween token utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully burned, ensuring the pool cannot be rug-pulled by the creator. Holder concentration data is currently unavailable, and liquidity is below the $10,000 threshold, which may impact trade execution.

> **Final Recommendation:** Investors should monitor the liquidity levels, as the current pool size is below $10,000, which may lead to significant slippage during trades. Since holder concentration data is unavailable, users should exercise caution regarding potential price volatility from large individual wallets.

Verify the current supply and authority status directly via a block explorer to confirm that no changes have occurred since this audit. Ensure that any future interactions are conducted through reputable DEX interfaces.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the SPL Token-2022 program, which provides advanced extension capabilities. 7.1 Architecture and 7.2 Code Security are standard for this program. 7.3 Access Control is… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic factors show a total liquidity of $9,990, which is below the $10,000 safety threshold. 7.5 Governance is decentralized due to the revocation of minting rights. 7.6 External market data… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is a fixed-supply asset. Metadata is immutable, and extension settings such as transfer fees are not upgradable. The token configuration is static and… |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 4 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $9,990. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the fee in any swap calculation.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $10K (DexScreener, all pools). 24h trading volume $71K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (pepe); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`5C5K1Z...pump`](https://solscan.io/account/5C5K1ZetdvGoF5QRcyRbVMiVLhkJzS8RkH8UL2pwpump) |
| **Network** | Solana |
| **Price** | $0.00001787 |
| **24h Volume** | $40.3K |
| **Liquidity** | $9.6K |
| **Volume / Liquidity** | 4.2× |
| **Token Age** | 7h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 403 buys / 361 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/5nbbsufa547vr74djq3jwdg7ygtdicpwhzdw4bmqo2w8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pepeween-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
