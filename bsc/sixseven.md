---
token: SIXSEVEN
ticker: 67
network: bsc
risk_score: 52
status: high
date: 2026-08-20
---

# SIXSEVEN (67) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 52/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sixseven-bsc)

---

## Audit Summary

The SixSevenOFT contract is an upgradeable Omnichain Fungible Token (OFT) implementation built on LayerZero V2. It utilizes a TransparentUpgradeableProxy pattern with a multisig as the proxy admin. The contract inherits standard OFT functionality, allowing cross-chain token transfers. While the core logic is based on audited LayerZero libraries and OpenZeppelin's upgradeable patterns, the operational security heavily depends on the correct configuration and management by the contract owner. Centralized control by the owner over critical LayerZero parameters and upgradeability presents a medium risk.

> **Final Recommendation:** It is crucial to ensure that the multisig owner maintains robust security practices, including secure key management and a well-defined process for approving transactions, especially those related to LayerZero configuration and contract upgrades. Regular monitoring of LayerZero's official channels for security announcements and updates is also recommended to address any potential vulnerabilities in the underlying protocol. Additionally, consider implementing a timelock for critical administrative actions to provide a delay for review and potential intervention.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract is a standard LayerZero OFT implementation, inheriting robust cross-chain token logic. It uses a recent Solidity compiler version (0.8.22) which includes default overflow/underflow… |
| **Governance / Economics** | 5/10 | Medium | The contract employs an `Ownable` pattern, granting significant control over critical LayerZero configurations and upgradeability to a single owner address (7.3 Access Control). While the owner is a… |
| **Upgrades** | 2/10 | High | The contract utilizes the Transparent Upgradeable Proxy pattern, a well-established and audited mechanism for upgradeability. The proxy's admin is controlled by a multisig, enhancing security for… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 1-of-1 |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Centralized Control by Owner  *(Severity: Medium · Status: Unresolved)*

The contract uses the `Ownable` pattern, granting significant administrative control to a single owner address (a multisig in this case). This owner has the power to configure critical LayerZero parameters (e.g., `setTrustedRemote`, `setMinDstGas`), set delegates, and potentially upgrade the contract. While a multisig mitigates some risk, it still represents a centralized point of failure or potential misuse if the multisig's security is compromised or its members act maliciously (7.3 Access Control, 7.5 Governance).

**Recommendation:** Consider implementing a timelock for critical administrative functions to introduce a delay before changes take effect, allowing for community review or emergency intervention. Ensure the multisig governance process is robust, transparent, and follows best practices for key management and transaction approval.


### `M-02` — Reliance on LayerZero Configuration and Operational Risks  *(Severity: Medium · Status: Unresolved)*

The contract's core functionality as an Omnichain Fungible Token (OFT) heavily relies on the correct and ongoing configuration of LayerZero parameters by the contract owner. Misconfiguration of parameters such as `setTrustedRemote`, `setMinDstGas`, or `setFeeManager` could lead to funds being stuck, lost during cross-chain transfers, or unexpected fee structures (7.6 External, 7.8 Operations). The security and reliability of the LayerZero protocol itself are also external dependencies.

**Recommendation:** Implement rigorous testing and verification procedures for all LayerZero parameter changes. Establish clear operational guidelines for the owner to manage these configurations. Monitor LayerZero's official channels for any security advisories or updates to the protocol. Consider integrating monitoring tools to detect unusual activity or misconfigurations.


### `L-01` — Potential Misconfiguration of Initial Owner  *(Severity: Low · Status: Unresolved)*

The `initialize` function, which sets the token's name, symbol, and the initial owner via `__Ownable_init(_delegate)`, is public. While protected by the `initializer` modifier to prevent re-initialization, if the `_delegate` parameter is incorrectly specified during the initial deployment and initialization of the proxy, the contract's ownership could be assigned to an unintended address (7.3 Access Control). Given the contract is live, this is primarily a deployment-time risk.

**Recommendation:** Ensure that the `_delegate` address passed to the `initialize` function during proxy deployment is thoroughly verified and corresponds to the intended multisig owner. Implement a robust deployment checklist to prevent such misconfigurations.


### `I-01` — Hardcoded Decimals  *(Severity: Informational · Status: Unresolved)*

The `decimals()` and `sharedDecimals()` functions are hardcoded to return `9`. This is a design decision for the token (7.4 Economic). Any future requirement to change the token's decimal precision would necessitate a contract upgrade, which might be a complex process.

**Recommendation:** No direct action is required if this is the intended design. If flexibility in decimal precision is ever anticipated, consider a design that allows the owner to update this value, though this introduces additional complexity and potential risks.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe7e5...c452`](https://bscscan.com/address/0xe7e569417d315ef260778c09d289d7966213c452) |
| **Network** | BNB Chain |
| **Price** | $0.03205 |
| **24h Volume** | $165.8K |
| **Liquidity** | $147.6K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 26d |
| **Top-10 Holders** | 12.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1126 buys / 1077 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xffe68427490247f4151a7e8ef744c59f4fc98a13)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sixseven-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-20*
