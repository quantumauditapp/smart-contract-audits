---
token: Non-Playable Coin
ticker: NPC
network: ethereum
risk_score: 0
status: low
date: 2026-08-12
---

# Non-Playable Coin (NPC) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/non-playable-coin-eth)

---

## Audit Summary

The NPC Token contract is a standard ERC-20 implementation, leveraging well-audited OpenZeppelin libraries. The provided code also includes an ERC1155Holder contract for receiving ERC-1155 tokens. Key security features include the use of safe arithmetic and the renunciation of ownership, which enhances decentralization. A full audit is limited by the truncation of the `_burn` function in the provided source code.

> **Final Recommendation:** It is recommended to ensure that the full, untruncated source code is available for any future audits or public verification to confirm the integrity of all functions, especially `_burn`. While the current implementation appears robust due to its reliance on OpenZeppelin standards and renounced ownership, thorough verification of the complete codebase is always a best practice. Users should be aware of the fixed token supply model due to the absence of public minting or burning capabilities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The codebase primarily consists of well-audited OpenZeppelin contracts for ERC-20, ERC-165, ERC-1155Receiver, and Ownable functionalities (7.1 Architecture, 7.2 Code Security). Safe arithmetic… |
| **Governance / Economics** | 9/10 | Low | The contract utilizes the Ownable pattern for administrative control. However, the prefill indicates that ownership has been renounced, which significantly reduces governance risk by removing a… |
| **Upgrades** | 10/10 | Low | The contract is not designed with upgradeability features, as indicated by `is_proxy: false` in the prefill (7.7 Upgrades). This means the contract's logic is immutable once deployed, eliminating… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — Null Address, TeamFinance |

## Security Findings

_🟢 1 Low · ⚪ 3 Informational_

### `L-01` — Incomplete Code Provided for Audit  *(Severity: Low · Status: Unresolved)*

The provided source code for the `_burn` function within the ERC20 contract is truncated. This prevents a comprehensive security analysis of the entire contract logic, specifically the token burning mechanism. While the visible parts of the ERC20 contract follow OpenZeppelin standards, the incomplete `_burn` function could potentially hide vulnerabilities or unexpected behavior.

**Recommendation:** Always provide the complete and final source code for all contracts intended for audit. Ensure that no functions or code blocks are truncated, allowing for a thorough and accurate security review.


### `I-01` — Standard Library Usage  *(Severity: Informational · Status: Unresolved)*

The contract extensively utilizes well-audited and widely adopted OpenZeppelin contracts for core functionalities such as ERC-20 token standards, Ownable access control, ERC-165 interface detection, and ERC-1155Receiver implementation. This practice significantly reduces the risk of common vulnerabilities and enhances the overall reliability and security of the codebase (7.2 Code Security).

**Recommendation:** Continue to leverage battle-tested libraries like OpenZeppelin. Regularly check for updates to these libraries to benefit from ongoing security improvements and bug fixes.


### `I-02` — Ownership Renounced  *(Severity: Informational · Status: Unresolved)*

According to the provided prefill data, the ownership of the contract has been renounced. This means the `owner` address is set to the zero address, making it impossible to call `onlyOwner` functions. This action decentralizes control, removes a single point of failure, and prevents potential malicious actions by a compromised owner key (7.3 Access Control, 7.5 Governance).

**Recommendation:** Ensure that the renunciation of ownership was an intentional and irreversible decision, as it removes the ability to perform any owner-restricted administrative tasks. Communicate this status clearly to the community.


### `I-03` — Fixed Token Supply (No Public Mint/Burn)  *(Severity: Informational · Status: Unresolved)*

The ERC20 contract includes internal `_mint` and `_burn` functions but does not expose any public or external functions to call them. This design choice, especially when combined with renounced ownership, implies that the token's total supply is fixed after its initial deployment and constructor-based minting (if any). There is no mechanism for the owner or any other entity to alter the supply post-deployment (7.4 Economic).

**Recommendation:** Clearly document this fixed supply characteristic for users and stakeholders. If future supply adjustments are ever desired, a new contract or a more complex governance mechanism would be required.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8ed9...08f6`](https://etherscan.io/address/0x8ed97a637a790be1feff5e888d43629dc05408f6) |
| **Network** | Ethereum |
| **Price** | $0.005336 |
| **24h Volume** | $73.3K |
| **Liquidity** | $2.13M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 3y |
| **Top-10 Holders** | 40.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 54 buys / 57 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x69c7bd26512f52bf6f76fab834140d13dda673ca)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/non-playable-coin-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-12*
