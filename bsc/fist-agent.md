---
token: FIST Agent
ticker: FAGENT
network: bsc
risk_score: 62
status: medium
date: 2026-11-01
---

# FIST Agent (FAGENT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 62/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fist-agent-bsc)

---

## Audit Summary

The contract at the provided address is not verified on the block explorer. Consequently, the source code is inaccessible for security analysis. Investors should exercise extreme caution as the lack of transparency prevents verification of ownership, tax mechanisms, or potential backdoors.

> **Final Recommendation:** Do not interact with this contract until the source code is verified on the block explorer. Verify the contract to allow for community audit and transparency regarding tax, minting, or blacklisting capabilities. 

Prioritize checking for ownership renouncement and liquidity lock status before considering any interaction. Without verified code, the contract should be treated as a high-risk asset.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical architecture cannot be evaluated due to the lack of verified source code. 7.1 Architecture and 7.2 Code Security are impossible to assess. 7.3 Access Control remains opaque, posing a… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance parameters are hidden from the public. The contract is controlled by an EOA (0x2175...), which implies centralized authority over the token's economic logic. There is… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not applicable as the contract is not a proxy. However, the inability to verify the code means potential hidden upgrade-like logic or logic-swapping functions cannot be ruled out.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 2 Medium · ⚪ 5 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer, preventing any security audit or verification of functionality.

**Recommendation:** Verify the contract source code on the block explorer immediately.


### `H-01` — Centralized Ownership  *(Severity: High · Status: Unresolved)*

The contract is owned by an EOA, granting the owner full control over administrative functions without transparency.

**Recommendation:** Renounce ownership or transfer control to a multi-sig wallet if administrative functions are required.


### `M-01` — Lack of Transparency  *(Severity: Medium · Status: Unresolved)*

The absence of verified code prevents users from identifying potential malicious features such as honeypot mechanisms or excessive transaction taxes.

**Recommendation:** Publish the source code and provide documentation for all custom logic.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x62a4…bf0c — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 56.2% of supply. What remains: 0.6% in wallets, 55.6% in other contracts. 4,973 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

4,973 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $26K (DexScreener, all pools). 24h trading volume $317K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $26K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0c87...0220`](https://bscscan.com/address/0x0c876f2f7c44cde660ab77bd2022537a305e0220) |
| **Network** | BNB Chain |
| **Price** | $0.00005315 |
| **24h Volume** | $317.5K |
| **Liquidity** | $26.2K |
| **Volume / Liquidity** | 12.1× |
| **Token Age** | 9h |
| **Top-10 Holders** | 56.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2704 buys / 4902 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x51201b678370714e07deec869d864245a8679a16)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fist-agent-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-01*
