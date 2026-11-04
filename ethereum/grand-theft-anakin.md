---
token: Grand Theft Anakin
ticker: GTA
network: ethereum
risk_score: 64
status: medium
date: 2026-11-04
---

# Grand Theft Anakin (GTA) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 64/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/grand-theft-anakin-eth)

---

## Audit Summary

The contract at the provided address is not verified on the Ethereum block explorer. Consequently, the source code is unavailable for security analysis. Investors should exercise extreme caution as the lack of transparency prevents verification of ownership, tax mechanisms, or liquidity safety.

> **Final Recommendation:** Do not interact with this contract. The absence of verified source code is a major red flag that prevents any meaningful security assessment. Without transparency, there is no way to ensure that the contract does not contain malicious functions such as blacklisting, infinite minting, or honeypot mechanisms.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture: Unknown. 7.2 Code Security: Cannot be assessed due to lack of source code. 7.3 Access Control: Cannot be verified; potential for hidden backdoors or owner-only functions exists. 7.6… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic: Liquidity is currently unlocked, posing a high risk of rug-pull. 7.5 Governance: No documentation exists regarding tokenomics or administrative control. 7.8 Operations: The project… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades: As the contract is unverified, it is impossible to determine if the contract is a proxy or if it contains upgradeable logic that could alter token behavior post-deployment. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer, making it impossible to audit for security vulnerabilities or malicious logic.

**Recommendation:** Verify the contract source code on the block explorer to allow for community and security review.


### `H-01` — Unlocked Liquidity  *(Severity: High · Status: Unresolved)*

Liquidity for this token is currently unlocked, allowing the deployer to withdraw all funds from the liquidity pool at any time.

**Recommendation:** Lock liquidity in a reputable, time-locked smart contract to protect investors.


### `H-02` — Lack of Transparency  *(Severity: High · Status: Unresolved)*

The project lacks public documentation or verifiable ownership, increasing the risk of centralized control and potential exit scams.

**Recommendation:** Provide clear documentation regarding tokenomics, ownership, and project roadmap.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xe627…8b13 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 34.7% of supply. What remains: 22.1% in wallets, 12.6% in other contracts. 122 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

122 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $31K (DexScreener, all pools). 24h trading volume $51K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $31K of DEX liquidity across 5 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa736...4cd2`](https://etherscan.io/address/0xa7362118a42ad52c68a694972b308cfb02e94cd2) |
| **Network** | Ethereum |
| **Price** | $0.0001123 |
| **24h Volume** | $51.5K |
| **Liquidity** | $30.6K |
| **Volume / Liquidity** | 1.7× |
| **Token Age** | 13h |
| **Top-10 Holders** | 34.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 314 buys / 126 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x945f0d74052c249572cf9a555b11d431cde2d2c2ce49f678a3bdd68b03e3a770)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/grand-theft-anakin-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
