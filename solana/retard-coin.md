---
token: Retard Coin
ticker: RETARD
network: solana
risk_score: 43
status: medium
date: 2026-06-16
---

# Retard Coin (RETARD) — Smart Contract Security Analysis | Solana

> **Risk Score: 43/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/retard-coin-sol)

---

## Audit Summary

This audit of the Retard Coin (RETARD) SPL Token Mint found no critical or high-severity issues based on the provided on-chain facts and deterministic rules. Key authorities such as mint and freeze are revoked, and no Token-2022 extensions like transfer hooks or permanent delegates are active. However, holder concentration data was unavailable, and RugCheck.xyz assigned an extremely low score of 1/100, indicating potential underlying risks not directly covered by the deterministic findings but warranting extreme caution.

> **Final Recommendation:** Based on the available on-chain data, the Retard Coin (RETARD) SPL token mint appears to have a robust technical setup with key authorities revoked and no active malicious Token-2022 extensions. However, the extremely low RugCheck score of 1/100 is a significant red flag that warrants extreme caution, despite not triggering a specific 'RUGGED' verdict. Investors should also note the unavailability of holder concentration data, which prevents a full assessment of potential market manipulation risks from large holders. It is strongly recommended to investigate the reasons behind the low RugCheck score and exercise extreme caution before interacting with this token. A Premium Deploy option is not applicable for existing SPL token mints.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The Retard Coin (RETARD) token is an SPL Token-2022 mint. Its core security posture is strong, with both the mint authority and freeze authority explicitly revoked, preventing further token issuance… |
| **Governance / Economics** | 5/10 | Medium | The token exhibits moderate liquidity with $54,938 USD available on DEXs, and a healthy 24-hour volume of $80,122 USD, resulting in a normal Volume/Liquidity ratio of 1.46. The DEX pair has been… |
| **Upgrades** | 8/10 | Low | The token's core parameters are immutable, as both mint and freeze authorities are revoked. The token utilizes the spl-token-2022 program, but no specific upgradable extensions like transfer hook or… |

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2q68mq...pump`](https://solscan.io/account/2q68mqEbjwmnMjs1o3KZDNZVyMv6RZKkHcm64iinpump) |
| **Network** | Solana |
| **Price** | $0.000125 |
| **24h Volume** | $35.6K |
| **Liquidity** | $26.5K |
| **Volume / Liquidity** | 1.3× |
| **Token Age** | 14d |
| **Top-10 Holders** | 34.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 367 buys / 313 sells |

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

### Is Retard Coin a scam?

Based on the available data, Retard Coin presents a mixed security picture rather than a definitive scam label. While ownership is renounced and no mint function exists, offering some security, the contract is unverified and its liquidity is not locked. These latter points introduce significant risks, including potential rug pulls or unidentifiable vulnerabilities. Investors should carefully evaluate these conflicting signals.

### Is Retard Coin safe to buy?

Retard Coin is assessed as 'Medium Risk' (36/100) and is not considered entirely safe due to several key factors. The contract's unverified status means its code cannot be publicly audited for security flaws. Crucially, the liquidity of $26,488 is not locked, posing a risk of removal by liquidity providers. Additionally, 34.0% of the supply is concentrated among the top 10 holders, raising concerns about potential market influence.

### Has Retard Coin been audited?

The provided information states that the Retard Coin contract is "unverified." This generally means its source code has not been published or matched on the blockchain explorer. Without verified code, a comprehensive third-party security audit is typically not feasible. Therefore, investors cannot rely on an independent audit to assess the contract's security or confirm its intended functionality.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/4fsjvbrpus55exor2mldbakhceusqxsyk5ndu62ntqme)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/retard-coin-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-16*
