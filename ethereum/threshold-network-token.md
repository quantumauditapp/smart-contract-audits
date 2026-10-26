---
token: Threshold Network Token
ticker: T
network: ethereum
risk_score: 54
status: medium
date: 2026-09-03
---

# Threshold Network Token (T) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 54/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/threshold-network-token-eth)

---

## Audit Summary

The audit of the T token contract reveals a well-structured ERC20 implementation with EIP-2612 permit and delegation features. Key security considerations include a reentrancy vulnerability in `approveAndCall` and front-running risks for signature-based operations. Dependencies on external, unaudited contracts also introduce potential risks, particularly concerning the `maxSupply` and voting power mechanisms.

> **Final Recommendation:** Address the identified reentrancy vulnerability in `approveAndCall` by implementing a Checks-Effects-Interactions pattern or using a reentrancy guard. Evaluate the necessity of `approveAndCall` and consider removing it if its risks outweigh its benefits. Review the `maxSupply()` implementation in the inherited contracts to ensure its robustness. Conduct a comprehensive audit of all external dependencies, specifically `MisfundRecovery` and `Checkpoints`, to ensure their security and proper integration with the token contract.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates strong technical foundations, utilizing Solidity 0.8.9 for automatic overflow/underflow protection and inheriting from battle-tested OpenZeppelin and Thesis libraries. The… |
| **Governance / Economics** | 3/10 | High | The economic model benefits from a `maxSupply` check during minting, preventing uncontrolled inflation (7.4 Economic). The `mint` function is appropriately restricted to the contract owner, which is… |
| **Upgrades** | 5/10 | Medium | The contract is not deployed as an upgradeable proxy, meaning direct in-place upgrades are not possible (7.7 Upgrades). Any significant changes to the token logic would necessitate a new deployment… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Front-running Risk in Signature-based Functions  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `permit` and `delegateBySig` functions rely on off-chain signed messages. While nonces and deadlines are used to prevent replay attacks, these transactions can still be front-run. A malicious actor could observe a pending transaction, submit their own transaction with a higher gas price, and potentially execute the action before the legitimate user, leading to a denial of service for the original signer or unexpected state changes, especially if the `deadline` is set far in the future.

**Recommendation:** Educate users about the risks of front-running for signature-based transactions and advise them to use short, reasonable deadlines. While not fully preventable, clear communication can mitigate user impact. Consider implementing a commit-reveal scheme for highly sensitive operations if applicable, though this adds complexity.


### `M-02` — Reentrancy Vulnerability in `approveAndCall`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `approveAndCall` function performs an external call to `spender.receiveApproval` after modifying the allowance state. If the `spender` contract is malicious or compromised, it could re-enter the token contract and perform unauthorized actions before the `approve` state change is fully committed, potentially leading to unexpected behavior or loss of funds. This violates the Checks-Effects-Interactions pattern.

**Recommendation:** Implement a reentrancy guard on the `approveAndCall` function or ensure that the external call is the last operation after all state changes. Alternatively, consider removing the `approveAndCall` function if its utility does not justify the inherent reentrancy risk.


### `L-01` — Undefined `maxSupply()` Function  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `mint` function in `T.sol` includes a `require` statement checking `totalSupply + amount <= maxSupply()`. However, the `maxSupply()` function is not defined within the provided `T.sol` or `ERC20WithPermit.sol` code. This implies a dependency on an external or inherited contract (e.g., `MisfundRecovery` or `Checkpoints`) for a critical economic constraint. Without its definition, the actual maximum supply limit and its enforceability cannot be fully assessed, posing an architectural dependency risk.

**Recommendation:** Ensure that the `maxSupply()` function is clearly defined and its logic is robust and immutable, or controlled by a secure governance mechanism. Document its location and behavior thoroughly. If it's intended to be a fixed value, consider making it a `constant` or `immutable` variable.


### `I-01` — Dependency on Unaudited External Contracts  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `T` contract inherits from `MisfundRecovery` and `Checkpoints`, whose source code was not provided for this audit. The security and correctness of the `T` token heavily rely on the proper functioning and security of these external contracts, particularly `Checkpoints` for voting power mechanics and `MisfundRecovery` for potential token recovery. Any vulnerabilities in these dependencies could directly impact the `T` token.

**Recommendation:** Conduct a comprehensive security audit of all external and inherited contracts (`MisfundRecovery`, `Checkpoints`) to ensure their robustness, correctness, and absence of vulnerabilities. Ensure that these dependencies are from reputable sources and have undergone prior security reviews.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xcdf7...bee5`](https://etherscan.io/address/0xcdf7028ceab81fa0c6971208e83fa7872994bee5) |
| **Network** | Ethereum |
| **Price** | $0.004428 |
| **24h Volume** | $83.3K |
| **Liquidity** | $473.8K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 4y |
| **Top-10 Holders** | 75.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 671 buys / 643 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x752ebeb79963cf0732e9c0fec72a49fd1defaeac)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/threshold-network-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-03*
