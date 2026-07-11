---
token: Backpack
ticker: BP
network: solana
risk_score: 92
status: critical
date: 2026-06-14
---

# Backpack (BP) — Smart Contract Security Analysis | Solana

> **Risk Score: 92/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/backpack-sol)

---

## Audit Summary

The Backpack (BP) token mint presents critical centralization risks due to unrevoked mint and freeze authorities. The issuer retains the ability to mint unlimited new tokens and freeze any holder's funds. Additionally, new holder accounts are created in a frozen state by default, requiring explicit unfreezing. Holder concentration data was unavailable, preventing a full assessment of supply distribution risk.

> **Final Recommendation:** Users considering holding Backpack (BP) tokens should be aware of the significant centralized risks. The unrevoked mint and freeze authorities grant the issuer complete control over the token supply and the ability to freeze any holder's assets. It is strongly recommended to verify on-chain that these authorities are revoked before considering the token supply fixed or your holdings secure. Additionally, new accounts being frozen by default requires an active issuer to unfreeze them, which could lead to funds being inaccessible if the issuer becomes unresponsive.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 1/10 | High | The token is an SPL token using the `spl-token` program, with a total supply of 999,999,846.945724009 tokens and 9 decimals. Critical access controls remain active: the mint authority… |
| **Governance / Economics** | 1/10 | High | The token exhibits healthy liquidity with $1,942,306 USD available on DEXs and a 24-hour volume of $1,046,962 USD. The volume/liquidity ratio is 0.54, indicating normal trading patterns without signs… |
| **Upgrades** | 4/10 | Medium | The token's core authorities, including mint and freeze, are not revoked, meaning the issuer retains full control over token supply and holder accounts. The token uses the standard `spl-token`… |

## Security Findings

_🔴 2 Critical · 🟠 1 High_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is GySFHFS5ZiN4Z5YnyPZcjjxpYcGvD7qHZYVjE9QzMHVH. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `C-02` — Freeze Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The freeze authority is GySFHFS5ZiN4Z5YnyPZcjjxpYcGvD7qHZYVjE9QzMHVH. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds.

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `H-01` — Default Frozen State  *(Severity: High · Status: Unresolved)*

New holder accounts are created in a frozen state and require explicit unfreezing by an authority, as indicated by `GoPlus.default_account_state: 1`.

**Recommendation:** Confirm an active issuer is available to unfreeze accounts; otherwise the token is unspendable.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`BPxxfR...jPCy`](https://solscan.io/account/BPxxfRCXkUVhig4HS1Lh7kZqV6SPJhzfEk4x6fVBjPCy) |
| **Network** | Solana |
| **Price** | $0.3828 |
| **24h Volume** | $389.9K |
| **Liquidity** | $731.8K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 99.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1148 buys / 700 sells |

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

### Is Backpack a scam?

Backpack (BP) shows critical risk factors. The contract is unverified, lacking transparency for investors. A staggering 99.0% of supply is held by the top 10 wallets, indicating extreme centralization risk. Crucially, liquidity is not locked, posing a clear withdrawal risk. While ownership is renounced and new tokens cannot be minted, these combined factors contribute to its 'High Risk' assessment.

### Is Backpack safe to buy?

No, Backpack (BP) is not safe to buy, indicated by its High Risk score of 58/100. Core issues include its unverified contract, which lacks transparency for investors. A critical 99.0% of the supply is controlled by the top 10 holders, posing extreme centralization risk. Crucially, liquidity is not locked, meaning it can be withdrawn. These factors make it highly speculative and risky.

### Has Backpack been audited?

No, the Backpack (BP) contract is unverified. Its deployed code isn't publicly matched against source code. Therefore, an independent security audit cannot be publicly confirmed. This lack of transparency prevents investors from assessing the contract's safety, significantly contributing to its high-risk profile.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/6qz7thwqvcjf3hydglukalbuk6eyjkezxzmwlaeiwfjd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/backpack-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-14*
