---
token: Gangstar
ticker: GANGSTAR
network: bsc
risk_score: 54
status: medium
date: 2026-10-27
---

# Gangstar (GANGSTAR) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 54/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gangstar-bsc)

---

## Audit Summary

The contract at the provided address is not verified on the BSC block explorer. Consequently, the source code is inaccessible, and no technical security analysis could be performed. Investors should exercise extreme caution as unverified contracts often lack transparency regarding ownership, minting capabilities, or transfer restrictions.

> **Final Recommendation:** Do not interact with or provide liquidity to this contract until the source code is verified on the block explorer. Perform thorough due diligence on the project's official documentation and community channels before considering any financial exposure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture: Unknown. 7.2 Code Security: Cannot be verified as the source code is unavailable. 7.3 Access Control: Cannot be verified, posing a risk of hidden administrative functions. 7.6… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic: Tokenomics and supply mechanics are opaque. 7.5 Governance: Potential for centralized control or malicious tax mechanisms cannot be ruled out. 7.8 Operations: Lack of transparency… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades: The contract's upgradeability status is unknown. Without source code, it is impossible to determine if the contract is immutable or if it contains proxy patterns that allow for logic… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 61.5% |
| **Top-3 Unlocked** | ⚠️ 91.9% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · ⚪ 5 Informational_

### `C-01` — Unverified Contract Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer, preventing any security review of the logic, ownership, or token mechanics.

**Recommendation:** Verify the contract source code on the block explorer to allow for community and security auditing.


### `H-02` — Opaque Administrative Privileges  *(Severity: High · Status: Unresolved)*

Without access to the source code, it is impossible to identify if the contract contains 'honeypot' features, such as restricted selling, hidden minting, or arbitrary tax adjustments.

**Recommendation:** Avoid interaction until the contract logic is transparent and audited by a reputable third party.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 5 address(es) other than the owner/deployer. One of them — a wallet, 0xa3f4…f38b — holds 61.5% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 23.3% of supply. What remains: 5.1% in wallets, 18.2% in other contracts. 1,313 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,313 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $86K (DexScreener, all pools). 24h trading volume $835K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $86K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6b2c...e694`](https://bscscan.com/address/0x6b2ce31a577d92f73516c7a91febc7672247e694) |
| **Network** | BNB Chain |
| **Price** | $0.0003497 |
| **24h Volume** | $834.7K |
| **Liquidity** | $85.6K |
| **Volume / Liquidity** | 9.7× |
| **Token Age** | 4h |
| **Top-10 Holders** | 23.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6357 buys / 4680 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xb61c41f8b334d183c4c22c026e9d35f363113330)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gangstar-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
