---
token: Pangea
ticker: PANGEA
network: base
risk_score: 84
status: high
date: 2026-10-26
---

# Pangea (PANGEA) — Smart Contract Security Analysis | Base

> **Risk Score: 84/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pangea-base-2d25)

---

## Audit Summary

The target contract is not verified on the Base block explorer, rendering the source code inaccessible for security analysis. Consequently, it is impossible to verify the presence of backdoors, minting functions, or tax mechanisms. Investors should exercise extreme caution as the lack of transparency is a significant indicator of potential risk.

> **Final Recommendation:** Do not interact with this contract. The lack of verified source code is a critical red flag that prevents any meaningful security assurance. Without transparency, there is no way to distinguish this contract from a malicious actor or a honeypot.

If you are considering an investment, wait for the developers to verify the contract on the block explorer. Perform thorough due diligence on the project's social presence and liquidity locks before considering any interaction.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture, 7.2 Code Security, 7.3 Access Control, 7.6 External: All technical aspects are opaque due to the lack of verified source code. Without bytecode analysis, it is impossible to… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic, 7.5 Governance: The economic model and governance structure are entirely hidden from the user. There is no way to verify if the owner has the ability to pause trading, blacklist… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades, 7.8 Operations: It is unknown if the contract utilizes a proxy pattern or is immutable. If the contract is a proxy, the implementation could be swapped at any time by an owner, leading… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 2 High · ⚪ 5 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not verified on the block explorer, making it impossible to audit the logic for vulnerabilities or malicious backdoors.

**Recommendation:** Verify the contract source code on the block explorer to provide transparency to users.


### `H-01` — Lack of Transparency  *(Severity: High · Status: Unresolved)*

The absence of public code prevents users from understanding the tokenomics, ownership privileges, and potential risks associated with the contract.

**Recommendation:** Publish the source code and provide documentation regarding the contract's functionality and ownership structure.


### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by the token's owner/deployer (0x5ca3…ffc1) — they can pull that liquidity at any moment. This is the rug-pull path. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 43.2% of supply. What remains: 22.8% in wallets, 20.5% in other contracts. 757 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

757 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $100K (DexScreener, all pools). 24h trading volume $3.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $100K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8fe5...2f63`](https://basescan.org/address/0x8fe5359c343813231279bef7a16b54e1b1622f63) |
| **Network** | Base |
| **Price** | $0.0001822 |
| **24h Volume** | $3.08M |
| **Liquidity** | $99.8K |
| **Volume / Liquidity** | 30.9× |
| **Token Age** | 10h |
| **Top-10 Holders** | 43.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3087 buys / 2303 sells |

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

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x7e57e887c3fb8f930cc84f1e6fc319608b64847e161c427487e60eb3aab82540)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pangea-base-2d25)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
