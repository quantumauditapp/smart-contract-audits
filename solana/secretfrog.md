---
token: ?
ticker: SECRETFROG
network: solana
risk_score: 38
status: medium
date: 2026-10-12
---

# ? (SECRETFROG) — Smart Contract Security Analysis | Solana

> **Risk Score: 38/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/secretfrog-sol)

---

## Audit Summary

The SECRETFROG SPL Token Mint demonstrates a strong security foundation with both mint and freeze authorities revoked, and all pool liquidity locked, mitigating common rug pull risks. However, the token's metadata remains mutable, allowing for potential changes to its name, symbol, or image post-launch. Holder distribution data was unavailable for analysis, preventing a full assessment of concentration risk.

> **Final Recommendation:** Holders should monitor the token's metadata for any unexpected changes to its branding, such as name or symbol. While liquidity is locked, new holders should verify the continued locking status of the liquidity pool through on-chain explorers. Due to unavailable holder distribution data, investors should exercise caution regarding potential concentration risks that could not be assessed.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The SECRETFROG token operates on the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, ensuring that no new tokens can be minted and no holder accounts can be… |
| **Governance / Economics** | 8/10 | Low | The token's DEX liquidity stands at $104,217. A significant positive is that 100.0% of the pool's liquidity is locked for good in Raydium's LP locker, preventing any single entity from withdrawing… |
| **Upgrades** | 8/10 | Low | The revocation of mint and freeze authorities indicates a fixed supply and unfreezable accounts, enhancing trust in token stability. While the transfer hook is not upgradable, the transfer fee is… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Transfer Fee** | ⚠️ 3.0% · upgradeable |

## Security Findings

_🟢 1 Low · ⚪ 6 Informational_

### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch, as indicated by `metadata_mutable: True`.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity. This assessment covers the main pool, which holds 89% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $115K (DexScreener, all pools). 24h trading volume $934K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the buy/sell tax; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (frog). Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $115K of DEX liquidity across 3 pools. Launch: 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`85Mo19...aQcg`](https://solscan.io/account/85Mo19cmRzg89Vz1niSw7jRZtrtfvCrkEwFSW1CBaQcg) |
| **Network** | Solana |
| **Price** | $0.0008531 |
| **24h Volume** | $880.0K |
| **Liquidity** | $102.6K |
| **Volume / Liquidity** | 8.6× |
| **Token Age** | 2d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5938 buys / 5792 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7dwwlrscrgkuhtebnzm6rlvekvs2uft3sz8ebj4xlumy)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/secretfrog-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-12*
