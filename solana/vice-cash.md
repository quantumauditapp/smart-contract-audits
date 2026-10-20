---
token: Vice Cash
ticker: VICE
network: solana
risk_score: 16
status: low
date: 2026-10-16
---

# Vice Cash (VICE) — Smart Contract Security Analysis | Solana

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/vice-cash-sol)

---

## Audit Summary

The Vice Cash (VICE) SPL Token Mint exhibits a low-risk profile based on available on-chain data and third-party security signals. Key authorities such as Mint Authority and Freeze Authority are revoked, preventing further token issuance or freezing of accounts. Liquidity for the token is fully burned or locked, and holder concentration is low. Third-party risk registries report no adverse flags, and no critical or high-severity issues were identified.

> **Final Recommendation:** Holders should verify on-chain that the Mint Authority and Freeze Authority remain revoked to ensure the supply is fixed and accounts cannot be frozen. Monitor DEX liquidity and trading volume for any significant changes, especially given the token's recent creation. While current signals are positive, continuous vigilance is recommended for new tokens.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented using the spl-token-2022 program. The Mint Authority and Freeze Authority are both revoked, ensuring no new tokens can be minted and no holder accounts can be frozen. No… |
| **Governance / Economics** | 9/10 | Low | Holder concentration is very low, with the top 10 holders that can sell holding only 3.66% of the supply, indicating a decentralized distribution. The token has moderate liquidity at $45,991 USD… |
| **Upgrades** | 10/10 | Low | The Mint Authority and Freeze Authority are permanently revoked, preventing any future changes to the token's supply or account freeze status. Metadata, transfer fees, and transfer hooks are not… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 96.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.0% in wallets, 3.7% in other contracts. 2 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $46K (DexScreener, all pools). 24h trading volume $150K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $46K of DEX liquidity across 3 pools. Launch: launched on pump.fun, 57 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2uwxxi...pump`](https://solscan.io/account/2uwxxiD1PshoPrrSoNvttRD8Aa1nwxVDTFf4JK36pump) |
| **Network** | Solana |
| **Price** | $0.0002316 |
| **24h Volume** | $113.0K |
| **Liquidity** | $46.0K |
| **Volume / Liquidity** | 2.5× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 638 buys / 607 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/52buwqk5uggkmvobhjfxrk5ywzfcbtthrpxz4o13dpx3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/vice-cash-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-16*
