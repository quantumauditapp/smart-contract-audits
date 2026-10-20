---
token: THEA Finance
ticker: THEA
network: arbitrum
risk_score: 73
status: high
date: 2026-10-08
---

# THEA Finance (THEA) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 73/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/thea-finance-arb)

---

## Audit Summary

This audit report is based on an unverified contract on the Arbitrum network. Due to the absence of publicly available source code, a comprehensive security analysis cannot be performed. The assessment is limited to external observations and general security best practices. The contract's reported deployment date (2026-10-07) is in the future, which is unusual and may indicate data discrepancy. Users are strongly cautioned against interacting with unverified contracts.

> **Final Recommendation:** It is strongly recommended that the contract's source code be verified on a block explorer. Without verified source code, users cannot independently audit the contract's functionality or security, posing significant trust and security risks. Interacting with unverified contracts should be avoided, as they may contain malicious logic, backdoors, or critical vulnerabilities that are not apparent from external observation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | Without access to the source code, a detailed technical assessment of the contract's architecture (7.1) and code security (7.2) is impossible. It is unknown if the contract follows secure coding… |
| **Governance / Economics** | 1/10 | High | The economic model (7.4) and governance mechanisms (7.5) of this contract cannot be assessed without source code. It is unknown if the contract manages any assets, implements fee structures, or has… |
| **Upgrades** | 6/10 | Medium | The upgradeability (7.7) of this contract cannot be determined without source code. It is unknown if the contract utilizes a proxy pattern (e.g., UUPS, Transparent) or if its logic can be modified… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.7% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 8 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0x8002…9c3f — holds 99.7% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `L-01` — Lack of Verified Source Code  *(Severity: Low · Status: Unresolved)*

The source code for the contract at address 0xd1ffd96424c22132bf785ddd88ae9c23ebfc0f8c is not verified on the Arbitrum block explorer. This prevents any form of code review or security analysis, making it impossible to ascertain the contract's intended functionality, security posture, or adherence to best practices (7.2 Code Security).

**Recommendation:** Verify the contract's source code on the block explorer. This allows for transparency, community review, and independent security audits, significantly reducing the trust assumption required from users.


### `I-01` — Unusual Future Deployment Date  *(Severity: Informational · Status: Unresolved)*

The provided deployment date for the contract is '2026-10-07T05:23:43Z', which is in the future. This is highly unusual for a deployed contract and may indicate a data discrepancy or an error in the provided metadata. While not a direct security vulnerability, it raises questions about the accuracy of the contract's associated information (7.8 Operations).

**Recommendation:** Confirm the actual deployment date of the contract. If this date is incorrect, ensure that all metadata associated with the contract is accurate to avoid confusion and maintain transparency.


### `I-02` — Inability to Assess Access Control  *(Severity: Informational · Status: Unresolved)*

Without the source code, it is impossible to evaluate the access control mechanisms (7.3 Access Control) implemented within the contract. It is unknown if critical functions are properly protected, if there are privileged roles, or if ownership can be transferred securely. This lack of visibility poses a potential risk of unauthorized actions or centralized control.

**Recommendation:** If the contract is intended to be permissioned or have administrative functions, ensure that robust and transparent access control mechanisms are implemented and clearly documented. Verification of source code would allow for this assessment.


### `I-03` — Potential for Hidden Malicious Logic  *(Severity: Informational · Status: Unresolved)*

The absence of verified source code means that the contract could contain arbitrary or malicious logic, such as backdoors, self-destruct functions, or unexpected state changes. Users interacting with such a contract are exposed to unknown risks, including loss of funds or unexpected behavior (7.2 Code Security).

**Recommendation:** Always prioritize interaction with contracts that have verified source code. If interaction is unavoidable, proceed with extreme caution and only after understanding the potential risks. Consider using a decompiler, though this provides limited insight and is not a substitute for verified source.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 92.3% of supply. What remains: 90.3% in wallets, 2.0% in other contracts. The deployer/owner wallet itself holds 2.0%. 415 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

415 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $125K (DexScreener, all pools). 24h trading volume $203K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $125K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd1ff...0f8c`](https://arbiscan.io/address/0xd1ffd96424c22132bf785ddd88ae9c23ebfc0f8c) |
| **Network** | Arbitrum |
| **Price** | $0.3585 |
| **24h Volume** | $202.7K |
| **Liquidity** | $125.4K |
| **Volume / Liquidity** | 1.6× |
| **Token Age** | 23h |
| **Top-10 Holders** | 92.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 897 buys / 303 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0xaba7dd2ee1a76b90ed92dfc6e62d05ec3dc09fb8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/thea-finance-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-08*
