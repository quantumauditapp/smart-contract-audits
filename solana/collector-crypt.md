---
token: Collector Crypt
ticker: CARDS
network: solana
risk_score: 63
status: high
date: 2026-06-10
---

# Collector Crypt (CARDS) — Smart Contract Security Analysis | Solana

> **Risk Score: 63/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/collector-crypt-sol)

---

## Audit Summary

The Collector Crypt (CARDS) token mint exhibits a low overall risk profile. The mint and freeze authorities have been revoked, indicating a fixed supply and unfreezable accounts. However, the token's metadata is mutable, allowing for potential changes to its name, symbol, or image post-launch. Holder concentration data was unavailable from chain-native RPC, though a third-party risk registry flagged high ownership concentration.

> **Final Recommendation:** Before engaging with the Collector Crypt (CARDS) token, verify the current token metadata (name, symbol, image) on-chain to ensure it aligns with expectations, as this information can be changed. Monitor the token's holder distribution if data becomes available, especially given the third-party registry's signals of high ownership concentration. Confirm that the mint and freeze authorities remain revoked to ensure supply stability and unfreezable accounts.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The Collector Crypt (CARDS) token is implemented using the classic spl-token program. Both the mint authority and freeze authority have been revoked (None), ensuring that no new tokens can be minted… |
| **Governance / Economics** | 1/10 | High | The token has substantial liquidity with $2,673,056 USD, and its 24-hour volume of $1,288,101 USD results in a normal Volume/Liquidity Ratio of 0.48, suggesting organic trading activity. The DEX pair… |
| **Upgrades** | 5/10 | Medium | The mint authority and freeze authority are both revoked, meaning the core parameters of token supply and account freezing cannot be altered. The token does not utilize Token-2022 extensions that… |

## Security Findings

_🟢 1 Low_

### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

The token's metadata is mutable (metadata_mutable: True), meaning its name, symbol, or image can be changed post-launch. This introduces a risk of misrepresentation if the metadata is altered without notice.

**Recommendation:** Verify the token's metadata against off-chain expectations before trusting its branding. Regularly check on-chain metadata for any unexpected changes.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`CARDSc...xYjp`](https://solscan.io/account/CARDSccUMFKoPRZxt5vt3ksUbxEFEcnZ3H2pd3dKxYjp) |
| **Network** | Solana |
| **Price** | $0.1361 |
| **24h Volume** | $743.3K |
| **Liquidity** | $2.29M |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 9mo |
| **Top-10 Holders** | 83.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4104 buys / 4101 sells |

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

### Is Collector Crypt a scam?

Based on the available data, Collector Crypt (CARDS) exhibits several high-risk characteristics, including an unverified contract, unrenounced ownership, and unlocked liquidity. While these factors do not definitively label it a scam, they are commonly associated with projects that pose significant risks to investors. The overall risk score is 63/100 (High Risk).

### Is Collector Crypt safe to buy?

Collector Crypt (CARDS) carries a high-risk score of 63/100. Key safety concerns include the contract not being verified, ownership not being renounced, and liquidity not being locked. These elements introduce considerable risk, such as the potential for contract manipulation or liquidity removal. Investors should exercise extreme caution and conduct thorough due diligence.

### Has Collector Crypt been audited?

The provided data indicates that Collector Crypt's (CARDS) contract is not verified. An audit typically requires public access to the contract's code for security experts to review. Without a verified contract, independent security audits are impossible, leaving potential vulnerabilities unexamined and making it difficult to assess the code's integrity or safety.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/hnhpjpjgbg2kwnimtnw8cvbhvk1hfog3rc3kjnyc23td)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/collector-crypt-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
