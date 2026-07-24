---
token: RaveDAO
ticker: RAVE
network: ethereum
risk_score: 37
status: medium
date: 2026-06-29
---

# RaveDAO (RAVE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 37/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ravedao-eth)

---

## Audit Summary

The RaveToken contract is an ERC-20 token built upon OpenZeppelin's Ownable and LayerZero's OFT (Omnichain Fungible Token) standards. The contract facilitates cross-chain transfers via LayerZero and includes a basic burn function. The codebase is concise and leverages well-audited external libraries, contributing to high technical security. However, the system exhibits centralized control by the owner over critical LayerZero configurations and lacks an emergency pause mechanism, which introduces medium-level governance and operational risks. The overall security is heavily reliant on the integrity of the LayerZero protocol.

> **Final Recommendation:** It is recommended to implement an emergency pause mechanism to allow the owner or a designated multisig to halt critical operations in case of an exploit or vulnerability. Consider deploying the contract with a robust multisig wallet as the owner to enhance security and decentralize control over critical LayerZero configurations. Additionally, establish clear operational procedures for managing LayerZero parameters and for handling potential incidents.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical architecture (7.1 Architecture) of RaveToken is straightforward, extending battle-tested ERC-20, Ownable, and LayerZero OFT contracts. The custom code (7.2 Code Security) is minimal… |
| **Governance / Economics** | 4/10 | Medium | The economic model (7.4 Economic) is simple, based on an ERC-20 token with cross-chain capabilities. Governance (7.5 Governance) is centralized, with a single owner address controlling critical… |
| **Upgrades** | 7/10 | Low | The RaveToken contract is not designed with upgradeability (7.7 Upgrades) in mind. It is a standard implementation contract, meaning there are no proxy-related risks or complexities associated with… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟢 2 Low · ⚪ 2 Informational_

### `L-01` — Lack of Emergency Pause Mechanism  *(Severity: Low · Status: Unresolved)*

The contract lacks an emergency pause mechanism. In the event of a critical vulnerability, an exploit, or a severe issue with the LayerZero protocol, there is no function available to the owner or any authorized entity to temporarily halt token transfers or cross-chain operations. This could prevent the project from mitigating ongoing losses or preventing further damage.

**Recommendation:** Implement a `Pausable` mechanism (e.g., from OpenZeppelin) that allows the owner or a designated governance entity to pause and unpause critical functions, such as `transfer`, `transferFrom`, `sendFrom`, and `_debit` (for cross-chain transfers). This provides a crucial safety switch for incident response.


### `L-02` — No Mechanism for Recovering Accidentally Sent Tokens  *(Severity: Low · Status: Unresolved)*

The contract does not include a function to recover accidentally sent ERC-20 tokens (other than RaveToken itself) or native currency (ETH/MATIC/BNB) that might be mistakenly sent to the contract address. Any such assets sent to the contract would become permanently locked and inaccessible.

**Recommendation:** Add an `onlyOwner` function to allow the recovery of arbitrary ERC-20 tokens and native currency. This function should enable the owner to transfer specified tokens or native currency from the contract to a designated address. Care should be taken to prevent the recovery of the contract's own RaveTokens if they are intended to be held by the contract for specific purposes.


### `I-01` — Centralized Control by Owner  *(Severity: Informational · Status: Unresolved)*

The contract utilizes the OpenZeppelin `Ownable` pattern, granting a single address (the owner) exclusive control over critical functions. Specifically, the owner can configure LayerZero parameters such as `setDelegate`, `setTrustedRemote`, and `setEnforcedOptions`. This centralization introduces a single point of failure, where a compromise of the owner's private key could lead to unauthorized control over the token's cross-chain functionality.

**Recommendation:** Consider using a robust multisig wallet (e.g., Gnosis Safe) as the owner to distribute control and reduce the risk associated with a single point of failure. For highly sensitive operations, explore integrating a more decentralized governance mechanism if feasible for the project's scope.


### `I-02` — Reliance on LayerZero Security  *(Severity: Informational · Status: Unresolved)*

The RaveToken contract's core functionality for cross-chain transfers is entirely dependent on the LayerZero protocol and its endpoint. The security and operational integrity of the token across different chains are directly tied to the security of LayerZero's infrastructure, including its relayer network and oracle services. Any vulnerability or compromise within LayerZero could directly impact the RaveToken's cross-chain value transfer and integrity.

**Recommendation:** Acknowledge and monitor the security posture of the LayerZero protocol. Stay updated on LayerZero's security announcements, audits, and any reported vulnerabilities. Implement robust monitoring for LayerZero-related events and potential anomalies in cross-chain transfers.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1720...db97`](https://etherscan.io/address/0x17205fab260a7a6383a81452ce6315a39370db97) |
| **Network** | Ethereum |
| **Price** | $0.2909 |
| **24h Volume** | $26.6K |
| **Liquidity** | $253.8K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 6mo |
| **Top-10 Holders** | 97.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1228 buys / 1122 sells |

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

### Is RaveDAO a scam?

Based on the provided data, RaveDAO exhibits several characteristics commonly associated with high-risk projects. The unrenounced contract ownership, extreme token centralization (97.3% in top 10 holders), and unlocked liquidity are significant red flags that can indicate a heightened potential for malicious actions or severe market manipulation. These factors contribute to its critical risk score of 71/100.

### Is RaveDAO safe to buy?

Investing in RaveDAO carries significant risk, reflected by its critical risk score of 71/100. Key safety concerns include the unrenounced contract ownership, allowing potential future alterations by the deployer, and the highly concentrated token supply that enables substantial market control by a few large holders. Additionally, the lack of locked liquidity means the project is vulnerable to liquidity withdrawals, posing a substantial risk to investor funds.

### Has RaveDAO been audited?

The RaveDAO contract has been verified on Etherscan, which means its code is publicly available and matches the deployed bytecode. However, contract verification is not the same as a professional security audit. An audit involves a thorough review by cybersecurity experts to identify vulnerabilities, and there is no information provided to suggest RaveDAO has undergone such a process.

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xca47e80bd01a1f5bcc8cf709d48a5399d533447e03d56f488498dc83c35b5831)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ravedao-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-29*
