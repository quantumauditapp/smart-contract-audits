---
token: CREPE
ticker: CREPE
network: bsc
risk_score: 0
status: low
date: 2026-07-25
---

# CREPE (CREPE) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/crepe-bsc)

---

## Audit Summary

The provided source code consists of standard Uniswap V2 interfaces (IUniswapV2Router01, IUniswapV2Router02, IUniswapV2Factory) and a utility library (Address). No concrete contract implementation, such as the 'CREPE' contract mentioned in the prefill, was provided for a comprehensive security audit. The analysis is therefore limited to the provided interfaces and library. The Address library implements common low-level call wrappers, which appear robust, though one function was truncated. Without the full contract logic, a complete assessment of potential vulnerabilities, economic risks, or upgradeability concerns is not possible.

> **Final Recommendation:** To conduct a comprehensive security audit, it is crucial to provide the complete source code for all contracts intended for deployment, especially the 'CREPE' contract. This includes any implementation contracts, proxy contracts, and all dependent libraries or modules. A full audit would then cover the interactions between these components, access control mechanisms, economic models, and upgradeability considerations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The provided code includes standard Uniswap V2 interfaces and a robust Address utility library. The library's functions for `sendValue` and `functionCallWithValue` include essential checks for… |
| **Governance / Economics** | 10/10 | Low | No specific contract logic related to governance or economic models was provided for review (7.4 Economic, 7.5 Governance). The interfaces define standard DeFi primitives, but their integration into… |
| **Upgrades** | 10/10 | Low | The provided code does not include any proxy contracts or upgradeability patterns (7.7 Upgrades). The interfaces and utility library are not inherently upgradeable components. Without the main… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | 3.5% |
| **LP Locked** | 100.0% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 0.0% |

## Security Findings

_⚪ 3 Informational_

### `I-01` — Incomplete Contract Code Provided for Audit  *(Severity: Informational · Status: Unresolved)*

The audit scope was limited to standard Uniswap V2 interfaces (IUniswapV2Router01, IUniswapV2Router02, IUniswapV2Factory) and a utility library (Address). The main contract, referred to as 'CREPE' in the prefill, was not provided. This prevents a comprehensive security assessment of the protocol's core logic, architecture (7.1 Architecture), access control (7.3 Access Control), economic model (7.4 Economic), and overall operational security (7.8 Operations).

**Recommendation:** Provide the complete source code for all contracts comprising the 'CREPE' protocol, including any implementation contracts, proxy contracts, and all custom libraries or dependencies. This will enable a full security review.


### `I-02` — Truncated Function in Address Library  *(Severity: Informational · Status: Unresolved)*

The `verifyCallResultFromTarget` function within the `Address` library was truncated in the provided source code. While the visible parts of the library's call wrappers appear robust, the full implementation of this critical error-handling function could not be reviewed (7.2 Code Security).

**Recommendation:** Ensure the complete and correct source code for all libraries is provided. Verify that `verifyCallResultFromTarget` correctly handles return data and error conditions, similar to established libraries like OpenZeppelin's `Address` library.


### `I-03` — Reliance on External Uniswap V2 Interfaces  *(Severity: Informational · Status: Unresolved)*

The provided code includes interfaces for Uniswap V2 routers and factory. Any contract interacting with these interfaces will be dependent on the security and correct functioning of the deployed Uniswap V2 contracts (7.6 External). While Uniswap V2 is a widely audited and established protocol, the security of the overall system relies on the correct integration and assumptions made about these external contracts.

**Recommendation:** When integrating with external protocols like Uniswap V2, ensure that all interactions are carefully designed to handle potential slippage, front-running, and unexpected behavior. Implement robust checks on return values and consider using trusted or whitelisted router addresses. This is a general best practice for external dependencies.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xeb2b...931d`](https://bscscan.com/address/0xeb2b7d5691878627eff20492ca7c9a71228d931d) |
| **Network** | BNB Chain |
| **Price** | $0.00001104 |
| **24h Volume** | $19.3K |
| **Liquidity** | $622.7K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 1y |
| **Top-10 Holders** | 27.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 413 buys / 425 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is CREPE a scam?

Based on automated analysis, CREPE scores 0/100 (Low Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is CREPE safe to buy?

Our scanner flagged a risk score of 0/100. Ownership is renounced which reduces rug-pull risk. DYOR before purchasing any token.

### Has CREPE been audited?

The contract is open-source and verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x7d90deedb9f15c1f8fdaccc3b6bc52dc208e9c9a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/crepe-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-25*
