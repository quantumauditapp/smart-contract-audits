---
token: UNICURVE
ticker: UNICURVE
network: ethereum
risk_score: 72
status: critical
date: 2026-08-01
---

# UNICURVE (UNICURVE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 72/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/unicurve-eth)

---

## Audit Summary

The UnicurveToken contract is an ERC20 token designed for an EIP-1167 cloning pattern. It features a highly centralized control model where a designated 'curve' address receives the entire token supply and controls the ability to enable/disable transfers. While the code is simple and leverages OpenZeppelin's battle-tested ERC20 implementation, the extreme centralization introduces significant economic and operational risks, including potential for a rug pull and permanent transfer lock.

> **Final Recommendation:** Given the highly centralized nature of the UnicurveToken, it is paramount to ensure the security and trustworthiness of the `curve` address. Implement robust key management practices for this address, potentially utilizing a multi-signature wallet or a time-locked contract for critical operations like enabling transfers or managing the initial token supply. Transparency with the community regarding the token's distribution and control mechanisms is also crucial to manage expectations and build trust.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract leverages battle-tested OpenZeppelin ERC20 for core token functionality, enhancing code security (7.2 Code Security). The logic is straightforward, primarily managing a… |
| **Governance / Economics** | 1/10 | High | The economic model is highly centralized, with the entire token supply minted to the `curve` address upon initialization (7.4 Economic). This grants the `curve` address complete control over token… |
| **Upgrades** | 1/10 | High | The `UnicurveToken` contract is designed as an EIP-1167 clone, meaning it is not directly upgradeable (7.7 Upgrades). This eliminates risks associated with upgrade mechanisms, such as proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Centralized Control by `curve` Address  *(Severity: High · Status: Unresolved)*

The `curve` address, set during initialization, is the sole recipient of the entire token supply (1 billion tokens) and the only entity capable of calling `enableTransfers()`. This grants the `curve` address complete control over token distribution and transferability, representing a single point of failure (7.3 Access Control, 7.5 Governance).

**Recommendation:** Acknowledge and clearly communicate this high degree of centralization to all users and potential investors. If future decentralization is desired, consider implementing a multi-signature wallet or a time-locked contract for the `curve` address to manage critical functions.


### `H-02` — Potential for Rug Pull / Malicious `curve` Behavior  *(Severity: High · Status: Unresolved)*

With 100% of the token supply minted to the `curve` address and its exclusive control over enabling transfers, there is a significant risk of a 'rug pull' (7.4 Economic). If the `curve` address is controlled by a malicious actor, they could unilaterally dump all tokens onto the market, causing a severe price crash.

**Recommendation:** Transparency is crucial. Clearly communicate the token distribution model and the power of the `curve` address to potential investors. Implement mechanisms (e.g., liquidity locks, vesting schedules for the `curve` address's holdings) in the `curve` contract itself to build trust, if applicable to the project's design.


### `M-01` — Permanent Transfer Lock Risk  *(Severity: Medium · Status: Unresolved)*

The `enableTransfers()` function, which sets `transfersEnabled = true`, can only be called by the `curve` address. If the `curve` address is compromised, lost, or becomes inaccessible, the tokens could remain permanently untransferable (except for transfers involving the `curve` itself), leading to a denial of service for token holders (7.3 Access Control, 7.8 Operations).

**Recommendation:** Ensure robust security and operational procedures for the `curve` address. Consider a mechanism to transfer `curve` ownership or a time-locked release of transfer control if the original `curve` becomes unresponsive, though this adds complexity and new risks.


### `L-01` — EIP-1167 Clone Initialization Race Condition (Theoretical)  *(Severity: Low · Status: Unresolved)*

The `initialize` function lacks explicit access control beyond the `AlreadyInitialized` check. In an EIP-1167 factory deployment scenario, if the factory's deployment and initialization logic is not atomic or properly secured, a malicious actor could theoretically front-run the `initialize` call on a newly deployed clone, setting an attacker-controlled `curve` address (7.2 Code Security, 7.3 Access Control).

**Recommendation:** Ensure the factory contract responsible for deploying and initializing `UnicurveToken` clones implements robust access control (e.g., `onlyFactory` or `onlyOwner` for initialization calls) and/or atomic deployment-initialization patterns to prevent front-running.


### `I-01` — Missing Event for `enableTransfers`  *(Severity: Informational · Status: Unresolved)*

The `enableTransfers()` function modifies a critical state variable (`transfersEnabled`) but does not emit an event. Emitting an event would improve transparency and allow off-chain monitoring of this crucial state change (7.2 Code Security, 7.8 Operations).

**Recommendation:** Emit an event (e.g., `event TransfersEnabled(address indexed caller, uint256 timestamp);`) when `transfersEnabled` is set to `true` to provide better traceability and off-chain monitoring capabilities.


### `I-02` — Hardcoded `SUPPLY` Constant  *(Severity: Informational · Status: Unresolved)*

The `SUPPLY` variable is declared as a `public constant`, fixing the total token supply at 1,000,000,000e18. This design choice means the token's total supply cannot be altered in the future without deploying a new contract (7.1 Architecture, 7.4 Economic).

**Recommendation:** This is a design decision for a fixed-supply token. No action is required if this immutability is intended. If flexibility in total supply was ever desired, a different token architecture (e.g., mintable/burnable) would be necessary.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd400...c0de`](https://etherscan.io/address/0xd400a048b726eba969449b342dc7c0e74187c0de) |
| **Network** | Ethereum |
| **Price** | $0.0001266 |
| **24h Volume** | $133.8K |
| **Liquidity** | $51.6K |
| **Volume / Liquidity** | 2.6× |
| **Token Age** | 3mo |
| **Top-10 Holders** | 36.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 378 buys / 280 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x6092abe3f6076f4e03954d9eab5f66cea426ecd395c1fd8289eca870a6241eab)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/unicurve-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-01*
