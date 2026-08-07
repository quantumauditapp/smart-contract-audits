---
token: Biconomy
ticker: BICO
network: ethereum
risk_score: 39
status: medium
date: 2026-08-07
---

# Biconomy (BICO) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 39/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/biconomy-eth)

---

## Audit Summary

The BicoToken contract, implemented as an upgradeable ERC-20 token behind a Transparent Proxy, leverages well-audited OpenZeppelin libraries for upgradeability, access control, and reentrancy protection. The proxy's administrative control is secured by a 2-of-3 multisig, enhancing operational security. While the architecture is robust, a known risk with Transparent Proxies regarding admin function clashes is present. The provided source code was truncated, limiting a full review of the entire implementation.

> **Final Recommendation:** It is recommended to ensure that the multisig administrators are fully aware of the Transparent Proxy pattern's specific operational considerations, particularly regarding potential function selector clashes. Implement robust internal procedures and testing for all upgrade proposals to mitigate this risk. Additionally, for future audits, provide the complete and verifiable source code for all contracts and their dependencies to allow for a comprehensive security review.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages battle-tested OpenZeppelin upgradeable libraries, including `Initializable` and `ReentrancyGuardUpgradeable`, which significantly enhances code security (7.2 Code Security).… |
| **Governance / Economics** | 1/10 | High | The contract's upgradeability and administrative functions are secured by a 2-of-3 multisig (7.5 Governance), providing a robust access control mechanism against single points of failure (7.3 Access… |
| **Upgrades** | 2/10 | High | The contract utilizes the Transparent Proxy pattern with OpenZeppelin's upgradeable contracts, including `Initializable` and `__gap` storage variables, ensuring proper storage layout for future… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | Multisig — 2-of-3 |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.4% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 2 Informational_

### `M-01` — Transparent Proxy Admin Function Clash  *(Severity: Medium · Status: Unresolved)*

The contract uses the Transparent Proxy pattern. A known characteristic of this pattern is that if the proxy admin (0x2a2d6e4919ff1519e3d7ede8e44164025654bce3) calls a function that exists in both the proxy contract and the implementation contract, the call will be routed to the proxy's function, not the implementation's. This can lead to unexpected behavior, failed transactions, or operational errors if the admin intends to interact with the implementation's logic (7.1 Architecture, 7.7 Upgrades).

**Recommendation:** The proxy admin should only call functions that are unique to the proxy (e.g., `upgradeTo`, `changeAdmin`). All other interactions with the contract's logic should be performed by non-admin accounts. Implement thorough testing and clear operational guidelines for the multisig signers to prevent accidental function clashes.


### `I-01` — Centralized Control of Upgradeability  *(Severity: Informational · Status: Unresolved)*

The upgradeability of the BicoToken is controlled by a 2-of-3 multisig (0x2a2d6e4919ff1519e3d7ede8e44164025654bce3). While a multisig enhances security over a single External Owned Account (EOA), it still represents a centralized point of control for future contract logic changes. This implies that a majority of the multisig signers can unilaterally decide on and execute upgrades, which could introduce new vulnerabilities or alter tokenomics (7.5 Governance, 7.3 Access Control).

**Recommendation:** This is a common and often necessary design choice for upgradeable contracts. For transparency, clearly communicate the role and responsibilities of the multisig signers to the community. Consider exploring more decentralized governance mechanisms for upgrades in the long term, if aligned with the project's vision.


### `I-02` — Incomplete Source Code Provided  *(Severity: Informational · Status: Unresolved)*

The provided source code snippet for the `BicoTokenImplementation` contract is truncated, specifically for the `StringsUpgradeable` library and potentially the main token logic. A full security audit requires access to the complete, verifiable source code of all deployed contracts and their dependencies to ensure no hidden logic or vulnerabilities exist beyond the scope of the provided snippet (7.2 Code Security).

**Recommendation:** For future audits, always provide the complete and verified source code for all contracts, including any imported libraries or inherited contracts, to enable a comprehensive security analysis.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf17e...c6c2`](https://etherscan.io/address/0xf17e65822b568b3903685a7c9f496cf7656cc6c2) |
| **Network** | Ethereum |
| **Price** | $0.04746 |
| **24h Volume** | $88.6K |
| **Liquidity** | $42.8K |
| **Volume / Liquidity** | 2.1× |
| **Token Age** | 4y |
| **Top-10 Holders** | 68.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 532 buys / 450 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x55d8ec728ea72477c6db12ca497a803c8db361e9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/biconomy-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-07*
