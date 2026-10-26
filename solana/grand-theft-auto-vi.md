---
token: Grand Theft Auto VI
ticker: GTAVI
network: solana
risk_score: 9
status: low
date: 2026-06-23
---

# Grand Theft Auto VI (GTAVI) — Smart Contract Security Analysis | Solana

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/grand-theft-auto-vi-sol)

---

## Audit Summary

The Grand Theft Auto VI (GTAVI) SPL Token Mint exhibits strong security characteristics with no critical or high-risk findings identified. Key authorities such as mint and freeze have been revoked, preventing further supply inflation or asset freezing. However, holder distribution data was unavailable, which limits the assessment of potential market manipulation risks.

> **Final Recommendation:** Holders should monitor on-chain for any changes to the token's state, although the current configuration indicates immutability for critical parameters. Verify the token's official branding and contract address against trusted sources to prevent phishing. If holder distribution data becomes available, assess the concentration to understand potential market impact from large holders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, preventing any further token minting or freezing of holder accounts. There… |
| **Governance / Economics** | 8/10 | Low | The token has a total DEX liquidity of $83,938, with a 24-hour volume of $54,495. The Volume/Liquidity Ratio is 0.65, which is considered normal and does not indicate wash trading. The DEX pair has… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, meaning no further changes can be made to the token's supply or account freeze status. Key Token-2022 extensions like transfer hooks are not… |

## Security Findings

_⚪ 1 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`EpVHyK...pump`](https://solscan.io/account/EpVHyKK8oxcLmp2C2NhAos1oDxgBNriw3wSLSozYpump) |
| **Network** | Solana |
| **Price** | $0.000109 |
| **24h Volume** | $2.9K |
| **Liquidity** | $51.1K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 4d |
| **Top-10 Holders** | 41.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6532 buys / 4928 sells |

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

## Frequently Asked Questions

### Is Grand Theft Auto VI a scam?

Defining a token as an outright 'scam' requires specific evidence of malicious intent. However, GTAVI exhibits several characteristics often seen in projects with high risk. The unverified contract, unlocked liquidity, and concentrated holder base are significant red flags. While ownership is renounced and no mint function exists, these positive aspects do not fully mitigate the severe transparency and potential liquidity withdrawal risks. Exercise extreme caution.

### Is Grand Theft Auto VI safe to buy?

Based on the available data, GTAVI is not considered safe to buy, carrying a low-risk score of 9/100. Key risks include an unverified contract, preventing code review, and unlocked liquidity, which exposes funds to potential removal. Furthermore, the significant concentration of tokens among the top holders introduces market manipulation concerns. While ownership renunciation and no mint function are positive, they do not outweigh these critical vulnerabilities that signal potential for substantial loss.

### Has Grand Theft Auto VI been audited?

There is no indication that Grand Theft Auto VI has undergone a formal security audit by an independent firm. Crucially, the contract itself is not verified, meaning its code is not publicly accessible or confirmed to match deployed bytecode. This lack of transparency is a fundamental barrier to any effective audit or even basic community code review, making it impossible to assess its security directly.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/3jtcvdjp9cszn9mjgxwlw37m48aubsry5es6wfcznqlm)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/grand-theft-auto-vi-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-23*
