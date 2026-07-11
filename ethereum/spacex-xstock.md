---
token: SpaceX xStock
ticker: SPCXX
network: ethereum
risk_score: 100
status: critical
date: 2026-06-16
---

# SpaceX xStock (SPCXX) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/spacex-xstock-eth)

---

## Audit Summary

This audit was conducted on a contract identified as a proxy for an ERC20 token. The primary and most critical finding is the complete lack of verified source code for both the proxy and its implementation contract. While snippets of OpenZeppelin upgradeable libraries were provided, the custom logic and the full deployment configuration remain unknown. This severely limits the scope and effectiveness of the audit, rendering a comprehensive security assessment impossible. The unverified nature of the deployed code introduces critical trust and security risks.

> **Final Recommendation:** Given the critical finding of unverified and missing source code for both the proxy and its implementation, a comprehensive security assessment is impossible. It is strongly recommended that the project team immediately verify the full source code on the blockchain for both contracts. Without this, users should exercise extreme caution as the deployed code's functionality and security cannot be confirmed. 

For future deployments, consider using a Premium Deploy service to ensure all contracts are verified, immutable, and follow best practices for transparency and security from the outset, allowing for full auditability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 1/10 | High | The contract appears to utilize well-audited OpenZeppelin upgradeable libraries for ERC20 and Ownable functionalities, which generally provide robust and secure foundations (7.2 Code Security). These  |
| **Governance / Economics** | 1/10 | High | The `OwnableUpgradeable` pattern provides a clear, single point of administrative control, allowing for efficient management of critical functions (7.3 Access Control). This centralized control, witho |
| **Upgrades** | 1/10 | High | The use of OpenZeppelin's `Initializable` and `__gap` patterns suggests an intention for proper upgradeability, which is a strong architectural choice (7.7 Upgrades). Despite this, the proxy contract  |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 2-of-3 |
| **Implementation** | ⚠️ Unverified source |
| **Upgrades (30d)** | ⚠️ 1 |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 39.5% |
| **Top-3 Unlocked** | ⚠️ 80.3% |

## Security Findings

_🔴 1 Critical · 🟠 3 High · 🟡 1 Medium · ⚪ 1 Informational_

### `C-01` — Unverified Contract & Missing Source Code  *(Severity: Critical · Status: Unresolved)*

The contract at the provided address (0x68fa48b1c2fe52b3d776e1953e0e782b5044ce28) is identified as a proxy, and its implementation (0xd865ce1b07540b5ede20e8298f48da69770fe22e) is also unverified. Only snippets of OpenZeppelin library code were provided for analysis. This means the actual deployed bytecode for both the proxy and its implementation cannot be correlated with any public source code. Without verified source code, it is impossible to conduct a meaningful security audit, understand the contract's true functionality, or confirm its safety. This poses an existential risk to users as the contract could contain malicious logic, backdoors, or critical vulnerabilities that are entirely…

**Recommendation:** Immediately verify the full and accurate source code for both the proxy contract and its implementation contract on the blockchain (e.g., Etherscan). This is a fundamental requirement for transparency and trust in smart contracts. Until verification is complete, users should be warned about the unverified nature of the contract.


### `H-01` — Centralized Control (Owner Privileges)  *(Severity: High · Status: Unresolved)*

The contract utilizes the `OwnableUpgradeable` pattern, granting a single external address (the owner) exclusive control over critical functions. While this allows for efficient administration, it introduces a single point of failure. If the owner's private key is compromised, or if the owner acts maliciously, the entire system could be jeopardized, leading to potential loss of funds or unauthorized modifications.

**Recommendation:** Consider implementing a multi-signature wallet (e.g., Gnosis Safe) for the owner address to enhance security and distribute control. For long-term decentralization, explore transitioning to a community-governed model or time-locked functions for highly sensitive operations.


### `H-02` — Unknown Implementation Logic and Tokenomics  *(Severity: High · Status: Unresolved)*

Only standard OpenZeppelin ERC20 and Ownable library snippets were provided. The specific custom logic of the ERC20 token's implementation (e.g., minting, burning mechanisms, pausing, fee structures, special transfer conditions) and its overall economic model (tokenomics) are entirely unknown. This lack of visibility means potential vulnerabilities such as reentrancy, integer overflows/underflows in custom calculations, or economic exploits (e.g., inflation attacks, unfair distribution) cannot be assessed.

**Recommendation:** Provide the complete and verified source code for the ERC20 implementation contract. A full audit of the custom logic and a detailed review of the tokenomics are essential to identify and mitigate potential vulnerabilities.


### `H-03` — Upgradeability Risks Due to Unverified Proxy and Implementation  *(Severity: High · Status: Unresolved)*

While the use of OpenZeppelin's `Initializable` and `__gap` patterns suggests an intention for proper upgradeability, the proxy contract itself and its implementation are unverified. This means the specific proxy pattern (e.g., UUPS, Transparent) and the mechanisms for authorizing and executing upgrades cannot be confirmed. An unverified proxy could have a flawed upgrade mechanism, or the implementation could be swapped to malicious code without public scrutiny, leading to a complete compromise of the token.

**Recommendation:** Verify the full source code for both the proxy contract and its implementation. Clearly document the chosen proxy pattern and the upgrade process, including any `_authorizeUpgrade` logic for UUPS proxies. Ensure that upgrade permissions are secured, ideally via a multi-sig wallet.


### `M-01` — Potential for Re-initialization of Implementation Contract  *(Severity: Medium · Status: Unresolved)*

The `Initializable` pattern is used to protect initializer functions from being called multiple times. However, if the implementation contract's `initialize` function is not properly protected (e.g., by a constructor marking it initialized) and is directly callable on the implementation contract itself (not through the proxy), an attacker could call `initialize` on the implementation directly. This could potentially seize ownership or reconfigure the implementation, which might affect future upgrades or even the proxy if storage slots are manipulated.

**Recommendation:** Ensure that the implementation contract's `initialize` function is either called once during deployment (e.g., via `ERC1967Proxy` constructor `_data`) or that the implementation contract's constructor explicitly calls `initializer()` to mark it as initialized, preventing direct calls to `initialize` on the implementation itself. Verify this protection is in place once the full source code is available.


### `I-01` — Dependency on OpenZeppelin Libraries  *(Severity: Informational · Status: Unresolved)*

The contract relies heavily on OpenZeppelin Contracts Upgradeable libraries (OwnableUpgradeable, Initializable, ERC20Upgradeable). While these libraries are widely used and well-audited, any future vulnerabilities discovered within these external dependencies could potentially affect this contract.

**Recommendation:** Stay informed about security updates and advisories from OpenZeppelin. Regularly review the versions of the libraries used and consider upgrading to newer, patched versions if critical vulnerabilities are identified.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x68fa...ce28`](https://etherscan.io/address/0x68fa48b1c2fe52b3d776e1953e0e782b5044ce28) |
| **Network** | Ethereum |
| **Price** | $215.6200 |
| **24h Volume** | $45.8K |
| **Liquidity** | $37.0K |
| **Volume / Liquidity** | 1.2× |
| **Token Age** | 3d |
| **Top-10 Holders** | 99.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 124 buys / 142 sells |

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

### Is SpaceX xStock a scam?

Labeling SpaceX xStock as an outright scam based solely on provided data is not definitive. While the contract is verified and ownership renounced, significantly concerning factors exist. 99.9% of the supply is controlled by the top 10 holders, indicating extreme centralization, and liquidity is not locked. These characteristics create a high potential for price manipulation or a liquidity pull. The assigned risk score of 60/100 reflects these considerable dangers, urging extreme vigilance from investors.

### Is SpaceX xStock safe to buy?

SpaceX xStock (SPCXX) carries significant risks and is not considered safe to buy based on current metrics. A critical concern is that 99.9% of the token supply is concentrated within the top 10 holders, making it highly susceptible to manipulation. Furthermore, the absence of locked liquidity means that the existing funds can be withdrawn at any time, posing a direct rug pull risk. Its overall risk score of 60/100 strongly indicates a hazardous investment profile.

### Has SpaceX xStock been audited?

The SpaceX xStock (SPCXX) smart contract is verified, making its code public and reviewable for transparency. However, 'contract verified' differs from a comprehensive security audit conducted by an independent firm. An audit involves a deeper, expert analysis to proactively identify vulnerabilities. The provided data does not confirm that such a formal audit has been performed for SPCXX.

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xba8e6701ead6b06a57fc83094b0b2d25fb504d6394f6b13a17de583d50c1ebc0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/spacex-xstock-eth)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-16*
