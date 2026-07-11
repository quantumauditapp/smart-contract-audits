---
token: Nockchain
ticker: NOCK
network: base
risk_score: 56
status: high
date: 2026-06-10
---

# Nockchain (NOCK) — Smart Contract Security Analysis | Base

> **Risk Score: 56/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/nockchain-base)

---

## Audit Summary

The Nock contract is an ERC-20 token designed to represent wrapped Nockchain assets, allowing users to burn tokens for withdrawals and enabling a designated MessageInbox to mint new tokens. The contract leverages OpenZeppelin's battle-tested ERC20 and Ownable implementations, contributing to a solid foundation for standard token operations. However, the centralized control over the minting authority via the `owner` role, coupled with the contract's explicit non-upgradeability and lack of an emergency pause mechanism, introduces significant operational and governance risks. The non-standard `decimals` value (16) also requires careful consideration for ecosystem integrations.

> **Final Recommendation:** The Nock contract provides a functional ERC-20 token with clear minting and burning mechanisms. However, the high degree of centralization around the `owner` for minting authority, combined with the contract's non-upgradeable nature and lack of a pause function, presents substantial risks. It is strongly recommended to implement a multi-signature wallet for the `owner` role to mitigate the risk of a single point of failure. Additionally, while immutability is a design choice, the lack of an emergency pause should be carefully considered against the potential impact of unforeseen vulnerabilities. For enhanced security and operational flexibility, a Premium Deploy option with a robust governance model and upgradeability features should be explored for future iterations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The Nock contract demonstrates good code quality, utilizing OpenZeppelin's ERC20 and Ownable libraries, which are well-audited and secure (7.2 Code Security). The logic for minting and burning is… |
| **Governance / Economics** | 2/10 | High | The `owner` role holds significant power, specifically the ability to update the `inbox` address, which is the sole entity authorized to mint new tokens (7.3 Access Control, 7.5 Governance). This… |
| **Upgrades** | 5/10 | Medium | The Nock contract is explicitly designed as non-upgradeable, as stated in its NatSpec documentation (7.7 Upgrades). This immutability means that any discovered vulnerability, bug, or desired feature… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 46.0% |
| **Top-3 Unlocked** | 75.2% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control of Minting Authority  *(Severity: High · Status: Unresolved)*

The `owner` of the Nock contract has the exclusive privilege to call `updateInbox(address _newInbox)`, which sets the address of the `inbox` contract. The `inbox` contract is the only entity authorized to call the `mint(address to, uint256 amount)` function, allowing it to create new Nock tokens. A compromise of the `owner`'s private key would allow an attacker to set a malicious `inbox` contract, which could then mint an arbitrary amount of tokens, leading to a complete devaluation of the Nock token supply. This represents a single point of failure for the token's supply control.

**Recommendation:** Implement a multi-signature wallet (e.g., Gnosis Safe) for the `owner` role to control the `updateInbox` function. This would require multiple independent approvals for critical administrative actions, significantly reducing the risk associated with a single compromised key. Alternatively, consider a time-locked governance mechanism for such critical changes.


### `M-01` — Non-Standard ERC-20 Decimals  *(Severity: Medium · Status: Unresolved)*

The `decimals()` function in the Nock contract returns `16`, deviating from the common ERC-20 standard of `18`. While the contract explicitly states this is for 'Nockchain alignment', this non-standard value can lead to integration issues with various DeFi protocols, exchanges, wallets, and block explorers that often assume 18 decimals by default. Incorrect handling of decimals by external systems could result in users seeing incorrect balances or performing transactions with unintended amounts.

**Recommendation:** Ensure all documentation, front-end interfaces, and integration guides prominently highlight that Nock tokens use 16 decimals. Proactively communicate this to any third-party integrators. Consider adding a check or warning in any associated dApp to prevent user errors.


### `M-02` — Immutability and Lack of Emergency Pause Mechanism  *(Severity: Medium · Status: Unresolved)*

The contract is explicitly designed to be non-upgradeable, as stated in its NatSpec documentation. Furthermore, it lacks an emergency pause mechanism. This combination means that in the event of a critical bug, security vulnerability, or unforeseen economic exploit, there is no way to halt token transfers or minting/burning operations. Remediation would require deploying an entirely new contract and migrating all users, which is a complex, costly, and potentially disruptive process.

**Recommendation:** While immutability is a design choice, consider the trade-offs. If immutability is paramount, ensure extensive testing and formal verification are performed. If operational flexibility is desired, explore implementing a robust upgradeable proxy pattern (e.g., UUPS) and/or an `onlyOwner` or governance-controlled `pause()` function to provide an emergency stop-gap in critical situations.


### `L-01` — Dependency on External `MessageInbox` Security and Liveness  *(Severity: Low · Status: Unresolved)*

The `burn` function makes an external call to `IMessageInbox(inbox).notifyBurn()`. While this call occurs after the internal `_burn` operation, mitigating reentrancy risks for the Nock contract itself, the overall system's security and liveness depend on the `inbox` contract. If the `inbox` contract is malicious, buggy, or becomes unresponsive (e.g., due to a self-destruct or permanent revert), `burn` transactions would revert, impacting user withdrawals. The `owner` can update the `inbox` address, which is a mitigating factor, but the immediate dependency remains.

**Recommendation:** Ensure the `MessageInbox` contract is thoroughly audited and secured. Implement robust monitoring for the `inbox` contract's behavior. Consider adding a mechanism for users to recover funds if the `inbox` becomes permanently inaccessible or malicious, or a way for the owner to disable the `notifyBurn` call if the `inbox` is compromised, though this would require contract modification given the current design.


### `I-01` — `cap()` Function Returns Zero  *(Severity: Informational · Status: Unresolved)*

The `cap()` function is implemented to return `0`, explicitly indicating that there is no maximum supply for the Nock token. While this is a valid design choice and clearly stated in the code, some external tools or users might misinterpret a zero cap as an error or an uninitialized value, especially if they expect a finite supply for ERC-20 tokens.

**Recommendation:** Ensure clear documentation and communication regarding the unlimited supply of Nock tokens. This helps prevent misunderstandings and ensures proper integration with platforms that might have assumptions about token caps.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9b5e...1722`](https://basescan.org/address/0x9b5e262cf9bb04869ab40b19af91d2dc85761722) |
| **Network** | Base |
| **Price** | $0.04957 |
| **24h Volume** | $2.63M |
| **Liquidity** | $1.41M |
| **Volume / Liquidity** | 1.9× |
| **Token Age** | 5mo |
| **Top-10 Holders** | 25.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1875 buys / 1606 sells |

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

## Frequently Asked Questions

### Is Nockchain a scam?

Based on available data, labeling Nockchain definitively as a scam is not possible without further context. However, critical vulnerabilities exist. The owner retains control, and liquidity is not locked, which are common characteristics seen in projects that later prove malicious. While the contract is verified, these factors contribute to its high-risk score and warrant extreme investor caution regarding potential malicious actions.

### Is Nockchain safe to buy?

Nockchain (NOCK) carries a high-risk score of 51/100, indicating it is not inherently safe for investment. Key risk factors include the contract owner retaining control, which could lead to unexpected changes or manipulation. Additionally, the liquidity is not locked, exposing investors to potential rug pulls where funds supporting the token's value are withdrawn. These significant risks should be carefully considered.

### Has Nockchain been audited?

The Nockchain contract is verified, meaning its code is publicly available for review on the blockchain. This enhances transparency. However, verification is not the same as a formal security audit by an independent firm. An audit rigorously assesses code for deeper vulnerabilities and adherence to best practices, which is not indicated by verification alone.

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x85f1aa3a70fedd1c52705c15baed143e675cd626)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/nockchain-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
