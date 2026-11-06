---
token: KieDex
ticker: KDX
network: base
risk_score: 64
status: medium
date: 2026-11-06
---

# KieDex (KDX) — Smart Contract Security Analysis | Base

> **Risk Score: 64/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kiedex-base)

---

## Audit Summary

The KieDex token contract implements a standard ERC-20 interface with an integrated fee-redirection mechanism. The contract exhibits critical flaws regarding external calls and state management that could lead to total loss of contract funds.

> **Final Recommendation:** Immediate remediation is required to remove the 'self.balance' transfer logic, which exposes the contract to potential drainage. Implement standard reentrancy guards and ensure that external calls to the fee wallet are strictly controlled and validated.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows a standard ERC-20 pattern but introduces a dangerous fee-redirection logic. 7.1 Architecture: The contract uses a simple state-based transfer mechanism. 7.2 Code Security… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic: The token lacks deflationary or inflationary mechanics beyond the fee redirection. 7.5 Governance: No governance mechanisms are implemented. 7.6 External: The contract relies on an… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades: The contract is immutable and does not support proxy patterns. 7.8 Operations: Operational security is limited by the lack of administrative control over the fee destination. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 5 Medium · ⚪ 5 Informational_

### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 79.1% of supply. What remains: 79.0% in wallets, 0.0% in other contracts. The deployer/owner wallet itself holds 78.9%. A holder that also controls the contract can sell into its own liquidity. 2,114 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `M-01` — Lack of Input Validation  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The 'feeWallet' address is not validated, potentially allowing transfers to be sent to an uninitialized or malicious contract.

**Recommendation:** Add a check to ensure the feeWallet address is not the zero address and is a trusted contract.


### `M-02` — Unsafe External Call to Fee Wallet  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The 'transfer' and 'transferFrom' functions call 'self.feeWallet.send(value = self.balance)'. This attempts to send the entire contract balance to the fee wallet on every transfer, which will drain the contract of all native tokens.

**Recommendation:** Remove the automatic balance transfer logic. If fees are required, implement a specific fee calculation based on the transaction amount, not the contract balance.


### `M-03` — Reentrancy Vulnerability  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract performs an external call to 'feeWallet' before updating internal balances, creating a reentrancy vector.

**Recommendation:** Follow the Checks-Effects-Interactions pattern. Update all internal state variables before making any external calls.


### `M-04` — Irreversible Ownership Lock  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The constructor sets the owner to the zero address, permanently locking any administrative functions that might be added in the future.

**Recommendation:** Set the owner to a secure multisig or a DAO address during deployment.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x73a2…3aeb — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — Redundant State Variables  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The variables 'lastFrom', 'lastTo', and 'sender' are updated but never used for logic, increasing gas costs unnecessarily.

**Recommendation:** Remove unused state variables to optimize gas usage.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,114 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $33K (DexScreener, all pools). 24h trading volume $179K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $33K of DEX liquidity across 1 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2580...0496`](https://basescan.org/address/0x2580aaefdf307f943691e8f7edd1315506690496) |
| **Network** | Base |
| **Price** | $0.04981 |
| **24h Volume** | $178.8K |
| **Liquidity** | $33.4K |
| **Volume / Liquidity** | 5.3× |
| **Token Age** | 1d |
| **Top-10 Holders** | 79.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1759 buys / 1767 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x3bc3cbc450f72229f408881ea5aa466c3471c686)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kiedex-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-06*
