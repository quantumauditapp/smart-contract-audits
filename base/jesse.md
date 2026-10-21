---
token: jesse
ticker: JESSE
network: base
risk_score: 63
status: medium
date: 2026-08-31
---

# jesse (JESSE) — Smart Contract Security Analysis | Base

> **Risk Score: 63/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/jesse-base)

---

## Audit Summary

The audit of the CreatorCoin and BaseCoin contracts identified a critical architectural misconfiguration related to the use of upgradeable patterns in a standalone deployment, which could lead to an uninitialized or exploitable state if not handled correctly. Additionally, the system exhibits centralization risks through its MultiOwnable pattern and lacks event emissions for key configuration changes. The vesting mechanism appears robust, and the code quality is generally high, leveraging OpenZeppelin standards. Addressing the critical architectural issue is paramount for the secure operation of the protocol.

> **Final Recommendation:** It is critical to resolve the architectural misconfiguration regarding the use of upgradeable patterns in a standalone contract. Either refactor the contract to remove all upgradeable components and move initialization logic to the constructor, or deploy it correctly behind a proxy contract if upgradeability is intended. Implement event emissions for all critical configuration changes to enhance transparency and auditability. Consider implementing a timelock for administrative actions controlled by `MultiOwnable` to mitigate centralization risks and provide a window for community review.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The technical architecture of CreatorCoin, inheriting from BaseCoin, is generally well-structured, leveraging OpenZeppelin contracts for ERC20 and access control. The vesting logic in CreatorCoin is… |
| **Governance / Economics** | 1/10 | High | The economic model for CreatorCoin incorporates a vesting schedule for creator supply, with `_calculateVestedAmount` and `getClaimableAmount` functions designed to prevent over-claiming, ensuring a… |
| **Upgrades** | 1/10 | High | The `CreatorCoin` and `BaseCoin` contracts incorporate OpenZeppelin's `Upgradeable` components and the `initializer` modifier, which are standard for proxy-based upgradeable systems. However, the… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 98.8% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `C-01` — Architectural Misconfiguration: Upgradeable Pattern in Standalone Contract  *(Severity: Critical · Status: Unresolved)*

The `BaseCoin` contract, from which `CreatorCoin` inherits, utilizes OpenZeppelin's `Upgradeable` contracts (`ERC20PermitUpgradeable`, `ERC165Upgradeable`) and the `initializer` modifier in both its constructor and its `initialize` function. This pattern is exclusively designed for proxy-based upgradeable contracts (e.g., UUPS or Transparent proxies). However, the deployment context indicates `is_proxy: false`, meaning `CreatorCoin` is deployed as a standalone contract. When deployed directly, the contract's constructor runs once. The `initializer` modifier on the constructor will execute. Subsequently, the `initialize` function *must be called separately* to set up critical contract parame…

**Recommendation:** If the contract is intended to be non-upgradeable, remove all `Upgradeable` base contracts and the `initializer` modifier. Move all initialization logic from the `initialize` function directly into the constructor. If the contract *is* intended to be upgradeable, it must be deployed behind a proxy contract (e.g., UUPS proxy), and the `is_proxy` flag in the deployment context should be `true`.


### `M-01` — Centralization Risk with MultiOwnable  *(Severity: Medium · Status: Unresolved)*

The `BaseCoin` contract uses the `MultiOwnable` pattern for critical administrative functions such as `setPayoutRecipient` and `setContractURI`. While `MultiOwnable` allows for multiple addresses to collectively control these functions, it still represents a centralized point of control. A compromise of a majority of the owner keys could lead to unauthorized changes to the contract's configuration, including redirecting the `payoutRecipient` to a malicious address, potentially impacting token distributions.

**Recommendation:** Consider implementing a timelock mechanism for critical administrative actions controlled by `MultiOwnable`. This would introduce a delay between the initiation and execution of sensitive changes, allowing for monitoring and potential intervention, thereby mitigating the immediate impact of a compromised owner key. Additionally, ensure robust key management practices for all owner addresses.


### `L-01` — Lack of Event Emission for Critical Configuration Changes  *(Severity: Low · Status: Unresolved)*

The `_setPayoutRecipient` and `_setContractURI` internal functions, which are called by external `onlyOwner` functions (`setPayoutRecipient`, `setContractURI`), do not emit events upon execution. While the `CreatorVestingClaimed` event is emitted for vesting claims, changes to core configuration parameters like the `payoutRecipient` or `contractURI` are not logged on-chain. This makes it challenging to monitor and audit changes to the contract's operational parameters, hindering transparency and off-chain analysis.

**Recommendation:** Emit specific events (e.g., `PayoutRecipientUpdated(address oldRecipient, address newRecipient)` and `ContractURIUpdated(string oldURI, string newURI)`) whenever critical configuration parameters are changed. This will provide a clear, immutable record of all administrative actions on-chain, improving transparency and auditability.


### `I-01` — Reliance on Hardcoded Constants  *(Severity: Informational · Status: Unresolved)*

The `CreatorCoin` contract relies heavily on hardcoded constants defined in `CoinConstants.sol` for critical parameters such as `CREATOR_COIN_MARKET_SUPPLY`, `TOTAL_SUPPLY`, `CREATOR_VESTING_DURATION`, and `CREATOR_COIN_CURRENCY`. While using constants ensures immutability and predictability, it removes flexibility for future adjustments or parameter tuning without requiring a full contract redeployment.

**Recommendation:** For parameters that might require future adjustments (e.g., vesting duration, supply caps), consider making them configurable by an authorized entity (e.g., `MultiOwnable` or governance) through setter functions, rather than hardcoding them. This would allow for greater adaptability to changing market conditions or protocol needs. If immutability is the explicit design choice, document this decision clearly.


### `I-02` — Potential for Vesting Dust Amounts Due to Integer Division  *(Severity: Informational · Status: Unresolved)*

The `_calculateVestedAmount` function uses integer division: `(CoinConstants.CREATOR_COIN_CREATOR_VESTING_SUPPLY * elapsedTime) / CoinConstants.CREATOR_VESTING_DURATION`. If `CREATOR_COIN_CREATOR_VESTING_SUPPLY` is not perfectly divisible by `CREATOR_VESTING_DURATION`, or if the `elapsedTime` does not perfectly align with a full vesting period, there might be a small remainder (dust) that is truncated during the division. This could result in a tiny amount of tokens being perpetually locked or the final claim being slightly less than expected.

**Recommendation:** While generally negligible for large token amounts, consider using a fixed-point math library or adjusting the calculation to ensure that any remaining dust is accounted for, especially in the final vesting period. For example, ensure the last claim explicitly transfers any remaining balance up to `CREATOR_COIN_CREATOR_VESTING_SUPPLY - totalClaimed` to prevent dust from being locked.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x50f8...0d59`](https://basescan.org/address/0x50f88fe97f72cd3e75b9eb4f747f59bceba80d59) |
| **Network** | Base |
| **Price** | $0.001868 |
| **24h Volume** | $6.1K |
| **Liquidity** | $553.9K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 9mo |
| **Top-10 Holders** | 77.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 327 buys / 1251 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xc39acb3ce11ebcd3e1c5d67cdfb8707ab12674449fdab859327a8aabee03cd10)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/jesse-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-31*
