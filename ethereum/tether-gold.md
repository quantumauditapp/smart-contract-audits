---
token: Tether Gold
ticker: XAUT
network: ethereum
risk_score: 58
status: high
date: 2026-07-27
---

# Tether Gold (XAUT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 58/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tether-gold-eth)

---

## Audit Summary

The TetherToken contract implements an upgradeable ERC-20 token with a centralized ownership model, including minting, burning, and a blocked list functionality. The contract utilizes well-audited OpenZeppelin Upgradeable libraries for its core functionalities and upgradeability. While the technical implementation is robust, the high degree of centralization in control over token supply, user funds, and contract upgrades introduces significant governance and economic risks inherent to its design as a stablecoin.

> **Final Recommendation:** To enhance the security posture, consider implementing a multi-signature wallet or a time-locked governance mechanism for the owner address, especially for critical functions such as minting, burning, and managing the blocked list. This would distribute control and introduce a delay for sensitive operations, mitigating the risk associated with a single point of failure. Additionally, ensure comprehensive documentation is available to users and integrators, clearly outlining the capabilities and limitations of the blocked list functionality and the owner's powers.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical implementation of the TetherToken contract demonstrates good practices, leveraging battle-tested OpenZeppelin Upgradeable libraries for ERC-20, Ownable, and Initializable patterns (7.2… |
| **Governance / Economics** | 4/10 | Medium | The contract exhibits a high degree of centralization, with a single owner controlling critical functions (7.3 Access Control, 7.5 Governance). The owner has the sole ability to `mint` new tokens… |
| **Upgrades** | 1/10 | High | The contract is designed for upgradeability using the TransparentUpgradeableProxy pattern with an OpenZeppelin ProxyAdmin (7.7 Upgrades). The implementation correctly uses `Initializable` and `__gap`… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Other-Contract |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 13.9% |
| **Top-3 Unlocked** | 36.0% |

## Security Findings

_🟠 1 High · 🟢 1 Low · ⚪ 3 Informational_

### `H-01` — Centralized Control over Token Supply and User Funds  *(Severity: High · Status: Unresolved)*

The `TetherToken` contract grants the `owner` address extensive control over the token supply and user funds. The `mint` function allows the owner to create new tokens, and the `redeem` function allows the owner to burn tokens from their own balance. More critically, the `destroyBlockedFunds` function enables the owner to burn the entire balance of any address on the blocked list. This level of centralization introduces significant counterparty risk, as a compromised or malicious owner could manipulate the supply or seize user assets.

**Recommendation:** While this centralization is an inherent design choice for stablecoins like USDT, it's crucial that the owner key management is robust. Consider implementing a multi-signature wallet or a time-locked governance mechanism for critical functions like `mint`, `redeem`, `addToBlockedList`, `removeFromBlockedList`, and `destroyBlockedFunds` to mitigate the risk of a single point of failure.


### `L-01` — Centralized Upgradeability Control  *(Severity: Low · Status: Unresolved)*

The contract uses a TransparentUpgradeableProxy pattern with an OpenZeppelin ProxyAdmin. The owner of the `TetherToken` contract (via `OwnableUpgradeable`) is the same address (`0xc6cde7c39eb2f0f0095f41570af89efc2c1ea828`) that controls the ProxyAdmin, which is responsible for upgrading the implementation contract. This means a single entity has full control over both the operational logic and the upgradeability of the token.

**Recommendation:** While this is a common setup, for high-value or critical infrastructure contracts, it is recommended to separate the upgradeability control from the operational control. This could involve using a different multisig or a more decentralized governance mechanism for the ProxyAdmin owner.


### `I-01` — Unused `isTrusted` Variable  *(Severity: Informational · Status: Resolved)*

The `isTrusted` mapping is declared but not used anywhere in the `TetherToken` contract logic. The comment explicitly states it is 'retained to preserve storage slots across upgrades.'

**Recommendation:** This is a good practice for upgradeable contracts to prevent storage collisions in future upgrades. No action is required, but ensure clear documentation of such design decisions.


### `I-02` — Reliance on External OpenZeppelin Libraries  *(Severity: Informational · Status: Resolved)*

The contract heavily relies on OpenZeppelin Contracts Upgradeable for core functionalities like ERC-20, Ownable, and Initializable patterns.

**Recommendation:** OpenZeppelin libraries are widely audited and considered industry-standard. Ensure that the specific versions used (`0.8.4` compatible versions) are free from known vulnerabilities. Regular monitoring of OpenZeppelin security advisories is recommended.


### `I-03` — Blocked List Functionality and Scope  *(Severity: Informational · Status: Resolved)*

The `WithBlockedList` contract and its integration into `TetherToken` implement a mechanism to block specific addresses. The `onlyNotBlocked` modifier prevents blocked addresses from initiating `transfer`, `transferFrom`, and `multiTransfer` operations. Additionally, `transferFrom` explicitly prevents transfers from a blocked `_sender`. However, the design allows tokens to be transferred *to* a blocked address by an unblocked sender. The owner also has the ability to `destroyBlockedFunds` from any blocked address. This design implies the blocked list primarily restricts outbound transactions from blocked users and allows for asset seizure, rather than completely isolating blocked accounts f…

**Recommendation:** Document this specific behavior clearly for users and integrators, especially regarding the ability to send funds *to* blocked addresses and the owner's power to destroy them. This ensures transparency about the system's censorship capabilities.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6874...2f38`](https://etherscan.io/address/0x68749665ff8d2d112fa859aa293f07a622782f38) |
| **Network** | Ethereum |
| **Price** | $4,087.5500 |
| **24h Volume** | $4.28M |
| **Liquidity** | $6.12M |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 9mo |
| **Top-10 Holders** | 56.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 273 buys / 442 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Frequently Asked Questions

### Is Tether Gold a scam?

Based on automated analysis, Tether Gold scores 65/100 (High Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is Tether Gold safe to buy?

Our scanner flagged a risk score of 65/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has Tether Gold been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xc756bba710d45647715079ce50aa16aab36ded42)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tether-gold-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-27*
