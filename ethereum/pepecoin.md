---
token: pepeCoin
ticker: PEPECOIN
network: ethereum
risk_score: 0
status: low
date: 2026-08-30
---

# pepeCoin (PEPECOIN) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pepecoin-eth)

---

## Audit Summary

The pepeCoin contract is an ERC20 token built upon battle-tested OpenZeppelin libraries. A key observation from the provided prefill data is that ownership of the contract has been renounced. This significantly impacts the functionality of owner-restricted functions, leading to a high-severity issue where any Ether sent to the contract will be permanently locked. Additionally, the initial token distribution is highly centralized, with the entire supply minted to the deployer. The contract also includes an unused `_tokenPrice` variable that can be misleading.

> **Final Recommendation:** Given the renounced ownership, it is critical to ensure no Ether is sent to the contract, as it will be permanently locked. For future projects, consider a more decentralized initial token distribution strategy to mitigate centralization risks. Evaluate the necessity of the `_tokenPrice` variable; if it serves no purpose, remove it to avoid confusion. Implement events for all critical state changes to enhance off-chain monitoring and transparency.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract leverages battle-tested OpenZeppelin contracts for ERC20 and Ownable functionalities, ensuring standard compliance and robust implementation of core token operations (7.2 Code Security).… |
| **Governance / Economics** | 10/10 | Low | The token features a fixed total supply and a burn mechanism, providing some predictability and deflationary potential. However, the primary economic risk stems from the highly centralized initial… |
| **Upgrades** | 10/10 | Low | The contract is not designed with an upgrade mechanism (e.g., proxy pattern), which inherently eliminates risks associated with upgradeability, such as proxy misconfigurations or malicious upgrade… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 99.2% — Null Address, UNCX |
| **Top-1 Unlocked Holder** | 0.6% |
| **Lock Expiry** | ✅ 2092 (verified ≥ 1 year) — UNCX V2 |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Centralized Token Distribution  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The entire `_totalSupply` of `pepeCoin` is minted to the contract deployer (`msg.sender`) in the constructor. This results in a highly centralized initial token distribution, where one address holds 100% of the token supply. Such centralization can lead to significant market manipulation risks, as the single holder has disproportionate control over the token's liquidity and price.

**Recommendation:** For future projects, consider implementing a more decentralized initial token distribution strategy, such as a fair launch, liquidity bootstrapping pool, or a vesting schedule for team tokens, to promote broader ownership and reduce centralization risks.


### `M-02` — Locked Ether Due to Renounced Ownership  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `withdraw()` function, which allows the contract owner to retrieve Ether, is protected by the `onlyOwner` modifier. According to the provided prefill data, the contract ownership has been renounced (`ownership_renounced: true`). This means the `_owner` address is set to `address(0)`, making the `onlyOwner` modifier always revert. Consequently, any Ether accidentally or intentionally sent to the contract will be permanently locked and inaccessible.

**Recommendation:** Ensure that no Ether is sent to this contract. If the contract was intended to hold or manage Ether, a redeployment with a revised withdrawal mechanism (e.g., a multi-signature wallet or a mechanism that allows anyone to trigger a withdrawal to a predefined address) would be necessary before renouncing ownership.


### `L-01` — Unused `_tokenPrice` Variable  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract includes a state variable `_tokenPrice` along with `setTokenPrice()` and `getTokenPrice()` functions. However, this `_tokenPrice` variable is not integrated into any core token logic, such as calculating transfer fees, enabling token purchases, or influencing any other economic mechanism within the contract. It serves no functional purpose, and its value is immutable due to renounced ownership.

**Recommendation:** Remove the `_tokenPrice` variable and its associated functions (`setTokenPrice`, `getTokenPrice`) if they are not intended to be used for any on-chain logic. This will reduce contract complexity, save gas, and prevent potential confusion for users or external systems that might misinterpret its purpose.


### `I-01` — Missing Event for State Change  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `setTokenPrice()` function modifies the `_tokenPrice` state variable but does not emit an event to signal this change. While this function is currently unusable due to renounced ownership, if it were callable, the absence of an event would make it difficult for off-chain applications, block explorers, or monitoring tools to track changes to this parameter.

**Recommendation:** For any function that modifies critical state variables, it is a best practice to emit an event. If `setTokenPrice` were to be functional, consider adding an event like `TokenPriceUpdated(uint256 oldPrice, uint256 newPrice)` to improve transparency and off-chain observability.


### `I-02` — Lack of Emergency Pause Mechanism  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract lacks a mechanism to pause critical operations, such as token transfers or burning, in case of an emergency (e.g., discovery of a critical vulnerability, major exploit, or market instability). While not strictly a vulnerability, a pause mechanism is a common security best practice for tokens to provide a temporary emergency stop.

**Recommendation:** Consider implementing a pause mechanism (e.g., using OpenZeppelin's `Pausable` contract) that can be triggered by a trusted entity (e.g., a multi-signature wallet or a governance contract). This would allow for a temporary halt of operations to address unforeseen issues, although this would require a redeployment given the current contract's non-upgradeable nature and renounced ownership.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa9e8...489a`](https://etherscan.io/address/0xa9e8acf069c58aec8825542845fd754e41a9489a) |
| **Network** | Ethereum |
| **Price** | $0.1584 |
| **24h Volume** | $178.4K |
| **Liquidity** | $1.92M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 3y |
| **Top-10 Holders** | 38.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 320 buys / 223 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xddd23787a6b80a794d952f5fb036d0b31a8e6aff)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pepecoin-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*
