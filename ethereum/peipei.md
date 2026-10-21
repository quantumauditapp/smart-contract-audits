---
token: PeiPei
ticker: PEIPEI
network: ethereum
risk_score: 0
status: low
date: 2026-09-04
---

# PeiPei (PEIPEI) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/peipei-eth)

---

## Audit Summary

The audit of the provided ERC20 token contract reveals a well-structured implementation adhering to the ERC20 standard, utilizing SafeMath for arithmetic safety. The contract includes internal minting and burning functions, which are not publicly exposed by the ERC20 contract itself. A significant limitation is the truncation of the `Ownable` contract, preventing a full assessment of its access control mechanisms. However, the prefill data indicates that ownership has been renounced, which, if accurate, mitigates centralized control risks. Overall, the contract presents a Low risk profile.

> **Final Recommendation:** Ensure that the full source code for all inherited contracts, especially `Ownable`, is available for a complete security assessment. Implement comprehensive NatSpec documentation for all public and external functions to improve code clarity and maintainability. Verify the on-chain state of ownership renunciation to confirm the absence of centralized control.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract demonstrates good technical architecture (7.1 Architecture) by implementing the ERC20 standard and utilizing the SafeMath library, which prevents common integer overflow/underflow… |
| **Governance / Economics** | 9/10 | Low | The contract's economic model (7.4 Economic) is based on a standard ERC20 token with internal minting and burning capabilities. The provided prefill indicates that ownership has been renounced, which… |
| **Upgrades** | 10/10 | Low | The contract is not designed as an upgradeable proxy (7.7 Upgrades), meaning its logic cannot be changed after deployment. This eliminates upgrade-related risks such as proxy initialization issues or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟢 2 Low · ⚪ 3 Informational_

### `L-01` — Incomplete `Ownable` Contract Provided  *(Severity: Low · Status: Unresolved)*

The provided source code for the `Ownable` contract is truncated. This prevents a full security assessment of its implementation, including verification of standard access control patterns, potential owner-controlled functions, and the impact of the `ownership_renounced: true` prefill information. Without the complete code, it's impossible to confirm the exact privileges of the owner or the implications of ownership renunciation.

**Recommendation:** Provide the complete and verified source code for all inherited contracts, especially `Ownable`, to allow for a comprehensive security audit of access control mechanisms (7.3 Access Control) and governance implications (7.5 Governance).


### `L-02` — Missing NatSpec Documentation  *(Severity: Low · Status: Unresolved)*

Several functions within the contract, particularly internal and private helper functions, lack comprehensive NatSpec documentation. This can hinder understanding of the contract's logic, especially for future maintainers or auditors, and may lead to misinterpretations or errors during upgrades or integrations.

**Recommendation:** Add detailed NatSpec comments for all functions, especially those that are public, external, or implement complex logic. This includes `@param`, `@return`, and `@notice` tags to clearly describe their purpose, parameters, and return values.


### `I-01` — Use of SafeMath Library  *(Severity: Informational · Status: Resolved)*

The contract correctly utilizes the SafeMath library for all arithmetic operations (addition, subtraction, multiplication, division, modulo). This effectively prevents integer overflow and underflow vulnerabilities (7.2 Code Security), which are common pitfalls in Solidity development.

**Recommendation:** Maintain the consistent use of SafeMath or Solidity's native checked arithmetic (available in Solidity 0.8.0 and above) for all arithmetic operations to ensure robust handling of numerical values.


### `I-02` — Adherence to ERC20 Standard  *(Severity: Informational · Status: Resolved)*

The contract implements the ERC20 standard correctly, including all required functions (`totalSupply`, `balanceOf`, `transfer`, `allowance`, `approve`, `transferFrom`) and events (`Transfer`, `Approval`). This ensures compatibility with various DeFi protocols and wallets (7.6 External).

**Recommendation:** Continue to adhere strictly to established ERC standards to maintain broad compatibility and interoperability within the EVM ecosystem.


### `I-03` — Internal Mint/Burn Functions  *(Severity: Informational · Status: Resolved)*

The `_mint` and `_burn` functions are declared as `internal virtual`. This design choice means that the ERC20 contract itself does not expose public minting or burning capabilities. Any such functionality would need to be explicitly implemented in a derived contract, allowing for controlled inflation/deflation mechanisms (7.4 Economic).

**Recommendation:** If public minting or burning is intended in a derived contract, ensure that these functions are protected by appropriate access control mechanisms (e.g., only callable by a trusted role or governance) to prevent unauthorized token supply manipulation.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3ffe...5790`](https://etherscan.io/address/0x3ffeea07a27fab7ad1df5297fa75e77a43cb5790) |
| **Network** | Ethereum |
| **Price** | $0.00000001 |
| **24h Volume** | $34.9K |
| **Liquidity** | $639.2K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 2y |
| **Top-10 Holders** | 39.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 82 buys / 55 sells |

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

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xbf16540c857b4e32ce6c37d2f7725c8eec869b8b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/peipei-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-04*
