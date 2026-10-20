---
token: T-OpenAI
ticker: TOPENAI
network: solana
risk_score: 99
status: critical
date: 2026-09-27
---

# T-OpenAI (TOPENAI) — Smart Contract Security Analysis | Solana

> **Risk Score: 99/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/t-openai-sol)

---

## Audit Summary

This SPL Token Mint exhibits critical security risks due to the active Mint Authority and Freeze Authority, allowing for unlimited token minting and account freezing, respectively. Additionally, a significant portion of the token supply is concentrated among the top 10 holders. Third-party registry data on holder distribution was unavailable, but external signals indicate high concentration. The token also features mutable metadata.

> **Final Recommendation:** Prospective holders should verify on-chain that the mint authority has been permanently revoked (set to null) to ensure a fixed token supply. Similarly, confirm the freeze authority is revoked to prevent account freezing and potential fund confiscation. Before relying on the token's branding, independently verify its current metadata against official sources, as it can be changed. Be aware of the 0.20% transfer fee and the holder concentration when considering large positions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The T-OpenAI token is implemented using the spl-token-2022 program. It has an active Mint Authority at EXvTtxurWBUNNCtLojaN8ZBJFNJPZFSH3szoih9hh7YW, which can create new tokens at will. A Freeze… |
| **Governance / Economics** | 1/10 | High | The token exhibits a significant holder concentration, with the top 10 token accounts holding 61.44% of the total supply. This concentration poses a risk of price volatility from large sell-offs. The… |
| **Upgrades** | 1/10 | High | The Mint Authority (EXvTtxurWBUNNCtLojaN8ZBJFNJPZFSH3szoih9hh7YW) and Freeze Authority (7n2PNcDXVDMK2m8dyV9cVPNY7p4jM4ZMHv7TzfibEt8o) remain active, allowing for potential changes to token supply and… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Transfer Fee** | ⚠️ 0.2% · upgradeable |

## Security Findings

_🔴 2 Critical · 🟡 1 Medium · 🟢 1 Low_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is EXvTtxurWBUNNCtLojaN8ZBJFNJPZFSH3szoih9hh7YW. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value. (Fact: Mint Authority: EXvTtxurWBUNNCtLojaN8ZBJFNJPZFSH3szoih9hh7YW)

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `C-02` — Freeze Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The freeze authority is 7n2PNcDXVDMK2m8dyV9cVPNY7p4jM4ZMHv7TzfibEt8o. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds. (Fact: Freeze Authority: 7n2PNcDXVDMK2m8dyV9cVPNY7p4jM4ZMHv7TzfibEt8o)

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `M-01` — Holder Concentration > 50%  *(Severity: Medium · Status: Unresolved)*

Top 10 token accounts hold 61.44% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range. (Fact: top10_holders_pct: 61.44)

**Recommendation:** Be aware of the significant holder concentration and its potential impact on price stability and liquidity.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch. (Fact: metadata_mutable: True)

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`oPAiAi...kjTZ`](https://solscan.io/account/oPAiAikWTaFj9RYoRFD35ccfwhnMcB3ThgBZRHSkjTZ) |
| **Network** | Solana |
| **Price** | $1,189.1000 |
| **24h Volume** | $5.01M |
| **Liquidity** | $628.3K |
| **Volume / Liquidity** | 8.0× |
| **Token Age** | 3mo |
| **Top-10 Holders** | 61.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 24146 buys / 37118 sells |

## Security Flags (2/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/2zwxt3niyjyudmdmdvar9ajne42rkwydzzbh6timukqy)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/t-openai-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-27*
