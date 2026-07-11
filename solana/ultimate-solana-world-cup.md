---
token: Ultimate Solana World Cup
ticker: USWC
network: solana
risk_score: 57
status: high
date: 2026-06-15
---

# Ultimate Solana World Cup (USWC) — Smart Contract Security Analysis | Solana

> **Risk Score: 57/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ultimate-solana-world-cup-sol)

---

## Audit Summary

The Ultimate Solana World Cup (USWC) token mint is configured with revoked mint and freeze authorities, indicating a fixed supply and unfreezable accounts. However, the token suffers from very low DEX liquidity, currently at $5,192, which poses a significant risk for large trades. Holder distribution data was unavailable for analysis.

> **Final Recommendation:** Potential holders should exercise extreme caution due to the very low liquidity. Verify the current DEX liquidity immediately before any transaction, as it can fluctuate rapidly. Consider the impact of high slippage on any intended trade size. Monitor for any significant changes in liquidity or trading volume before committing substantial capital.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The Ultimate Solana World Cup (USWC) token is an SPL Token-2022 mint. Both the mint authority and freeze authority are revoked, meaning no new tokens can be minted and no accounts can be frozen.… |
| **Governance / Economics** | 3/10 | High | The token exhibits very low liquidity, with total DEX liquidity at only $5,192. This makes large trades highly susceptible to severe slippage and prevents significant positions from being exited… |
| **Upgrades** | 8/10 | Low | The token mint has a robust upgrade posture, with both the mint authority and freeze authority permanently revoked. This ensures that the token supply is fixed and no accounts can be frozen… |

## Security Findings

_🟠 1 High_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $5,192. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Verify current liquidity levels before any trade, as low liquidity can lead to significant price impact and make large positions difficult to exit.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`CqFJhm...pump`](https://solscan.io/account/CqFJhmzTVCdULq4KdfwKqsBf7ABaaZarWCrarazupump) |
| **Network** | Solana |
| **Price** | $0.00009856 |
| **24h Volume** | $48.8K |
| **Liquidity** | $31.6K |
| **Volume / Liquidity** | 1.5× |
| **Token Age** | 2d |
| **Top-10 Holders** | 33.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4829 buys / 4479 sells |

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

### Is Ultimate Solana World Cup a scam?

Based on available data, direct evidence for USWC being an outright scam is not definitive, especially with ownership renounced and no mint function. However, the lack of contract verification means its code is not public for review, and unlocked liquidity presents a significant risk of a rug pull, where funds could be withdrawn. These factors elevate the potential for adverse outcomes for investors.

### Is Ultimate Solana World Cup safe to buy?

USWC is currently rated with a High Risk score of 46/100. Key safety concerns include the contract not being verified, which prevents code inspection, and the liquidity not being locked, meaning funds can be withdrawn at any time. While developer control risks are reduced by ownership renunciation, these fundamental vulnerabilities suggest a high degree of risk for potential buyers.

### Has Ultimate Solana World Cup been audited?

Information regarding an official security audit for USWC is not provided. Crucially, the contract is also not verified on the blockchain explorer. This means its source code is not publicly published and accessible for review by anyone, including potential auditors or investors, making it impossible to independently assess the contract's security and functionality.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/f1bb4rjipymldps8inubdy4mrnvopu7jpvgh7ighe2r)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ultimate-solana-world-cup-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-15*
