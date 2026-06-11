---
token: RECON RACCOON
ticker: RCON
network: solana
risk_score: 72
status: critical
date: 2026-06-10
---

# RECON RACCOON (RCON) — Smart Contract Security Analysis | Solana

> **Risk Score: 72/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/recon-raccoon-sol)

---

## Audit Summary

The RECON RACCOON (RCON) token presents a significant operational risk due to its default frozen account state, meaning new holders cannot transfer tokens without an issuer's intervention. While core mint and freeze authorities are revoked, the lack of holder concentration data and a 'High holder correlation' flag from RugCheck.xyz suggest potential market manipulation risks. Information on holder distribution was unavailable, limiting a complete assessment of supply centralization.

> **Final Recommendation:** Prospective holders should exercise caution due to the 'Default Frozen State' of new accounts. It is critical to confirm the availability and responsiveness of an issuer or authority capable of unfreezing accounts before acquiring this token, as otherwise, newly received tokens may be unspendable. Additionally, while core authorities are revoked, the 'High holder correlation' flagged by RugCheck.xyz warrants further investigation into the token's distribution and potential for large-scale sell-offs. For a premium deployment, consider a token design where default account states are unfrozen, or where unfreezing is decentralized.

## Security Analysis

The RECON RACCOON (RCON) token presents a significant operational risk due to its default frozen account state, meaning new holders cannot transfer tokens without an issuer's intervention. While core mint and freeze authorities are revoked, the lack of holder concentration data and a 'High holder correlation' flag from RugCheck.xyz suggest potential market manipulation risks. Information on holder distribution was unavailable, limiting a complete assessment of supply centralization.

Prospective holders should exercise caution due to the 'Default Frozen State' of new accounts. It is critical to confirm the availability and responsiveness of an issuer or authority capable of unfreezing accounts before acquiring this token, as otherwise, newly received tokens may be unspendable. Additionally, while core authorities are revoked, the 'High holder correlation' flagged by RugCheck.xyz warrants further investigation into the token's distribution and potential for large-scale sell-offs. For a premium deployment, consider a token design where default account states are unfrozen, or where unfreezing is decentralized.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | The RECON RACCOON (RCON) token is implemented using the standard `spl-token` program on Solana. Key administrative authorities, including the Mint Authority and Freeze Authority, have been successfull |
| **Governance / Economics** | 7/10 | Medium | The token exhibits moderate liquidity with $50,129 USD available on DEXs, and a healthy 24-hour volume to liquidity ratio of 0.00, suggesting organic trading activity rather than wash trading. The DEX |
| **Upgrades** | 9/10 | Low | The RECON RACCOON (RCON) token mint has a robust immutability profile regarding its core administrative functions. Both the Mint Authority and Freeze Authority have been permanently revoked, ensuring  |

## Security Findings

_🟠 1 High · ⚪ 2 Informational_

### `H-01` — Default Frozen State  *(Severity: High · Status: Unresolved)*

New holder accounts are created in a frozen state (`GoPlus.default_account_state: 1`) and require explicit unfreezing by an authority. This means that any new recipient of the token will not be able to transfer their tokens until an authorized party unfreezes their account.

**Recommendation:** Confirm an active issuer is available to unfreeze accounts; otherwise the token is unspendable.


### `I-02` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.


### `I-03` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7nZuYZ...bonk`](https://solscan.io/account/7nZuYZYZnof9gF3zr9QhdnxpQ1mTM8LN3VaJuhrGbonk) |
| **Network** | Solana |
| **Price** | $0.002601 |
| **24h Volume** | $121.1K |
| **Liquidity** | $141.8K |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 8mo |
| **Top-10 Holders** | 51.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/gcxnezvgsn3sj753ak6mcca43gsjlmnvfhyqva2bsf4k)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/recon-raccoon-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
