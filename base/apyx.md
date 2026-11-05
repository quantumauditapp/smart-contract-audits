---
token: APYX
ticker: APYX
network: base
risk_score: 49
status: medium
date: 2026-11-05
---

# APYX (APYX) — Smart Contract Security Analysis | Base

> **Risk Score: 49/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/apyx-base)

---

## Audit Summary

The APYX token implementation contains critical logic flaws regarding fee handling and arithmetic operations. The contract attempts to send the entire contract balance to a fee wallet on every transfer, which is highly dangerous and likely to cause transaction failures or loss of funds. The audit covers 7.1 Architecture, 7.2 Code Security, 7.3 Access Control, 7.4 Economic, 7.5 Governance, 7.6 External, 7.7 Upgrades, 7.8 Operations.

> **Final Recommendation:** The contract should be redeployed after removing the fee-on-transfer mechanism, which currently attempts to send the entire contract balance on every transaction. The arithmetic functions should be audited for underflow risks and removed if they serve no purpose for the token's core functionality.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture relies on an external fee wallet call within every transfer, which is prone to reentrancy and gas exhaustion. 7.1 Architecture shows a lack of separation between token logic and fee… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic analysis shows no complex DeFi primitives, but the fee mechanism is fundamentally broken. 7.5 Governance is non-existent as ownership is burned at deployment. No economic incentives or… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades: The contract is not upgradeable. The ownership is burned, making the contract immutable. No upgrade risk exists. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 5 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 36.0% of supply. What remains: 35.9% in wallets, 0.1% in other contracts. The deployer/owner wallet itself holds 35.8%. A holder that also controls the contract can sell into its own liquidity. 9,132 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `M-01` — Redundant Code  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The functions MultiSum and check are identical and serve no purpose for an ERC-20 token.

**Recommendation:** Remove unused and redundant code to reduce gas costs and attack surface.


### `M-02` — Unsafe Fee Distribution  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The transfer functions call feeWallet.send(value = self.balance) on every transfer. This will cause all transfers to fail if the contract has insufficient ETH or if the feeWallet is not a payable contract, effectively bricking the token.

**Recommendation:** Remove the fee distribution logic or implement a standard fee-on-transfer mechanism that only transfers a percentage of the token amount, not the contract's ETH balance.


### `M-03` — Arithmetic Underflow in MultiSum  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The expression 'num1 - num5 / num6' in MultiSum does not check if num1 is greater than the result of the division, leading to potential underflow errors in Vyper.

**Recommendation:** Add explicit checks to ensure num1 >= (num5 / num6) before subtraction.


### `M-04` — Unprotected External Call  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The feeWallet address is not restricted, allowing any address to be set if a setter existed, or potentially causing issues if the address is a malicious contract.

**Recommendation:** Validate the feeWallet address and ensure it implements the expected interface.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xe085…faec — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `L-01` — Lack of Zero Address Validation  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The transfer functions do not prevent transfers to the zero address.

**Recommendation:** Add 'assert _to != empty(address)' to prevent accidental burning of tokens.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

9,132 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $50K (DexScreener, all pools). 24h trading volume $486K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $50K of DEX liquidity across 1 pools. Launch: 13 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 13 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 13 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x36d5...0290`](https://basescan.org/address/0x36d539900653b5d721ecec9ca9d7bacf65f10290) |
| **Network** | Base |
| **Price** | $0.6332 |
| **24h Volume** | $485.8K |
| **Liquidity** | $49.6K |
| **Volume / Liquidity** | 9.8× |
| **Token Age** | 13d |
| **Top-10 Holders** | 36.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3828 buys / 3736 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xe58da38dec80450e5e30e865ea027dde6b15c723)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/apyx-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
