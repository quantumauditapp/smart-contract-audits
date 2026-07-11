---
token: wojak
ticker: WOJAK
network: ethereum
risk_score: 15
status: low
date: 2026-06-10
---

# wojak (WOJAK) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wojak-eth)

---

## Audit Summary

The Wojak token contract is an ERC-20 implementation with custom tokenomics including transaction fees, liquidity fees, buyback fees, and transaction/wallet size limits. It utilizes OpenZeppelin's Ownable contract, granting significant control to a single owner address. While leveraging well-audited OpenZeppelin libraries, the custom logic introduces complexity and critical centralization risks.

> **Final Recommendation:** The Wojak token contract presents significant centralization risks due to the extensive privileges granted to the owner. While leveraging standard ERC-20 functionality, the custom tokenomics, particularly the owner's ability to manipulate fees and exclude addresses, introduces critical economic vulnerabilities. It is strongly recommended that potential users understand and accept these inherent risks. For enhanced security and decentralization, consider implementing a multi-signature wallet or a decentralized autonomous organization (DAO) for critical administrative functions, along with timelocks for sensitive parameter changes. A Premium Deploy option could include a comprehensive review of the owner's operational security practices and a formal verification of the complex `_transfer` logic.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract leverages battle-tested OpenZeppelin libraries for its ERC-20 and access control functionalities (7.2 Code Security). The `_swapAndLiquify` mechanism includes a reentrancy guard… |
| **Governance / Economics** | 7/10 | Low | The contract exhibits a high degree of centralization, with the owner possessing extensive control over critical economic parameters (7.5 Governance). The owner can unilaterally adjust all fee… |
| **Upgrades** | 9/10 | Low | The contract is not designed with an upgrade mechanism (7.7 Upgrades). This means its logic is immutable once deployed, providing certainty regarding its behavior. However, any discovered… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Centralized Control and Potential Rug Pull Vector  *(Severity: Critical · Status: Unresolved)*

The contract owner has the ability to set transfer fees (tax, liquidity, buyback) up to 100% and can exclude any address from these fees and transaction limits. This allows the owner to effectively halt all trading, drain all tokens from users by setting a 100% fee to their own wallet, or grant themselves privileged trading capabilities, representing a critical rug-pull vector and an unfair advantage.

**Recommendation:** Implement a maximum cap for all fee percentages (e.g., 10-20%) that cannot be exceeded. Remove or significantly restrict the `excludeFromFee` and `excludeFromMaxTransaction` functionalities, or subject them to a multi-signature wallet and timelock. Clearly communicate these capabilities to users.


### `H-01` — Extensive Owner Privileges and Single Point of Failure  *(Severity: High · Status: Unresolved)*

The `Ownable` pattern grants a single external account significant control over critical contract parameters, including all fee percentages, transaction limits, fee recipient wallets, and the ability to enable/disable the swap mechanism. This high degree of centralization creates a single point of failure and introduces substantial trust assumptions on the owner's benevolence and operational security.

**Recommendation:** Consider migrating ownership to a multi-signature wallet (e.g., Gnosis Safe) or a decentralized autonomous organization (DAO) to distribute control and reduce the risk associated with a single point of failure. Implement a timelock for sensitive administrative actions.


### `M-01` — Complex Transfer Logic  *(Severity: Medium · Status: Unresolved)*

The `_transfer` function incorporates intricate logic for applying multiple fee types, enforcing transaction and wallet size limits, and triggering an automated token swap. This complexity increases the attack surface and the likelihood of subtle bugs or unexpected interactions, making the code harder to audit and maintain.

**Recommendation:** Thoroughly test all possible execution paths within the `_transfer` function, especially edge cases related to fee calculations, limit enforcement, and the `_swapAndLiquify` trigger. Consider breaking down complex conditional logic into smaller, more manageable internal functions for improved readability and testability. Formal verification could be beneficial for this critical function.


### `L-01` — Lack of Timelock for Critical Operations  *(Severity: Low · Status: Unresolved)*

Critical owner-controlled functions, such as `setTaxFeePercent`, `setLiquidityFeePercent`, `setBuybackFeePercent`, `setTaxWallet`, `setLiquidityWallet`, `setBuybackWallet`, `setMaxTxPercent`, `setMaxWalletSize`, `excludeFromFee`, and `excludeFromMaxTransaction`, lack a timelock mechanism. This allows the owner to enact sensitive changes immediately without any delay for community review or intervention, increasing the risk of malicious or erroneous actions.

**Recommendation:** Implement a timelock for all sensitive owner-controlled functions. This would introduce a delay between the owner initiating a change and its actual execution, providing a window for community scrutiny and potential mitigation of malicious or erroneous actions.


### `I-01` — Reliance on External DEX Router  *(Severity: Informational · Status: Unresolved)*

The `_swapAndLiquify` function depends on an external Uniswap V2 router for token swaps. While Uniswap V2 is a widely used and generally trusted protocol, the contract's functionality is reliant on the continuous availability and correct operation of this external dependency. Any issues with the router could impact the token's fee collection and liquidity generation mechanisms.

**Recommendation:** Acknowledge the dependency on the external DEX router. While direct mitigation within this contract is limited, ensure that the chosen router address is correct and corresponds to a well-established and audited DEX. Consider monitoring the health and availability of the external router.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8de3...31ef`](https://etherscan.io/address/0x8de39b057cc6522230ab19c0205080a8663331ef) |
| **Network** | Ethereum |
| **Price** | $0.00000014 |
| **24h Volume** | $1.05M |
| **Liquidity** | $1.31M |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 3mo |
| **Top-10 Holders** | 37.4% of supply |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xcaa3a16f8440f85303afaab1992f2b97d12469b1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wojak-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
