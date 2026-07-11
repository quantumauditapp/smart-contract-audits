---
token: Re Protocol reUSD
ticker: REUSD
network: ethereum
risk_score: 98
status: critical
date: 2026-06-20
---

# Re Protocol reUSD (REUSD) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 98/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/re-protocol-reusd-eth)

---

## Audit Summary

This audit covers the OpenZeppelin ERC1967Proxy contract and its associated utility libraries. The contracts implement a standard EIP-1967 compliant upgradeable proxy, providing a robust foundation for upgradeable systems. While the core OpenZeppelin code is highly audited and secure, inherent risks associated with upgradeable proxies, such as centralized admin control, reliance on implementation contract security, and potential initialization vulnerabilities, necessitate careful consideration during deployment and operation.

> **Final Recommendation:** The OpenZeppelin ERC1967Proxy provides a secure and well-vetted foundation for upgradeable smart contracts. The primary risks stem from the inherent nature of upgradeable proxies, particularly the centralized control over upgrades and the dependency on the security of the implementation contract. It is crucial to implement robust access control for the admin key, thoroughly audit all implementation contracts, and carefully manage storage layouts during upgrades to prevent vulnerabilities.

For enhanced security and operational peace of mind, consider a Premium Deploy option that includes a multi-signature wallet for admin control, a time-lock mechanism for upgrade proposals, and continuous monitoring of the implementation contract for any potential vulnerabilities or unexpected behavior.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The technical architecture (7.1 Architecture) is based on OpenZeppelin's well-established EIP-1967 proxy standard, ensuring a robust and widely-adopted design. Code security (7.2 Code Security) is… |
| **Governance / Economics** | 1/10 | High | The proxy itself does not contain specific economic (7.4 Economic) or governance (7.5 Governance) logic; these aspects reside within the implementation contract. However, the upgrade mechanism… |
| **Upgrades** | 3/10 | High | The contract utilizes the EIP-1967 proxy pattern, allowing for future upgrades (7.7 Upgrades). The `ERC1967Utils` library provides functions like `upgradeToAndCall` and `changeAdmin`, which are… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ⚠️ Unverified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 72.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟡 2 Medium · ⚪ 1 Informational_

### `H-01` — Centralized Admin Control for Upgrades  *(Severity: High · Status: Unresolved)*

The `ERC1967Proxy` pattern, through `ERC1967Utils`, grants a single admin address full control over upgrading the proxy's implementation and changing the admin itself. This centralized control represents a single point of failure. If the admin key is compromised, an attacker could deploy a malicious implementation, leading to loss of funds or system compromise.

**Recommendation:** Implement a robust access control mechanism for the admin role. This should ideally involve a multi-signature wallet (e.g., Gnosis Safe) for the admin address. Additionally, consider integrating a time-lock contract to introduce a delay between proposing an upgrade and its execution, allowing time for review and potential intervention.


### `H-02` — Reliance on External Implementation Contract Security  *(Severity: High · Status: Unresolved)*

The `ERC1967Proxy` delegates all calls to an external implementation contract. The security and correctness of the entire system are entirely dependent on the security of this implementation contract, which was not provided for this audit. Any vulnerability (e.g., reentrancy, access control flaws, logic errors) in the implementation would directly affect the proxy and its users.

**Recommendation:** Thoroughly audit all implementation contracts before deployment and every time an upgrade is performed. Ensure that the implementation contract adheres to best security practices, is well-tested, and has undergone independent security reviews. Implement robust testing, including unit, integration, and fuzz testing.


### `M-01` — Potential Initialization Race Condition  *(Severity: Medium · Status: Unresolved)*

While the `ERC1967Proxy` constructor calls `upgradeToAndCall` with `_data` to initialize the implementation, a common vulnerability in proxy patterns arises if the implementation contract's `initialize` function is public and can be called directly on the implementation address *before* the proxy's constructor executes it. An attacker could front-run the initialization, gaining control of the implementation contract's state, which would then be reflected in the proxy.

**Recommendation:** Ensure that the implementation contract's `initialize` function can only be called once and is protected by an `initializer` modifier. For added safety, consider deploying the implementation contract with a disabled `initialize` function (e.g., by calling it in its own constructor) and then enabling it via a separate, restricted function call through the proxy, or by ensuring the proxy's constructor is the *only* way to call `initialize` initially.


### `M-02` — Storage Collision Risk During Upgrades  *(Severity: Medium · Status: Unresolved)*

Although EIP-1967 slots prevent collisions between proxy-specific storage and implementation storage, changes to the implementation contract's storage layout across upgrades can lead to storage collisions. If new state variables are added, removed, or reordered without careful planning, they might overwrite existing data from previous versions, leading to data corruption, unexpected behavior, or loss of funds.

**Recommendation:** Adhere strictly to upgrade-safe storage layout principles. New state variables should only be appended to the end of the contract's storage. Never reorder or change the type of existing state variables. Utilize tools like OpenZeppelin's 'Upgrades Plugins' for Hardhat or Foundry to detect potential storage layout incompatibilities during development and before deployment.


### `I-01` — Robust `msg.value` Handling in Upgrades  *(Severity: Informational · Status: Resolved)*

The `ERC1967Utils` library includes the `_checkNonPayable()` function, which is called when `upgradeToAndCall` or `upgradeBeaconToAndCall` is invoked without any `data`. This function explicitly reverts if `msg.value > 0` in such scenarios. This prevents Ether from being accidentally sent to the proxy contract and becoming permanently locked if there's no delegate call to forward it.

**Recommendation:** No action required. This is a positive security feature that prevents accidental loss of funds.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5086...0c72`](https://etherscan.io/address/0x5086bf358635b81d8c47c66d1c8b9e567db70c72) |
| **Network** | Ethereum |
| **Price** | $1.2300 |
| **24h Volume** | $283.4K |
| **Liquidity** | $1.53M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 10mo |
| **Top-10 Holders** | 98.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 15 buys / 14 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Frequently Asked Questions

### Is Re Protocol reUSD a scam?

While the data does not definitively confirm Re Protocol reUSD as a scam, several red flags warrant caution. The contract is verified, and ownership is renounced, which are positive indicators. However, the extreme token centralization, with 98.7% held by the top 10 wallets, coupled with unlocked liquidity, presents significant risks often associated with potential malicious activities or market instability. Investors should exercise due diligence.

### Is Re Protocol reUSD safe to buy?

Based on the provided data, Re Protocol reUSD carries a high-risk score of 51/100, suggesting it is not safe for risk-averse investors. Key concerns include the top 10 holders controlling nearly all supply (98.7%), posing a significant centralization risk and potential for market manipulation. Furthermore, the absence of locked liquidity means funds can be withdrawn, increasing volatility and potential for sudden market impact.

### Has Re Protocol reUSD been audited?

The Re Protocol reUSD contract is verified, meaning its code is public and matches the deployed version on the blockchain, providing transparency. However, verification differs from a full security audit performed by third-party experts. The available data does not indicate whether such a comprehensive audit, which assesses code for vulnerabilities, has been completed for the REUSD contract.

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x5c2ab69eb2bf12a2f4572d178687bd4660512972)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/re-protocol-reusd-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-20*
