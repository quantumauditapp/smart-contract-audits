---
token: Main Street USD
ticker: MSUSD
network: ethereum
risk_score: 72
status: critical
date: 2026-06-21
---

# Main Street USD (MSUSD) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 72/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/main-street-usd-eth)

---

## Audit Summary

This audit covers an ERC1967Proxy contract, which is a standard UUPS proxy implementation from OpenZeppelin. While the proxy contract itself is well-vetted, the critical finding is that its associated implementation contract (0x96271bea7a9c4b8edd6c3a05e548f05f157ada46) is unverified on-chain. This prevents any meaningful security assessment of the protocol's core logic, access control, economic model, and upgrade mechanisms, introducing severe risks.

> **Final Recommendation:** The most critical recommendation is to immediately verify the source code of the implementation contract (0x96271bea7a9c4b8edd6c3a05e548f05f157ada46) on the blockchain. Without this, a full security audit cannot be performed, and the system's overall security posture remains unknown and highly risky. Once verified, a comprehensive audit of the implementation contract should be conducted to identify and mitigate any vulnerabilities related to its core logic, access control, economic model, and upgrade authorization mechanisms.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 3/10 | High | The proxy contract (7.1 Architecture) utilizes the battle-tested OpenZeppelin ERC1967Proxy, which is a strong foundation for upgradeability. However, the primary technical risk stems from the… |
| **Governance / Economics** | 1/10 | High | The governance and economic models (7.4 Economic, 7.5 Governance) of the protocol are entirely dependent on the logic within the implementation contract. Since the implementation contract is… |
| **Upgrades** | 1/10 | High | The contract employs the UUPS proxy pattern (7.7 Upgrades), which is a secure and widely adopted upgrade mechanism. The `ERC1967Proxy` correctly delegates upgrade authorization to the implementation… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 2 High · ⚪ 3 Informational_

### `C-01` — Unverified Implementation Contract  *(Severity: Critical · Status: Unresolved)*

The proxy contract at 0x4ba01f22827018b4772cd326c7627fb4956a7c00 delegates calls to an implementation contract at 0x96271bea7a9c4b8edd6c3a05e548f05f157ada46. However, the source code for this implementation contract is not verified on the blockchain. This prevents any security analysis of the actual business logic, access control, economic model, and upgrade authorization, making the entire system's security posture unknown and highly vulnerable to undiscovered issues.

**Recommendation:** Immediately verify the source code of the implementation contract (0x96271bea7a9c4b8edd6c3a05e548f05f157ada46) on the blockchain. Once verified, a full security audit of the implementation contract must be performed to identify and address any vulnerabilities.


### `H-01` — Undeterminable Access Control and Economic Logic  *(Severity: High · Status: Unresolved)*

Due to the unverified nature of the implementation contract, it is impossible to assess the access control mechanisms (7.3 Access Control) governing critical functions, privileged roles, or the economic logic (7.4 Economic) of the protocol. This includes evaluating potential attack vectors like unauthorized fund transfers, manipulation of economic parameters, or reentrancy vulnerabilities within the core logic. The lack of visibility into these critical components poses a high risk to the integrity and security of the protocol.

**Recommendation:** Verify the implementation contract's source code and then conduct a thorough audit of its access control mechanisms, role-based permissions, and economic logic to ensure they are robust and secure against common attack patterns.


### `H-02` — Upgrade Mechanism Security Risk  *(Severity: High · Status: Unresolved)*

While the proxy uses the UUPS pattern, which is generally secure, the actual authorization logic for upgrades resides within the unverified implementation contract. This means the conditions under which the contract can be upgraded, who has the authority to initiate upgrades, and any associated timelocks or governance procedures (7.7 Upgrades) cannot be verified. A compromised or malicious implementation could allow unauthorized upgrades, leading to a complete loss of control over the protocol or introduction of backdoors.

**Recommendation:** After verifying the implementation contract, meticulously audit the `_authorizeUpgrade` function and any related upgrade governance mechanisms within the implementation. Ensure that upgrade permissions are tightly controlled, ideally through a multi-signature wallet or a robust governance process with appropriate timelocks.


### `I-01` — Use of Standard OpenZeppelin ERC1967Proxy  *(Severity: Informational · Status: Resolved)*

The contract utilizes the `ERC1967Proxy` from OpenZeppelin Contracts (v5.0.0). This is a well-audited and widely adopted standard for upgradeable proxies, providing a solid and secure foundation for the proxy layer.

**Recommendation:** Continue to rely on well-vetted libraries like OpenZeppelin for core infrastructure components.


### `I-02` — UUPS Proxy Pattern in Use  *(Severity: Informational · Status: Resolved)*

The contract implements the UUPS (Universal Upgradeable Proxy Standard) pattern, where the upgrade logic resides within the implementation contract itself, rather than a separate admin contract. This design choice offers flexibility and can simplify the upgrade process.

**Recommendation:** Ensure that the upgrade logic within the implementation contract is robust, secure, and adheres to best practices for authorization and safety checks.


### `I-03` — Constructor Initialization with `upgradeToAndCall`  *(Severity: Informational · Status: Resolved)*

The proxy's constructor uses `ERC1967Utils.upgradeToAndCall(implementation, _data)` to initialize the implementation address and optionally call an initialization function on the implementation. This is a standard and secure way to deploy and initialize UUPS proxies.

**Recommendation:** Ensure that the initialization function in the implementation contract is properly secured against re-initialization attacks.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4ba0...7c00`](https://etherscan.io/address/0x4ba01f22827018b4772cd326c7627fb4956a7c00) |
| **Network** | Ethereum |
| **Price** | $0.3235 |
| **24h Volume** | $738 |
| **Liquidity** | $299.7K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 1y |
| **Top-10 Holders** | 98.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1155 buys / 990 sells |

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

### Is Main Street USD a scam?

Based on available data, Main Street USD exhibits high-risk characteristics, especially its highly concentrated token distribution where 99.2% is held by the top 10 wallets, and unlocked liquidity. While the contract is verified and ownership renounced, these don't mitigate the direct market manipulation or rug pull potential from concentrated holders and unprotected liquidity. It requires careful consideration.

### Is Main Street USD safe to buy?

Investing in Main Street USD carries significant risks. The extreme centralization, with 99.2% of tokens held by the top 10 addresses, makes it vulnerable to price manipulation. Additionally, liquidity is not locked, posing a risk of liquidity withdrawal (rug pull) that could leave investors unable to sell. These factors contribute to its high-risk score.

### Has Main Street USD been audited?

The Main Street USD contract has been verified on Ethereum, meaning its code is publicly visible and matches the deployed bytecode. However, "contract verified" is not the same as a comprehensive security audit by an independent third party. An audit typically involves deeper code analysis for vulnerabilities beyond just transparency.

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x111ce2a60c30f6058a57d0dbae1a39a42d998826-0x4ba01f22827018b4772cd326c7627fb4956a7c00-0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/main-street-usd-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-21*
