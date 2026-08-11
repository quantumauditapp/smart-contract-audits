---
token: elizaOS
ticker: ELIZAOS
network: bsc
risk_score: 61
status: high
date: 2026-08-11
---

# elizaOS (ELIZAOS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 61/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/elizaos-bsc)

---

## Audit Summary

The BurnMintERC20 contract implements a standard ERC20 token with additional minting and burning capabilities, leveraging OpenZeppelin's AccessControl for role-based permissions. The contract includes a maximum supply limit and a dedicated CCIP admin role. While the codebase demonstrates good adherence to established patterns and includes basic safety checks, a primary concern is the high degree of centralization inherent in the administrative roles, particularly the DEFAULT_ADMIN_ROLE, which controls critical functions like minting, burning, and the CCIP admin address. This centralization introduces a single point of failure and trust risk.

> **Final Recommendation:** To enhance the security posture, consider implementing a multi-signature wallet or a timelock for the `DEFAULT_ADMIN_ROLE` to manage critical functions such as granting/revoking roles and setting the `s_ccipAdmin`. This would introduce a delay or require multiple approvals for sensitive operations, significantly mitigating the risk of a single point of failure. Additionally, evaluate the necessity of an emergency pause mechanism to provide a safety net during unforeseen events or exploits.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract exhibits a robust architecture (7.1 Architecture) by inheriting from well-audited OpenZeppelin libraries (ERC20, AccessControl, ERC20Burnable), which significantly enhances code security… |
| **Governance / Economics** | 1/10 | High | The contract's economic model (7.4 Economic) includes a fixed `maxSupply` and controlled minting/burning, which provides predictability. Governance (7.5 Governance) is highly centralized, with the… |
| **Upgrades** | 6/10 | Medium | The contract is not designed as an upgradeable proxy (7.7 Upgrades) and does not implement any upgrade mechanisms. Therefore, there are no upgrade-related risks. Any changes to the contract's logic… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Centralized Control of Token Supply and Roles  *(Severity: High · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE` has absolute control over the token's supply by being able to grant and revoke `MINTER_ROLE` and `BURNER_ROLE` to any address. This centralization (7.3 Access Control, 7.5 Governance) means a single compromised private key or malicious administrator could manipulate the token supply, leading to severe economic consequences for the protocol and its users. The constructor grants this role to `msg.sender`.

**Recommendation:** Implement a multi-signature wallet or a timelock contract to control the `DEFAULT_ADMIN_ROLE`. This would require multiple approvals or introduce a delay for critical administrative actions, reducing the risk of a single point of failure and providing a window for intervention.


### `M-01` — Critical External Admin Role (`s_ccipAdmin`) Controlled by Single Admin  *(Severity: Medium · Status: Unresolved)*

The `s_ccipAdmin` address, which is likely crucial for Cross-Chain Interoperability Protocol (CCIP) operations (7.6 External), can be changed by the `DEFAULT_ADMIN_ROLE` via the `setCCIPAdmin` function. A compromise of the `DEFAULT_ADMIN_ROLE` could allow an attacker to redirect or disrupt CCIP-related functionalities, potentially impacting cross-chain asset transfers or data flows.

**Recommendation:** Similar to other critical roles, consider placing the `setCCIPAdmin` function under the control of a multi-signature wallet or a timelock. This would add an additional layer of security for managing external protocol integrations.


### `L-01` — Lack of Timelock or Multi-sig for Critical Operations  *(Severity: Low · Status: Unresolved)*

Critical administrative functions, such as `grantRole`, `revokeRole`, and `setCCIPAdmin`, are directly executable by the `DEFAULT_ADMIN_ROLE` without any time delay or multi-signature requirement (7.5 Governance, 7.8 Operations). This allows immediate execution of sensitive changes, increasing the risk of human error or rapid exploitation if the admin key is compromised.

**Recommendation:** Introduce a timelock mechanism for all critical administrative functions. This would enforce a delay between the initiation and execution of sensitive operations, providing a window for detection and potential mitigation of malicious or erroneous actions.


### `I-01` — No Emergency Pause Mechanism  *(Severity: Informational · Status: Unresolved)*

The contract lacks a mechanism to pause token transfers, minting, or burning in an emergency (7.2 Code Security, 7.8 Operations). In the event of a critical vulnerability, exploit, or unforeseen market event, the inability to halt operations could lead to significant and irreversible damage.

**Recommendation:** Consider integrating OpenZeppelin's `Pausable` contract or a similar custom pausing mechanism. This would allow authorized roles (e.g., `DEFAULT_ADMIN_ROLE` or a dedicated 'PAUSER_ROLE') to temporarily suspend critical functions during emergencies.


### `I-02` — Immutable `maxSupply` Parameter  *(Severity: Informational · Status: Unresolved)*

The `i_maxSupply` is set during construction and is immutable (7.4 Economic). While this provides a clear and predictable supply cap, it means the maximum supply cannot be adjusted in the future without deploying a new contract. This design choice might limit the protocol's flexibility for long-term evolution or unforeseen economic requirements.

**Recommendation:** This is a design decision. If future flexibility is desired, consider making `maxSupply` adjustable by a governance mechanism (e.g., `DEFAULT_ADMIN_ROLE` with a timelock), or acknowledge this immutability as a core feature of the token's economic policy.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xea17...2478`](https://bscscan.com/address/0xea17df5cf6d172224892b5477a16acb111182478) |
| **Network** | BNB Chain |
| **Price** | $0.0001897 |
| **24h Volume** | $48.6K |
| **Liquidity** | $172.8K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 8mo |
| **Top-10 Holders** | 85.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 482 buys / 510 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x56adadf82e3346eb8317628df5ce1f776f89014d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/elizaos-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
