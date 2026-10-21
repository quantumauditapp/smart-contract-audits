---
token: AntFun
ticker: ANTFUN
network: bsc
risk_score: 68
status: high
date: 2026-09-15
---

# AntFun (ANTFUN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 68/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/antfun-bsc)

---

## Audit Summary

The ANTFUNOFT contract implements an Omnichain Fungible Token (OFT) using LayerZero, enhanced with EIP-3009 for gasless meta-transactions. The contract leverages well-audited OpenZeppelin libraries for access control (Ownable) and cryptographic utilities (EIP712, ECDSA). The implementation of EIP-3009 includes robust nonce management and timestamp checks to prevent replay attacks and ensure authorization validity. Key areas of focus include centralized ownership, reliance on external protocols, and inherent characteristics of meta-transactions and blockchain timestamps. No critical or high-severity vulnerabilities were identified.

> **Final Recommendation:** It is recommended to carefully manage the private key associated with the owner address due to its centralized control over the contract and LayerZero delegate functions. Consider implementing a multi-signature wallet for ownership to enhance security and decentralize control. For EIP-3009 authorizations, advise users to set `validBefore` timestamps carefully to minimize the window for potential front-running, and ensure robust nonce management in off-chain signing processes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract demonstrates good technical architecture (7.1 Architecture) by inheriting from established and audited libraries like OpenZeppelin's Ownable, EIP712, and ECDSA, as well as LayerZero's… |
| **Governance / Economics** | 2/10 | High | The economic model (7.4 Economic) is that of a standard fungible token with cross-chain capabilities and gasless transfers. Governance (7.5 Governance) is centralized, with a single owner address… |
| **Upgrades** | 3/10 | High | The contract is not designed with an explicit upgrade mechanism (7.7 Upgrades). While a 'version' constant is present, there are no proxy patterns (e.g., UUPS, Transparent) or other upgradeability… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟢 2 Low · ⚪ 2 Informational_

### `L-01` — Timestamp Dependence for Authorization Validity  *(Severity: Low · Status: Unresolved)*

The EIP-3009 authorization mechanism relies on `block.timestamp` to enforce `validAfter` and `validBefore` conditions. While standard for time-based checks on EVM chains, `block.timestamp` can be manipulated by miners within a small window (e.g., up to 900 seconds on Ethereum). This could lead to minor deviations in the precise validity period of an authorization, potentially allowing a transaction to be valid slightly earlier or later than intended by the signer.

**Recommendation:** While this is an inherent characteristic of blockchain timestamps and not a flaw in the EIP-3009 implementation, users should be aware of this potential imprecision. When signing authorizations, consider adding a small buffer to `validAfter` and `validBefore` if precise timing is critical, or use a sufficiently wide window where minor deviations are acceptable.


### `L-02` — Front-running Risk for EIP-3009 Authorizations  *(Severity: Low · Status: Unresolved)*

EIP-3009 meta-transactions, by their nature, are susceptible to front-running. If a signed authorization is broadcast to the mempool, a malicious actor could observe it and submit a transaction with a higher gas price to execute the same authorization (or cancel it) before the legitimate sender. Although nonces prevent replay attacks, a successful front-run would consume the nonce, forcing the original sender to generate a new signature, leading to a poor user experience.

**Recommendation:** Advise users to keep the `validBefore` window as short as practically possible to minimize the time an authorization is exposed to the mempool. Implement off-chain mechanisms to submit transactions quickly or use private transaction relays where available to reduce front-running opportunities.


### `I-01` — Centralized Ownership and Control  *(Severity: Informational · Status: Unresolved)*

The contract utilizes OpenZeppelin's `Ownable` pattern, which assigns all administrative privileges to a single owner address. This includes the ability to set LayerZero delegate and minimum destination gas parameters (inherited from OFT). This centralization of power, while common, introduces a single point of failure and potential for a single compromised key to control critical contract functions.

**Recommendation:** Consider migrating ownership to a multi-signature wallet (e.g., Gnosis Safe) to distribute control and enhance security against a single point of compromise. This would require multiple approvals for sensitive operations.


### `I-02` — Reliance on LayerZero Protocol Security  *(Severity: Informational · Status: Unresolved)*

The contract's core cross-chain functionality is built upon LayerZero's Omnichain Fungible Token (OFT) standard. This means the security and operational integrity of the ANTFUNOFT token across different chains are inherently dependent on the LayerZero protocol, its endpoints, and its underlying infrastructure. Any vulnerabilities or operational issues within LayerZero could directly impact the token.

**Recommendation:** Maintain awareness of LayerZero's security posture, audits, and any reported vulnerabilities. Ensure that the LayerZero endpoint address used is the official and correct one for the deployed network.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6ced...087c`](https://bscscan.com/address/0x6ced5c6d3f913b48d59fa07abbfe9060c409087c) |
| **Network** | BNB Chain |
| **Price** | $0.08971 |
| **24h Volume** | $299.1K |
| **Liquidity** | $2.43M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 3mo |
| **Top-10 Holders** | 62.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 840 buys / 455 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xf0c22680044948752f696bf0bc70672129246df7)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/antfun-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-15*
