---
token: STABLE
ticker: STABLE
network: bsc
risk_score: 54
status: high
date: 2026-07-24
---

# STABLE (STABLE) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 54/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/stable-bsc)

---

## Audit Summary

The audit focused on the `StableOFTUpgradeable` contract, which serves as an Omnichain Fungible Token (OFT) implementation utilizing LayerZero's upgradeable framework and OpenZeppelin's Ownable pattern. The contract is deployed behind an OptimizedTransparentUpgradeableProxy. The implementation itself is minimal, primarily inheriting functionality from well-audited libraries. Key findings include centralized control by the owner (mitigated by multisig), inherent dependency on LayerZero protocol security, and a theoretical, but mitigated, initialization front-running risk. Overall, the contract exhibits a robust architecture leveraging established patterns and libraries.

> **Final Recommendation:** It is recommended to maintain robust operational security for the multisig controlling both the proxy administration and the contract owner. This includes secure key management, strict internal procedures for transaction approval, and regular review of multisig signers. Additionally, continuous monitoring of LayerZero's official security announcements and updates is crucial, given the inherent dependency on the underlying bridging protocol. Ensure that the `initialize` function is called immediately and atomically with the proxy deployment to prevent any theoretical front-running windows.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical architecture (7.1) is sound, leveraging LayerZero's OFTUpgradeable and OpenZeppelin's OwnableUpgradeable, which are well-audited components. Code security (7.2) is enhanced by the… |
| **Governance / Economics** | 1/10 | High | The economic model (7.4) is based on the LayerZero OFT standard, implying cross-chain fungibility. Governance (7.5) is centralized around the contract owner, who can control critical token parameters… |
| **Upgrades** | 4/10 | Medium | The contract utilizes the Transparent Proxy pattern (7.7), a well-understood and secure upgrade mechanism. The `StableOFTUpgradeable` contract correctly employs `_disableInitializers()` in its… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 3-of-5 |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Centralized Control by Owner  *(Severity: Medium · Status: Unresolved)*

The `owner` of the `StableOFTUpgradeable` contract, set during initialization, holds significant administrative privileges inherited from `OFTUpgradeable` and `OwnableUpgradeable`. These privileges include pausing token transfers, setting trusted remote LayerZero endpoints, and transferring ownership. While the prefill data indicates the owner is a 3-of-5 multisig, which mitigates single-point-of-failure risk, the concentration of power remains.

**Recommendation:** Ensure robust operational security for the multisig, including secure key management, strict internal procedures for transaction approval, and regular review of multisig signers. Implement a clear emergency response plan for potential misuse of these privileges.


### `M-02` — Dependency on LayerZero Protocol Security  *(Severity: Medium · Status: Unresolved)*

The `StableOFTUpgradeable` contract is built upon the LayerZero protocol, specifically `OFTUpgradeable` and `ILayerZeroEndpointV2`. The security and functionality of this token are directly dependent on the integrity, correctness, and ongoing security of the underlying LayerZero infrastructure and smart contracts. Any vulnerability or misconfiguration within the LayerZero protocol could directly impact the cross-chain functionality and security of this token.

**Recommendation:** Continuously monitor LayerZero's official security announcements, audits, and updates. Ensure that the LayerZero endpoint address configured for this contract is the official and correct one for the target network. Consider implementing circuit breakers or emergency pause mechanisms if LayerZero experiences critical issues.


### `L-01` — Potential for Initialization Front-Running (Mitigated)  *(Severity: Low · Status: Unresolved)*

The `initialize` function, which sets the token's name, symbol, and crucially, the contract owner (`_delegate`), is protected by the `initializer` modifier. Additionally, the constructor calls `_disableInitializers()`. While these mechanisms prevent re-initialization, a theoretical front-running attack during the brief window between contract deployment and the first `initialize` call could allow an attacker to become the owner if the deployment process is not atomic or carefully managed. However, in practice, with standard proxy deployment scripts, the `initialize` call is typically executed immediately by the deployer, making this scenario highly improbable.

**Recommendation:** Ensure that the `initialize` function is called immediately and atomically with the proxy deployment, or by a trusted, whitelisted address, to prevent any window for front-running. This is a standard practice for proxy deployments.


### `I-01` — Minimal Custom Logic Reduces Attack Surface  *(Severity: Informational · Status: Unresolved)*

The `StableOFTUpgradeable` contract introduces very minimal custom logic, primarily serving as a thin wrapper around the well-audited `OFTUpgradeable` and `OwnableUpgradeable` contracts from LayerZero and OpenZeppelin, respectively. It does not add new state variables or complex business logic beyond initialization. This design choice significantly reduces the potential attack surface for vulnerabilities specific to this contract's implementation.

**Recommendation:** N/A (This is a strength of the current implementation and contributes positively to its security posture).

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x011e...075f`](https://bscscan.com/address/0x011ebe7d75e2c9d1e0bd0be0bef5c36f0a90075f) |
| **Network** | BNB Chain |
| **Price** | $0.03873 |
| **24h Volume** | $898.9K |
| **Liquidity** | $1.02M |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 7mo |
| **Top-10 Holders** | 95.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 7691 buys / 7418 sells |

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

## Frequently Asked Questions

### Is STABLE a scam?

Based on automated analysis, STABLE scores 64/100 (High Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is STABLE safe to buy?

Our scanner flagged a risk score of 64/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has STABLE been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xeaa6c7292ed954ca9dd72e769568d057b0525c9a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/stable-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-24*
