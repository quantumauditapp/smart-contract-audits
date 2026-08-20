---
token: TokenFi
ticker: TOKEN
network: bsc
risk_score: 28
status: medium
date: 2026-08-20
---

# TokenFi (TOKEN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 28/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tokenfi-bsc)

---

## Audit Summary

The T1 contract is an ERC-20 token implementation with Compound-style governance delegation features. It utilizes OpenZeppelin's Ownable pattern for administrative functions and integrates with external Tax and Treasury handlers. The contract exhibits good adherence to ERC-20 standards for core transfer logic, including safe handling of integer arithmetic. Key findings include an incorrect usage of `transferFrom` in the `withdraw` function, significant centralized control by the owner, and inherent risks associated with critical external dependencies. The owner is a multisig, which partially mitigates centralization risks.

> **Final Recommendation:** It is recommended to address the identified functional bug in the `withdraw` function to ensure proper ERC-20 token recovery. A thorough review of the `ITaxHandler` and `ITreasuryHandler` contracts is crucial, as their security directly impacts the T1 token system. Consider implementing a timelock for critical owner-controlled functions to introduce a delay for sensitive operations, enhancing security and transparency.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract demonstrates a solid foundation, leveraging OpenZeppelin libraries and implementing standard ERC-20 and governance patterns (7.1 Architecture, 7.2 Code Security). Integer arithmetic is… |
| **Governance / Economics** | 7/10 | Low | The contract implements a Compound-style delegation system for governance, allowing token holders to delegate their voting power, which is a robust and widely adopted model (7.5 Governance). The… |
| **Upgrades** | 8/10 | Low | The T1 contract is not designed with an upgrade mechanism (e.g., proxy pattern). This means the contract's logic cannot be modified post-deployment. While this eliminates upgrade-related risks, any… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 90.6% — OnlyMoons Lock |
| **Top-1 Unlocked Holder** | 9.4% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Incorrect ERC-20 `transferFrom` usage in `withdraw` function  *(Severity: Medium · Status: Unresolved)*

The `withdraw` function, intended for recovering ERC-20 tokens, uses `IERC20(tokenAddress).transferFrom(address(this), address(treasuryHandler), amount);`. For a contract to send tokens it holds, it should use `IERC20(tokenAddress).transfer(address(treasuryHandler), amount);`. The current implementation requires the `T1` contract itself to have approved the `treasuryHandler` to spend its own tokens, which is an incorrect and impractical setup, effectively preventing the withdrawal of ERC-20 tokens from the contract.

**Recommendation:** Change the ERC-20 withdrawal logic in the `withdraw` function from `IERC20(tokenAddress).transferFrom(address(this), address(treasuryHandler), amount);` to `IERC20(tokenAddress).transfer(address(treasuryHandler), amount);`.


### `M-02` — Centralized Control over Critical Parameters and Funds  *(Severity: Medium · Status: Unresolved)*

The `onlyOwner` role has significant control over critical functions, including `setTaxHandler`, `setTreasuryHandler`, and `withdraw`. This allows a single entity (or a multisig, as indicated by the prefill) to change core external dependencies and withdraw any tokens (including native currency) held by the contract. While the owner is a multisig, this level of centralized control still presents a single point of failure or potential for malicious action if the multisig is compromised.

**Recommendation:** Consider implementing a timelock for sensitive `onlyOwner` functions, such as `setTaxHandler`, `setTreasuryHandler`, and potentially `withdraw`. This would introduce a delay before changes take effect, allowing time for community review or intervention if a malicious action is detected. Alternatively, explore a more decentralized governance mechanism for these critical operations.


### `M-03` — Reliance on External Contract Security  *(Severity: Medium · Status: Unresolved)*

The T1 contract heavily relies on external contracts, `ITaxHandler` and `ITreasuryHandler`, which are set by the owner. The security, correctness, and trustworthiness of these external contracts are paramount. A vulnerability or malicious design within `ITaxHandler` or `ITreasuryHandler` could directly impact the T1 token's functionality or economic model, potentially leading to unexpected behavior or loss of funds.

**Recommendation:** Ensure that `ITaxHandler` and `ITreasuryHandler` contracts undergo rigorous security audits. Implement robust validation checks for new handler addresses (e.g., checking if the address is a contract, or if it implements expected interfaces). Consider a community-driven or timelocked process for updating these critical external dependencies.


### `L-01` — Hardcoded Token Parameters  *(Severity: Low · Status: Unresolved)*

The `totalSupply()` and `decimals()` functions return hardcoded values (5e9 * 1e9 and 9, respectively). While this provides predictability and is common for many tokens, it means these parameters cannot be adjusted in the future without deploying a new contract. This limits flexibility for potential future economic model adjustments.

**Recommendation:** If future flexibility is desired, consider making `totalSupply` or `decimals` configurable during deployment or through a governance mechanism. However, for a standard fixed-supply token, this is often an acceptable design choice.


### `I-01` — Inconsistent Visibility for ERC-20 Metadata Functions  *(Severity: Informational · Status: Unresolved)*

The `name()` function is declared as `public view`, while `symbol()` and `decimals()` are declared as `external view` or `external pure`. While this does not pose a security vulnerability, it represents a minor inconsistency in function visibility for standard ERC-20 metadata getters.

**Recommendation:** For consistency and adherence to common ERC-20 patterns, consider declaring `name()` as `external view` to match `symbol()` and `decimals()`.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4507...b528`](https://bscscan.com/address/0x4507cef57c46789ef8d1a19ea45f4216bae2b528) |
| **Network** | BNB Chain |
| **Price** | $0.002116 |
| **24h Volume** | $263.4K |
| **Liquidity** | $1.37M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 2y |
| **Top-10 Holders** | 75.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1182 buys / 870 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x05616b7b6da03fb4c773b76663816b360ccaede4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tokenfi-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-20*
