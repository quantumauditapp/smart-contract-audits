---
token: TOSH
ticker: TOSH
network: bsc
risk_score: 56
status: medium
date: 2026-10-30
---

# TOSH (TOSH) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 56/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tosh-bsc)

---

## Audit Summary

The ToshTokenV3 is a minimal clone (EIP-1167) implementation of an ERC-20 token with custom minting and receiver registration logic. The architecture is immutable, preventing logic upgrades, but relies on external roles (bidbook, hook) for critical operations. Security coverage includes 7.1 Architecture (Minimal Clone), 7.2 Code Security (Standard ERC-20), 7.3 Access Control (Role-based), 7.4 Economic (Minting caps), 7.5 Governance (Limited), 7.6 External (Hook dependencies), 7.7 Upgrades (None), and 7.8 Operations (Role management).

> **Final Recommendation:** The protocol should ensure the 'hook' and 'bidbook' contracts are thoroughly audited, as they hold absolute authority over the token's minting and receiver registration processes. Since the DEFAULT_ADMIN_ROLE is left vacant, ensure the initial setup is perfect, as no administrative recovery path exists for role management.

Developers should replace the use of tx.origin with msg.sender in the registerReceiver function to prevent potential cross-contract authorization vulnerabilities. While the current implementation is immutable, ensure that all external dependencies are robust and resistant to flash loan or oracle manipulation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes a standard EIP-1167 minimal clone pattern, ensuring the implementation logic remains immutable and safe from proxy-based attacks. Code quality is high, adhering to standard… |
| **Governance / Economics** | 1/10 | High | Economic control is centralized within the MINTER_ROLE, which is assigned to the 'hook' address. The lack of an active DEFAULT_ADMIN_ROLE means that once initialized, the minter role cannot be… |
| **Upgrades** | 2/10 | High | The contract is deployed as a minimal clone, which is inherently immutable. No upgrade mechanisms are present, meaning the logic cannot be altered post-deployment. This eliminates risks associated… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 54.5% |
| **Top-3 Unlocked** | ⚠️ 95.3% |

## Security Findings

_🟡 3 Medium · ⚪ 5 Informational_

### `CD-01` — Use of tx.origin for Authorization  *(Severity: Medium · Status: Unresolved)*

The registerReceiver function uses tx.origin to verify the caller. This is a security risk because a malicious contract could potentially trick a user into calling a function that triggers this registration, bypassing intended security checks.

**Recommendation:** Replace tx.origin with msg.sender to ensure that only the direct caller can register themselves as a receiver.


### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The mint(address,uint256) function allows the holder of the MINTER_ROLE to create new tokens at will, up to the MAX_SUPPLY. This grants the 'hook' contract significant power to dilute existing token holders.

**Recommendation:** Implement a multi-signature wallet or a time-locked governance contract to manage the MINTER_ROLE to prevent unauthorized or sudden supply inflation.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 4 address(es) other than the owner/deployer. One of them — a contract, 0xecd1…3dea — holds 54.5% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 41.3% of supply. Of that, 1.4% burned — not holders that can sell, so excluded from the concentration score. What remains: 5.4% in wallets, 34.6% in other contracts. 2,054 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,054 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $106K (GeckoTerminal, all pools). 24h trading volume $1.1M (GeckoTerminal, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $106K of DEX liquidity across 17 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xcb54...bfb3`](https://bscscan.com/address/0xcb54cfbc2699c405e5c88cdec75cba2ec8b7bfb3) |
| **Network** | BNB Chain |
| **Price** | $0.00038823 |
| **24h Volume** | $957.9K |
| **Liquidity** | $103.6K |
| **Volume / Liquidity** | 9.2× |
| **Token Age** | 1d |
| **Top-10 Holders** | 41.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4924 buys / 4328 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xcb54cfbc2699c405e5c88cdec75cba2ec8b7bfb3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tosh-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
