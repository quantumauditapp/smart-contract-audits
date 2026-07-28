---
token: TRADOOR
ticker: TRADOOR
network: bsc
risk_score: 34
status: medium
date: 2026-07-25
---

# TRADOOR (TRADOOR) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 34/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tradoor-bsc)

---

## Audit Summary

The audited contract is a basic ERC20 token implementation, inheriting from battle-tested OpenZeppelin contracts. The custom logic is minimal, primarily minting the initial supply to the deployer. While technically robust due to its reliance on audited libraries, the design presents a medium economic risk due to the centralization of the initial token supply with the deployer. The contract is immutable, offering predictable behavior but no upgrade path.

> **Final Recommendation:** For projects intending to launch a public token, consider implementing a more decentralized initial distribution strategy to mitigate the economic risks associated with a single entity holding the entire supply. This could involve vesting schedules, airdrops, or liquidity pool provisions. Additionally, evaluate the need for emergency controls like pausing or blacklisting functions, which can be crucial for responding to unforeseen events or exploits, even for simple tokens. If such features are desired, they should be integrated with appropriate access control mechanisms.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The technical architecture (7.1) is straightforward, implementing a standard ERC20 token. Code security (7.2) is high due to the extensive use of OpenZeppelin's audited ERC20 library, which handles… |
| **Governance / Economics** | 2/10 | High | The economic model (7.4) involves minting the entire initial token supply to the deployer, which presents a centralization risk. This concentration of tokens could allow the deployer to significantly… |
| **Upgrades** | 6/10 | Medium | The contract is not designed with any upgradeability pattern (7.7), such as proxies. This means the contract is immutable once deployed, and its logic cannot be altered. While this provides certainty… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 97.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Centralization of Initial Token Supply  *(Severity: Medium · Status: Unresolved)*

The `Token` contract's constructor mints the entire `supply` to `msg.sender` (the deployer). This design choice results in 100% of the initial token supply being held by a single address. This concentration of tokens creates a significant centralization risk (7.4 Economic), as the deployer could potentially manipulate the market, dump tokens, or exert undue influence over the token's ecosystem.

**Recommendation:** If the token is intended for a decentralized project or public distribution, consider implementing a more diversified initial distribution strategy. This could involve: 1) Minting to a multi-signature wallet for controlled distribution. 2) Allocating portions to various stakeholders (e.g., treasury, liquidity pools, community airdrops). 3) Implementing a vesting schedule for team or early investor allocations.


### `L-01` — Lack of Emergency Controls  *(Severity: Low · Status: Unresolved)*

The `Token` contract, being a basic ERC20, does not include any emergency control mechanisms such as `pause` or `blacklist` functionality. While this simplifies the contract and reduces complexity, the absence of these controls (7.8 Operations) means that in the event of a critical vulnerability, exploit, or regulatory requirement, there is no built-in mechanism to halt transfers or restrict malicious addresses, potentially leading to irreversible damage.

**Recommendation:** Assess the project's risk tolerance and potential future needs. If the ability to react to emergencies is deemed important, consider integrating OpenZeppelin's `Pausable` or `Blacklist` modules. These should be controlled by a robust access control mechanism, such as a multi-signature wallet, to prevent single points of failure.


### `I-01` — Reliance on OpenZeppelin Standards  *(Severity: Informational · Status: Unresolved)*

The `Token` contract heavily relies on the battle-tested and widely audited OpenZeppelin Contracts library (v4.9.0) for its ERC20 implementation. This significantly reduces the risk of common vulnerabilities (7.2 Code Security) such as reentrancy, integer overflows/underflows, and incorrect ERC20 behavior, as these libraries are maintained by a reputable team and have undergone extensive scrutiny.

**Recommendation:** Continue to monitor OpenZeppelin's security advisories and updates. Ensure that any future custom logic or modifications are thoroughly reviewed to maintain the high security standard provided by the base library.


### `I-02` — Immutability of Contract Logic  *(Severity: Informational · Status: Unresolved)*

The `Token` contract is deployed as a standard, non-upgradeable contract. This means its logic is immutable once deployed to the blockchain (7.7 Upgrades). This design provides certainty and eliminates risks associated with upgrade mechanisms (e.g., proxy vulnerabilities, upgrade key compromise). However, it also implies that any discovered bugs or desired feature enhancements cannot be implemented without deploying an entirely new contract and migrating existing token holders.

**Recommendation:** Acknowledge the trade-offs of immutability. For a simple token, this is often an acceptable design. If future flexibility or bug-fixing capabilities are critical, consider an upgradeable proxy pattern for future contract deployments, ensuring proper implementation and robust access control for upgrade functions.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9123...f492`](https://bscscan.com/address/0x9123400446a56176eb1b6be9ee5cf703e409f492) |
| **Network** | BNB Chain |
| **Price** | $0.5008 |
| **24h Volume** | $576.3K |
| **Liquidity** | $712.0K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 10mo |
| **Top-10 Holders** | 89.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3713 buys / 3810 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is TRADOOR a scam?

Based on automated analysis, TRADOOR scores 67/100 (High Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is TRADOOR safe to buy?

Our scanner flagged a risk score of 67/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has TRADOOR been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x924e62a3689e7b94f397e61ac796dabfea32e93b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tradoor-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-25*
