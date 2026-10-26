---
token: Prometeus
ticker: PROM
network: bsc
risk_score: 57
status: medium
date: 2026-09-01
---

# Prometeus (PROM) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/prometeus-bsc)

---

## Audit Summary

The Prometeus (PROM) Token contract is a standard BEP20 implementation with `Ownable` access control and `SafeMath` for arithmetic operations. The contract exhibits good adherence to BEP20 standards and includes common security practices such as zero-address checks and event emissions. Identified risks are minor, primarily related to the use of an older Solidity compiler version and a low-severity `approve` race condition, which is partially mitigated by helper functions.

> **Final Recommendation:** It is recommended to consider migrating to a newer Solidity compiler version (e.g., 0.8.x) to leverage built-in overflow/underflow checks and gas optimizations, making `SafeMath` redundant. While the contract includes mitigation for the `approve` race condition, users should still be educated on the best practices of using `increaseAllowance` and `decreaseAllowance` instead of directly calling `approve` when adjusting existing allowances. Regular security reviews of any interacting contracts are also advised.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical architecture (7.1 Architecture) is a straightforward BEP20 token with `Ownable` pattern. Code security (7.2 Code Security) is strong, utilizing `SafeMath` to prevent integer… |
| **Governance / Economics** | 1/10 | High | The economic model (7.4 Economic) is a fixed-supply token with all tokens minted to the deployer at creation, which is a standard distribution model. There are no complex economic mechanisms… |
| **Upgrades** | 6/10 | Medium | The contract is not designed to be upgradeable (7.7 Upgrades), meaning there are no proxy patterns (e.g., UUPS, Transparent, Beacon) implemented. This eliminates upgrade-related risks such as proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.7% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟢 1 Low · ⚪ 1 Informational_

### `L-01` — Potential `approve` Race Condition (Mitigated)  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The standard ERC-20 `approve` function is susceptible to a front-running attack where a malicious actor can observe a transaction to decrease an allowance and front-run it, transferring the original approved amount before the allowance is reduced. This could lead to a user approving a larger amount than intended. While the contract provides `increaseAllowance` and `decreaseAllowance` functions to mitigate this by allowing atomic adjustments, the base `approve` function still exists and can be used directly.

**Recommendation:** Educate users to primarily use `increaseAllowance` and `decreaseAllowance` instead of directly calling `approve` when modifying an existing allowance. For new approvals, `approve` is safe. Ensure any external integrations or dApps interacting with this token prioritize the use of the safer allowance adjustment functions.


### `I-01` — Use of Older Solidity Compiler Version  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract is compiled with Solidity version `0.5.16`. While functional, this version is older. Newer Solidity versions (e.g., 0.8.x) offer significant improvements, including built-in overflow/underflow checks (making `SafeMath` redundant and potentially saving gas), better optimizer performance, and enhanced security features.

**Recommendation:** Consider upgrading the Solidity compiler version to a more recent stable release (e.g., 0.8.x) for future deployments or contract updates. This would allow for removal of the `SafeMath` library, reducing bytecode size and gas costs, and leveraging modern compiler optimizations.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xaf53...afd5`](https://bscscan.com/address/0xaf53d56ff99f1322515e54fdde93ff8b3b7dafd5) |
| **Network** | BNB Chain |
| **Price** | $5.2700 |
| **24h Volume** | $191.4K |
| **Liquidity** | $132.9K |
| **Volume / Liquidity** | 1.4× |
| **Token Age** | 1y |
| **Top-10 Holders** | 98.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3759 buys / 3358 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x83e98cac01259a0d00729cfb722810472c421459)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/prometeus-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-01*
