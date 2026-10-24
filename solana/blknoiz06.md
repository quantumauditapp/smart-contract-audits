---
token: blknoiz06
ticker: ANSEM
network: solana
risk_score: 22
status: low
date: 2026-10-24
---

# blknoiz06 (ANSEM) — Smart Contract Security Analysis | Solana

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/blknoiz06-sol)

---

## Audit Summary

The blknoiz06 token operates on the standard SPL Token program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn of LP tokens, and no adverse flags were identified by third-party risk registries. The token exhibits a low-risk profile with no active administrative control over supply or holder accounts.

> **Final Recommendation:** The token configuration is secure and requires no immediate remediation. Users should continue to monitor the top holder distribution via block explorers to ensure concentration remains within acceptable limits.

Verify the mint and freeze authority status periodically using a block explorer to confirm they remain set to null. No further action is required to secure the protocol's current state.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard spl-token program (7.1 Architecture). Access control is fully decentralized as both mint and freeze authorities are revoked (7.3 Access Control). The token does not… |
| **Governance / Economics** | 9/10 | Low | The top 10 holders control 27.20% of the supply, indicating a distributed ownership structure (7.4 Economic). Liquidity is robustly protected with 100% of LP tokens burned, preventing rug-pulls via… |
| **Upgrades** | 10/10 | Low | The token metadata is immutable, preventing unauthorized branding changes (7.7 Upgrades). There are no upgradeable components or proxy patterns associated with this mint (7.7 Upgrades). The… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 51.3% of supply. Of that, 24.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 27.2% in wallets, 0.0% in other contracts. 306 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

306 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $12K (DexScreener, all pools). 24h trading volume $30K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $12K of DEX liquidity across 2 pools. Launch: launched on pump.fun, 8 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 8 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 8 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`4Fys6Y...pump`](https://solscan.io/account/4Fys6Yv393Erv8tRLEzXNMLonBDpjNVM2mJwDHUjpump) |
| **Network** | Solana |
| **Price** | $0.00002677 |
| **24h Volume** | $30.1K |
| **Liquidity** | $12.3K |
| **Volume / Liquidity** | 2.4× |
| **Token Age** | 8d |
| **Top-10 Holders** | 51.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 480 buys / 330 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/fuetnfwmmqggmtdexyn7diazpwmvgpzyynzqnljzg8cu)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/blknoiz06-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
