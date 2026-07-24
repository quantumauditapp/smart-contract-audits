---
token: Jupiter
ticker: JUP
network: solana
risk_score: 54
status: high
date: 2026-06-21
---

# Jupiter (JUP) — Smart Contract Security Analysis | Solana

> **Risk Score: 54/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/jupiter-sol)

---

## Audit Summary

This audit of the Jupiter (JUP) SPL token mint identifies a low-severity risk related to mutable metadata, meaning the token's name, symbol, or image can be altered post-launch. Key authorities like mint and freeze are appropriately revoked, indicating a fixed supply and unfreezable accounts. Holder distribution data was unavailable, preventing an assessment of concentration risk.

> **Final Recommendation:** Holders should verify the token's metadata against official sources to ensure branding consistency, especially given its mutability. Monitor for any changes to the token's name, symbol, or image that could indicate a change in project identity or intent. While key authorities are revoked, the absence of holder distribution data means investors should be aware of potential concentration risks that could impact price stability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The Jupiter (JUP) token operates on the standard `spl-token` program (v3). Both the Mint Authority and Freeze Authority are revoked, ensuring no new tokens can be minted and no existing accounts can… |
| **Governance / Economics** | 1/10 | High | The token exhibits strong market health with over $216 million in DEX liquidity and $82 million in 24-hour trading volume. The Volume/Liquidity Ratio of 0.38 is normal, not indicating wash trading.… |
| **Upgrades** | 5/10 | Medium | The token's core functionalities are immutable, as both the mint and freeze authorities have been revoked. There are no indications of upgradable transfer fees or transfer hooks. The only mutable… |

## Security Findings

_🟢 1 Low_

### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

The token's metadata is mutable, meaning its name, symbol, or image can be changed post-launch. This was identified by the `metadata_mutable: True` flag.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding. Monitor for any changes to the token's branding elements.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`JUPyiw...DvCN`](https://solscan.io/account/JUPyiwrYJFskUPiHa7hkeR8VUtAeFoSYbKedZNsDvCN) |
| **Network** | Solana |
| **Price** | $0.1939 |
| **24h Volume** | $577.9K |
| **Liquidity** | $1.09M |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 7mo |
| **Top-10 Holders** | 66.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 503 buys / 641 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is Jupiter a scam?

Characterizing Jupiter (JUP) as a "scam" requires direct evidence of malicious intent, which isn't provided by the data alone. However, significant red flags exist, including an unverified contract and high token centralization (top 10 holders owning 68.3% of supply). While ownership is renounced and no mint function exists, these risks contribute to its 58/100 "High Risk" score, indicating serious concerns.

### Is Jupiter safe to buy?

Investing in Jupiter (JUP) carries notable risks, making it difficult to deem "safe" based on current data. The primary concerns include the unverified contract, which prevents public code scrutiny, and the lack of locked liquidity, raising potential rug pull scenarios. Furthermore, 68.3% of the supply is held by the top 10 wallets, indicating significant centralization risk. These factors contribute to its "High Risk" classification.

### Has Jupiter been audited?

The provided data indicates the Jupiter (JUP) contract is "not verified." This means its code has not been publicly published on the blockchain explorer. Without verification, an independent audit of the contract's logic for security vulnerabilities or unintended functions is extremely difficult, if not impossible, for external parties. This lack of transparency is a significant risk.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/3xngdc58axytrj64stqz5trdqwvtwhlr888irbbwznee)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/jupiter-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-21*
