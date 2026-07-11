---
token: Jupiter
ticker: JUP
network: solana
risk_score: 34
status: medium
date: 2026-06-21
---

# Jupiter (JUP) — Smart Contract Security Analysis | Solana

> **Risk Score: 34/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/jupiter-sol)

---

## Audit Summary

The Jupiter (JUP) token mint exhibits strong security configurations with both mint and freeze authorities revoked, ensuring a fixed supply and preventing account freezing. Liquidity is robust, and trading volume appears healthy. However, holder concentration data was unavailable, preventing a full assessment of distribution risk. A discrepancy exists regarding metadata mutability, with RugCheck flagging it as mutable while GoPlus reports it as immutable.

> **Final Recommendation:** Based on the available on-chain data and external signals, the Jupiter (JUP) token mint appears to be robustly configured with critical authorities revoked, ensuring a fixed supply and preventing arbitrary freezing of funds. Liquidity is high, and trading patterns are normal, suggesting a healthy market. However, the absence of holder concentration data means that potential risks associated with concentrated supply cannot be assessed. Investors should also note the conflicting information regarding metadata mutability from GoPlus and RugCheck. It is recommended to verify the metadata immutability on-chain if this is a critical concern, and to monitor holder distribution if such data becomes available. For enhanced security, consider utilizing a Premium Deploy option for future token launches to ensure comprehensive pre-deployment audits and continuous monitoring.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture & 7.2 Code Security: The token is an SPL token mint utilizing the standard `spl-token` program. Both the Mint Authority and Freeze Authority have been revoked (None), indicating that… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic: The token exhibits substantial liquidity with $167,376,320 USD available on DEXs. The 24-hour volume of $281,072,047 USD results in a healthy Volume/Liquidity Ratio of 1.68, which is… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades: The mint authority and freeze authority are both revoked, meaning the token's supply and account freezing capabilities cannot be altered post-launch. The token is not using Token-2022… |

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`JUPyiw...DvCN`](https://solscan.io/account/JUPyiwrYJFskUPiHa7hkeR8VUtAeFoSYbKedZNsDvCN) |
| **Network** | Solana |
| **Price** | $1,077.4400 |
| **24h Volume** | $249.87M |
| **Liquidity** | $88.97M |
| **Volume / Liquidity** | 2.8× |
| **Token Age** | 7mo |
| **Top-10 Holders** | 68.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 503 buys / 641 sells |

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
