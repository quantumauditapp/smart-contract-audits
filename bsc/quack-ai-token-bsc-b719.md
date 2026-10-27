---
token: Quack AI Token
ticker: Q
network: bsc
risk_score: 97
status: critical
date: 2026-10-27
---

# Quack AI Token (Q) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 97/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/quack-ai-token-bsc-b719)

---

## Audit Summary

The contract at the provided address is not verified on the block explorer, rendering the source code inaccessible for security analysis. As a result, it is impossible to verify the presence of backdoors, minting functions, or tax mechanisms. Investors should exercise extreme caution as the contract's behavior is opaque.

> **Final Recommendation:** Do not interact with this contract until the source code is verified on the block explorer and audited by a reputable third party. The lack of transparency is a primary indicator of potential rug-pull risk or malicious intent.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The technical architecture cannot be assessed due to the lack of verified source code. 7.1 Architecture, 7.2 Code Security, 7.3 Access Control, 7.6 External interactions, and 7.8 Operations are all… |
| **Governance / Economics** | 1/10 | High | Ownership is currently held by an EOA (0x34f0...), which presents a significant centralization risk. 7.4 Economic and 7.5 Governance parameters are opaque, meaning the owner could potentially modify… |
| **Upgrades** | 4/10 | Medium | The contract is not identified as a proxy, but 7.7 Upgrades cannot be verified. If the contract is a hidden proxy, the implementation could be swapped at any time. Without source code, the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 2 Critical · 🟠 1 High · 🟡 2 Medium · ⚪ 4 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer, preventing any security review of the logic.

**Recommendation:** Verify the contract source code on the block explorer to allow for public scrutiny.


### `QA-IDENTITY` — Imitation of Quack AI (Q)  *(Severity: Critical · Status: Acknowledged)*

Presents itself as Quack AI (Q), but the listed Q contract on bsc is 0xc07e1300dc138601fa6b0b59f8d0fa477e690589 (CoinGecko). Holders who think they own the real asset own this contract instead; it has none of the real asset's backing, liquidity or redemption.

**Recommendation:** Do not buy, hold or accept this token as the asset it names. Verify any token address against the issuer's official site.


### `H-01` — Centralized Ownership  *(Severity: High · Status: Unresolved)*

The contract is owned by an EOA, granting the owner full control over administrative functions without transparency.

**Recommendation:** Renounce ownership or transfer control to a multi-signature wallet or a time-locked governance contract.


### `M-01` — Lack of Operational Transparency  *(Severity: Medium · Status: Unresolved)*

There is no documentation or verified code to explain the token's economic model, tax structure, or liquidity management.

**Recommendation:** Provide clear documentation and verify the contract to explain all economic mechanisms to users.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x34f0…c385 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 80.4% of supply. Of that, 0.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 79.8% in wallets, 0.0% in other contracts. 1,381 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $3.1M (DexScreener, all pools). 24h trading volume $252.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Imitation of Quack AI (Q)  *(Severity: Informational · Status: Acknowledged)*

A token presenting itself under the name or ticker of an established asset without being that asset's contract. Its only reason to borrow that identity is to be mistaken for it. Scored as an imitation (see the identity finding). Basis: behaves as: project token. Tokenomics — Supply: mint capability could not be read. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $3.1M of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Do not treat this token as the asset it names. Use only the official contract address published by that asset's issuer.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfa9f...7777`](https://bscscan.com/address/0xfa9fc8bb8e2085cb0b58fa1957b1cee7eac37777) |
| **Network** | BNB Chain |
| **Price** | $0.3038 |
| **24h Volume** | $252.40M |
| **Liquidity** | $3.10M |
| **Volume / Liquidity** | 81.5× |
| **Token Age** | 7h |
| **Top-10 Holders** | 80.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3338 buys / 3135 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x5b9e254bfba6f06a87b0ae78827141c1ed0fb57f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/quack-ai-token-bsc-b719)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
