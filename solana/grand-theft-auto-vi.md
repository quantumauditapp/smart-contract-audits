---
token: Grand Theft Auto VI
ticker: GTAVI
network: solana
risk_score: 35
status: medium
date: 2026-06-23
---

# Grand Theft Auto VI (GTAVI) — Smart Contract Security Analysis | Solana

> **Risk Score: 35/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/grand-theft-auto-vi-sol)

---

## Audit Summary

This audit of the Grand Theft Auto VI (GTAVI) SPL token mint found no critical or high-severity issues based on the provided on-chain facts and deterministic rules. Key authorities like mint and freeze have been revoked, and no malicious Token-2022 extensions are active. Holder concentration data was unavailable, preventing a full assessment of distribution risk.

> **Final Recommendation:** Based on the available data, the Grand Theft Auto VI (GTAVI) token appears to be well-configured from a security perspective, with critical authorities revoked and no active malicious Token-2022 extensions. Holders should be aware that holder concentration data was not available, so the distribution risk could not be assessed. For a comprehensive understanding, it is recommended to monitor on-chain holder distribution once data becomes available. Consider using a premium deployment option for future tokens to ensure all relevant on-chain data points are captured and analyzed from launch.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture, 7.2 Code Security, 7.3 Access Control, 7.8 Operations: The token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic, 7.5 Governance: DEX liquidity for the token is $65,402, which is moderate. The 24-hour trading volume is $111,523, resulting in a Volume/Liquidity Ratio of 1.71, which is considered… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades: The mint authority and freeze authority have both been revoked, meaning the token's core parameters related to supply and account freezing cannot be altered. The token uses the… |

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`EpVHyK...pump`](https://solscan.io/account/EpVHyKK8oxcLmp2C2NhAos1oDxgBNriw3wSLSozYpump) |
| **Network** | Solana |
| **Price** | $0.001407 |
| **24h Volume** | $821.2K |
| **Liquidity** | $112.0K |
| **Volume / Liquidity** | 7.3× |
| **Token Age** | 4d |
| **Top-10 Holders** | 23.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6532 buys / 4928 sells |

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

### Is Grand Theft Auto VI a scam?

Defining a token as an outright 'scam' requires specific evidence of malicious intent. However, GTAVI exhibits several characteristics often seen in projects with high risk. The unverified contract, unlocked liquidity, and concentrated holder base are significant red flags. While ownership is renounced and no mint function exists, these positive aspects do not fully mitigate the severe transparency and potential liquidity withdrawal risks. Exercise extreme caution.

### Is Grand Theft Auto VI safe to buy?

Based on the available data, GTAVI is not considered safe to buy, carrying a high-risk score of 46/100. Key risks include an unverified contract, preventing code review, and unlocked liquidity, which exposes funds to potential removal. Furthermore, the significant concentration of tokens among the top holders introduces market manipulation concerns. While ownership renunciation and no mint function are positive, they do not outweigh these critical vulnerabilities that signal potential for substantial loss.

### Has Grand Theft Auto VI been audited?

There is no indication that Grand Theft Auto VI has undergone a formal security audit by an independent firm. Crucially, the contract itself is not verified, meaning its code is not publicly accessible or confirmed to match deployed bytecode. This lack of transparency is a fundamental barrier to any effective audit or even basic community code review, making it impossible to assess its security directly.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/3jtcvdjp9cszn9mjgxwlw37m48aubsry5es6wfcznqlm)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/grand-theft-auto-vi-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-23*
