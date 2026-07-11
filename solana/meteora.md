---
token: Meteora
ticker: MET
network: solana
risk_score: 46
status: high
date: 2026-06-21
---

# Meteora (MET) — Smart Contract Security Analysis | Solana

> **Risk Score: 46/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/meteora-sol)

---

## Audit Summary

The Meteora (MET) token has its mint and freeze authorities revoked, indicating a fixed supply and unfreezable accounts. However, new holder accounts are created in a frozen state, requiring an issuer to unfreeze them before transfers are possible. Holder concentration data was unavailable, and RugCheck provided a low score of 7/100.

> **Final Recommendation:** Holders should be aware that new token accounts for Meteora (MET) are created in a frozen state, requiring an explicit unfreeze operation by an authority. It is crucial to confirm the availability and responsiveness of the issuer to perform this action, as otherwise, newly received tokens may be unspendable. While mint and freeze authorities are revoked, the default frozen state introduces a significant operational dependency.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The Meteora (MET) token is an SPL token operating on the `spl-token` program. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and existing accounts |
| **Governance / Economics** | 4/10 | Medium | The token exhibits healthy economic indicators with a liquidity of $2,133,784 and a normal 24-hour volume/liquidity ratio of 0.19. The DEX pair has been active for 228 days, providing a reasonable tra |
| **Upgrades** | 8/10 | Low | The token's core parameters are largely immutable, with both mint and freeze authorities revoked. GoPlus indicates that metadata is not mutable (`GoPlus.metadata_mutable: False`), and transfer fee and |

## Security Findings

_🟠 1 High · ⚪ 2 Informational_

### `H-01` — Default Frozen State  *(Severity: High · Status: Unresolved)*

New holder accounts are created in a frozen state and require explicit unfreezing by an authority. (Fact: `GoPlus.default_account_state: 1`)

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
| **Contract** | [`METvsv...mWQL`](https://solscan.io/account/METvsvVRapdj9cFLzq4Tr43xK4tAjQfwX76z3n6mWQL) |
| **Network** | Solana |
| **Price** | $887.2900 |
| **24h Volume** | $178.5K |
| **Liquidity** | $332.61M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 68.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 273 buys / 261 sells |

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

### Is Meteora a scam?

Meteora carries a high-risk score of 56/100 based on available data. While ownership is renounced and no new tokens can be minted, significant concerns exist. The contract is unverified, meaning its code cannot be publicly scrutinized for vulnerabilities or hidden functions. Additionally, 68% of the supply is concentrated in the top 10 wallets, raising centralization risks. These factors warrant extreme caution.

### Is Meteora safe to buy?

Meteora is classified with a high-risk score of 56/100, suggesting it is not inherently safe to buy without significant due diligence. Key risk factors include an unverified contract, which prevents independent security audits, and highly centralized holdings, with 68.0% of the supply controlled by the top ten wallets. Additionally, the substantial liquidity, while impressive, is not locked, adding to potential vulnerabilities.

### Has Meteora been audited?

Based on the provided information, the Meteora contract is unverified. This means its source code has not been published and confirmed to match the deployed code on the blockchain. Without contract verification, a comprehensive security audit by independent third parties is practically impossible to conduct or validate, significantly increasing the uncertainty regarding its integrity.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/huprxabcjqyrhj6scpqxua6qqjss2ia1txmeeuvwphog)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/meteora-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-21*
