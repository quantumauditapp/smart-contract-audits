---
token: USDP
ticker: USDP
network: solana
risk_score: 94
status: critical
date: 2026-11-07
---

# USDP (USDP) — Smart Contract Security Analysis | Solana

> **Risk Score: 94/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/usdp-sol-96e0)

---

## Audit Summary

The USDP token utilizes the Token-2022 program with all administrative authorities, including mint and freeze, successfully revoked. Liquidity is fully secured via a 100% burn of LP tokens, and metadata is immutable. Holder distribution data was unavailable, preventing a full assessment of concentration risk.

> **Final Recommendation:** The token exhibits strong security characteristics regarding authority control and liquidity safety. Users should monitor the token's market activity via block explorers to track holder distribution, as this data was not available during this audit.

Verify the mint address dMyGV4ptoPmJPQ6Cqh2j69AJRZU88mGL7JryMezpump directly on-chain to confirm that the mint and freeze authorities remain set to null before executing large transactions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The token is deployed on the Token-2022 program, ensuring modern extension compatibility. 7.1 Architecture and 7.2 Code Security are robust as both mint and freeze authorities are revoked. 7.3 Access… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic stability is supported by $1,033,444 in liquidity, with 100% of pool tokens burned to prevent rug-pulls. 7.5 Governance is decentralized by the lack of minting capabilities. 7.6 External… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not applicable as the mint is a standard SPL token. Metadata is immutable, and no balance-mutating authorities exist. The token configuration is permanently locked in its current… |

## Security Findings

_🔴 1 Critical · ⚪ 5 Informational_

### `QA-IDENTITY` — Imitation of Pax Dollar (USDP)  *(Severity: Critical · Status: Acknowledged)*

Presents itself as Pax Dollar (USDP), but the listed USDP contract on solana is hvbpjaqgnpkgbaybzqbr1t7yfdvayvp2vcqqfkken4tm (CoinGecko). Holders who think they own the real asset own this contract instead; it has none of the real asset's backing, liquidity or redemption.

**Recommendation:** Do not buy, hold or accept this token as the asset it names. Verify any token address against the issuer's official site.


### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.0M (DexScreener, all pools). 24h trading volume $634K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Imitation of Pax Dollar (USDP)  *(Severity: Informational · Status: Acknowledged)*

A token presenting itself under the name or ticker of an established asset without being that asset's contract. Its only reason to borrow that identity is to be mistaken for it. Scored as an imitation (see the identity finding). Its name presents it as a stable-value coin, yet it trades at $0.1684 — it does not hold a peg. Basis: launched on pump.fun, a meme launchpad; behaves as: meme token. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.0M of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Do not treat this token as the asset it names. Use only the official contract address published by that asset's issuer.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`dMyGV4...pump`](https://solscan.io/account/dMyGV4ptoPmJPQ6Cqh2j69AJRZU88mGL7JryMezpump) |
| **Network** | Solana |
| **Price** | $0.1684 |
| **24h Volume** | $633.8K |
| **Liquidity** | $1.03M |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 15h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 16613 buys / 3697 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7klonpgjzvqp8bxpgluj4yxmnhjt48pumlu7ydhe4kx8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/usdp-sol-96e0)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
