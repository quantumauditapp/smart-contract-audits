---
token: 用过去的表情包回到牛市
ticker: MEMES
network: bsc
risk_score: 42
status: medium
date: 2026-11-02
---

# 用过去的表情包回到牛市 (MEMES) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 42/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/memes-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is an EIP-1167 minimal clone token. Ownership has been renounced on-chain, rendering all privileged administrative functions dormant. The contract logic is immutable and cannot be upgraded. No security vulnerabilities were identified in the provided code map.

> **Final Recommendation:** The contract is in a secure, immutable state with ownership renounced. No further action is required for the current deployment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes a standard EIP-1167 minimal clone pattern, ensuring gas-efficient deployment. 7.1 Architecture is robust due to the immutable nature of the clone. 7.2 Code Security is high… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance risks are non-existent because the owner cannot modify the pool state or tax parameters. The token operates as a trustless asset. 7.6 External dependencies are limited… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are impossible for this contract as it is a minimal clone. The implementation address is hardcoded into the proxy bytecode. 7.8 Operations are stable and require no further maintenance. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x5722…6512 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 56.4% of supply. What remains: 13.1% in wallets, 43.3% in other contracts. 335 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

335 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10K (DexScreener, all pools). 24h trading volume $665K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (meme). Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 0% on buy, 0.99% on sell. Market: $10K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4ab8...7777`](https://bscscan.com/address/0x4ab894934dbd185fcb28a07af55844535a1e7777) |
| **Network** | BNB Chain |
| **Price** | $0.00001167 |
| **24h Volume** | $553.4K |
| **Liquidity** | $10.3K |
| **Volume / Liquidity** | 53.8× |
| **Token Age** | 12h |
| **Top-10 Holders** | 56.4% of supply |
| **Buy / Sell Tax** | 0.0% / 1.0% |
| **24h Transactions** | 3674 buys / 3492 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x73849c9b7970c90c548c66640f365db1fc066134)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/memes-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
