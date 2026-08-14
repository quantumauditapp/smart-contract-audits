---
token: GoPlus Security
ticker: GPS
network: bsc
risk_score: 65
status: high
date: 2026-08-14
---

# GoPlus Security (GPS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 65/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/goplus-security-bsc)

---

## Audit Summary

The HypERC20 contract implements an upgradeable ERC-20 token with interchain capabilities, leveraging Hyperlane's Mailbox system for cross-chain transfers. The contract utilizes OpenZeppelin's upgradeable patterns and standard ERC-20 functionalities, with custom logic for burning tokens on the source chain and minting on the destination chain. Key strengths include the use of battle-tested OpenZeppelin libraries and a multisig for ownership. However, the system exhibits a high degree of centralized control by the owner multisig over critical interchain security parameters and initial token distribution, posing significant trust assumptions and potential single points of failure. Operational risks related to gas configuration also exist.

> **Final Recommendation:** Prioritize strengthening the governance and operational security around the owner multisig, given its extensive control over critical interchain components and initial token supply. Implement robust monitoring for all external dependencies and cross-chain transaction health. Consider a roadmap for progressive decentralization of key parameters, potentially through time-locks or community governance, to reduce single points of failure and enhance the protocol's long-term resilience.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The HypERC20 contract demonstrates good architectural design for an interchain token, utilizing a modular approach with clear separation of concerns for token logic, routing, and gas management (7.1… |
| **Governance / Economics** | 1/10 | High | The contract's economic model is a burn-and-mint cross-chain token, which is a standard approach. Access control is primarily managed through an `onlyOwner` modifier, with the owner being a multisig… |
| **Upgrades** | 3/10 | High | The contract is designed for upgradeability using OpenZeppelin's `ERC20Upgradeable` and `OwnableUpgradeable` patterns, including `initializer` functions and `__GAP` storage slots (7.7 Upgrades). This… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 2-of-3 |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control over Critical Interchain Security Parameters  *(Severity: High · Status: Unresolved)*

The `owner` (a multisig) has exclusive control over setting the `interchainSecurityModule` and `hook` contracts via `setInterchainSecurityModule` and `setHook` functions. These contracts are fundamental to the security and functionality of cross-chain message verification and post-dispatch logic. A compromise of the owner's private keys or the multisig itself could allow a malicious actor to replace these critical components with arbitrary contracts, potentially leading to unauthorized minting, burning, or other severe exploits. This impacts 7.3 Access Control, 7.4 Economic, 7.5 Governance, and 7.6 External.

**Recommendation:** While centralized control is common in early-stage protocols, consider a phased approach to decentralization. Implement time-locks for changes to critical parameters, or introduce a more robust governance mechanism (e.g., a DAO) for such sensitive operations. Ensure the multisig itself has strong operational security, including multi-factor authentication and strict key management policies.


### `M-01` — Initial Token Supply Concentrated with Owner  *(Severity: Medium · Status: Unresolved)*

The `initialize` function of `HypERC20` mints the entire `_totalSupply` to `msg.sender`, which, in the context of a proxy, is the address that calls `initialize` (the proxy admin owner, a multisig in this case). This design concentrates the entire initial token supply in the hands of the owner multisig. While this might be an intended distribution model, it creates a single point of failure for the token's initial liquidity and distribution. A compromise of this multisig would give an attacker control over the entire initial supply. This impacts 7.4 Economic and 7.5 Governance.

**Recommendation:** Evaluate if this level of centralization for the initial supply is appropriate for the project's long-term decentralization goals. Consider distributing the initial supply across multiple secure wallets, vesting contracts, or a more decentralized distribution mechanism to mitigate the risk associated with a single large holder.


### `M-02` — Operational Risk from Owner-Controlled Gas Configuration  *(Severity: Medium · Status: Unresolved)*

The `setDestinationGas` function in `GasRouter` allows the `owner` to configure the gas limits for cross-chain messages to different destination domains. If these gas limits are set incorrectly (e.g., too low), cross-chain transactions might consistently fail, leading to operational disruptions, stuck funds, or a poor user experience. While this does not directly lead to fund loss through a vulnerability, it can significantly impact the protocol's reliability and usability. This impacts 7.4 Economic and 7.8 Operations.

**Recommendation:** Implement robust monitoring for cross-chain transaction failures related to gas limits. Consider adding a mechanism for users or a decentralized oracle to propose or vote on gas settings, or at least a public dashboard to track current settings and their impact. Ensure the owner has clear operational procedures for setting and updating these values.


### `L-01` — Immutable Decimals Limit Future Flexibility  *(Severity: Low · Status: Unresolved)*

The `_decimals` variable is declared as `immutable` in the `HypERC20` constructor. This means the token's decimal precision is permanently fixed at deployment of the implementation contract and cannot be altered through upgrades. While this is a common and often desirable characteristic for ERC-20 tokens to maintain consistency, it removes any potential flexibility for future protocol changes that might benefit from adjusting the decimal precision. This impacts 7.7 Upgrades.

**Recommendation:** Acknowledge this design choice. Ensure that the chosen decimal value is robust and suitable for all foreseeable future use cases of the token, as it cannot be changed.


### `I-01` — High Reliance on External Interchain Components  *(Severity: Informational · Status: Unresolved)*

The `HypERC20` contract, as an interchain token, heavily relies on the security and correct functioning of several external contracts: `IMailbox`, `IInterchainSecurityModule`, and `IPostDispatchHook`. The integrity of cross-chain transfers (minting and burning) is directly dependent on these components. Any vulnerability or misconfiguration in these external contracts could directly impact the security and economic stability of the `HypERC20` token. This impacts 7.6 External and 7.1 Architecture.

**Recommendation:** Ensure that all integrated external contracts (`IMailbox`, `IInterchainSecurityModule`, `IPostDispatchHook`) are thoroughly audited, well-maintained, and have robust security practices. Implement continuous monitoring for these dependencies and have a clear incident response plan in case of issues with any of them.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9a4a...642e`](https://bscscan.com/address/0x9a4a67721573f2c9209dfff972c52be4e3f6642e) |
| **Network** | BNB Chain |
| **Price** | $0.0117 |
| **24h Volume** | $251.4K |
| **Liquidity** | $172.6K |
| **Volume / Liquidity** | 1.5× |
| **Token Age** | 1y |
| **Top-10 Holders** | 95.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2263 buys / 2093 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x8943a75f4d0d1babea4cd77eabc323127714caa4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/goplus-security-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-14*
