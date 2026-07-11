---
token: three.ws
ticker: THREE
network: solana
risk_score: 22
status: medium
date: 2026-06-10
---

# three.ws (THREE) — Smart Contract Security Analysis | Solana

> **Risk Score: 22/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/threews-sol)

---

## Audit Summary

The three.ws (three) SPL Token Mint on Solana exhibits a robust security posture with all critical authorities, including Mint and Freeze authorities, being revoked. This ensures a fixed supply and prevents arbitrary freezing of user funds. Holder concentration data was unavailable, preventing a full assessment of distribution risk.

> **Final Recommendation:** Based on the available on-chain facts and external security signals, the three.ws (three) SPL Token Mint appears to be well-configured with critical authorities revoked, indicating a fixed supply and no ability to freeze user funds. The token's metadata is also immutable.
However, holder concentration data was unavailable, which is a key metric for assessing potential market manipulation risks from large holders. Users should consider this information gap when evaluating the token. For a Premium Deploy, further off-chain due diligence on the project team and community engagement is recommended.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The token is implemented using the spl-token-2022 program. Both the Mint Authority and Freeze Authority are revoked (None), indicating a fixed supply and preventing the issuer from freezing user accou |
| **Governance / Economics** | 7/10 | Low | The token has a healthy liquidity of $258,109 USD on DEXs. The 24-hour volume of $1,266,452 USD results in a Volume/Liquidity Ratio of 4.91, which is considered normal and does not suggest wash tradin |
| **Upgrades** | 8/10 | Low | The Mint Authority and Freeze Authority are both revoked, ensuring that the core parameters of the token (supply and transferability) cannot be altered post-launch. The token uses the spl-token-2022 p |

## Security Findings

_⚪ 3 Informational_

### `I-01` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.


### `I-02` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.


### `I-03` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`FeMbDo...pump`](https://solscan.io/account/FeMbDoX7R1Psc4GEcvJdsbNbZA3bfztcyDCatJVJpump) |
| **Network** | Solana |
| **Price** | $0.004757 |
| **24h Volume** | $1.46M |
| **Liquidity** | $266.3K |
| **Volume / Liquidity** | 5.5× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 18.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 32461 buys / 17505 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is three.ws a scam?

Based on automated analysis, three.ws scores 65/100 (High Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is three.ws safe to buy?

Our scanner flagged a risk score of 65/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has three.ws been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/5byl7mzolabynwmpzkpkjf4mgkz7febzranos19pre2z)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/threews-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
