---
token: MEEP CAT
ticker: MEEP
network: solana
risk_score: 34
status: medium
date: 2026-06-19
---

# MEEP CAT (MEEP) — Smart Contract Security Analysis | Solana

> **Risk Score: 34/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/meep-cat-sol)

---

## Audit Summary

This audit of the MEEP CAT (MEEP) SPL Token Mint found no critical or high-severity issues based on the provided deterministic rules. The mint authority and freeze authority are both revoked, indicating a fixed supply and immutability of account states. Liquidity is moderate at $22,477 USD, and trading volume is normal relative to liquidity. Holder concentration data was unavailable, though RugCheck.xyz flagged 'Single holder ownership'.

> **Final Recommendation:** Based on the available on-chain data and external security signals, the MEEP CAT token mint appears to have a low technical risk profile due to the revocation of critical authorities. However, potential holders should be aware that holder concentration data was unavailable, and RugCheck.xyz flagged 'Single holder ownership', which could imply significant market manipulation risk. Always conduct independent due diligence on the project's team and community before making investment decisions. For enhanced security, consider using a Premium Deploy option for any token interactions, which can provide additional transaction simulation and protection against common on-chain exploits.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The MEEP CAT token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no existing token accounts… |
| **Governance / Economics** | 7/10 | Low | The token exhibits moderate liquidity with $22,477 USD available on DEXs, and a 24-hour volume of $19,171 USD, resulting in a normal Volume/Liquidity Ratio of 0.85. The DEX pair has been active for… |
| **Upgrades** | 8/10 | Low | The mint authority and freeze authority for the MEEP CAT token have been revoked, preventing any further changes to the token's supply or the ability to freeze accounts. The token utilizes the… |

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8jvtfe...pump`](https://solscan.io/account/8jvtfeVTJQsrQ3L4kjQmRcXJ1iSFQMmkjkCqPUe3pump) |
| **Network** | Solana |
| **Price** | $0.0004162 |
| **24h Volume** | $729.7K |
| **Liquidity** | $56.8K |
| **Volume / Liquidity** | 12.9× |
| **Token Age** | 5mo |
| **Top-10 Holders** | 25.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5604 buys / 4916 sells |

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

### Is MEEP CAT a scam?

Based on the provided data, there isn't definitive proof to label MEEP CAT as a scam, but significant risks exist. The ownership being renounced and no mint function present are positive signals, preventing certain common scam tactics like malicious contract changes or endless token creation. However, the unverified contract and unlocked liquidity introduce considerable potential for misuse or instability, indicating a need for extreme caution.

### Is MEEP CAT safe to buy?

MEEP CAT carries notable risks that investors should be aware of. The contract is unverified, meaning its code hasn't been publicly scrutinized for vulnerabilities or hidden functions. Furthermore, the liquidity is not locked, exposing investors to the risk of a liquidity withdrawal or rug pull. While ownership is renounced, these fundamental security gaps mean it is not inherently "safe" and requires careful consideration of its medium risk profile.

### Has MEEP CAT been audited?

The provided data indicates that the MEEP CAT contract is *not* verified. This means its code is not publicly available for review, which is a prerequisite for a credible security audit. Without a verified contract, conducting a comprehensive and trustworthy audit is extremely challenging, making it impossible to confirm its security posture through this method.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/cgvkakbhnm93ul9tddwnfeyjt7d7qztctsyvkznevuem)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/meep-cat-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-19*
