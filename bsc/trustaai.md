---
token: Trusta.AI
ticker: TA
network: bsc
risk_score: 33
status: low
date: 2026-09-13
---

# Trusta.AI (TA) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 33/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/trustaai-bsc)

---

## Audit Summary

The TrustaOFT contract is an ERC20 token implementing LayerZero's Omnichain Fungible Token (OFT) standard and OpenZeppelin's ERC20Permit. The contract is minimal, primarily inheriting from well-audited libraries. Initial token minting occurs only on a designated main chain. The primary risks identified are related to the inherent reliance on the LayerZero protocol's security and the operational management of its configurations by the multisig owner.

> **Final Recommendation:** Ensure the multisig owner for LayerZero configurations adheres to strict operational security procedures, including multi-party review and testing of all parameter changes. Implement robust monitoring for cross-chain transactions and LayerZero endpoint health. Educate users about the potential front-running risks associated with ERC20Permit functionality, especially when interacting with off-chain relayers.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract (7.1 Architecture) is well-structured, inheriting from battle-tested OpenZeppelin and LayerZero libraries. The code (7.2 Code Security) is minimal and straightforward, reducing the… |
| **Governance / Economics** | 4/10 | Medium | The contract utilizes `Ownable` for access control (7.3 Access Control), with the owner being a multisig address, which is a strong security practice (7.5 Governance). The token's economic model (7.4… |
| **Upgrades** | 7/10 | Low | The TrustaOFT contract is not designed as an upgradeable proxy (7.7 Upgrades). It is a standard implementation contract, meaning its logic cannot be changed after deployment. This eliminates… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 44.0% |
| **Top-3 Unlocked** | ⚠️ 95.1% |

## Security Findings

_🟠 1 High · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Reliance on LayerZero Protocol and Configuration  *(Severity: High · Status: Unresolved)*

The `TrustaOFT` contract relies heavily on the LayerZero protocol for its cross-chain functionality. The security and integrity of the token's supply across different chains are directly dependent on the correct functioning and security of the LayerZero endpoint and its underlying infrastructure. Any vulnerabilities or misconfigurations within the LayerZero protocol itself could impact the `TrustaOFT` token's cross-chain operations and overall supply integrity.

**Recommendation:** While this is an inherent design choice for an Omnichain Fungible Token, it is crucial to monitor LayerZero's security announcements and ensure the `_lzEndpoint` address provided during deployment is correct and trusted. Implement robust monitoring for cross-chain transactions and LayerZero endpoint health.


### `L-01` — Operational Risk of LayerZero Configuration  *(Severity: Low · Status: Unresolved)*

The owner (a multisig, according to prefill data) has significant control over LayerZero-specific configurations, such as setting trusted remotes (`setPeer`), minimum destination gas (`setMinDstGas`), and other parameters. Incorrect or malicious configuration by the owner, even if it's a multisig, could lead to funds being stuck, lost, or enable unauthorized cross-chain transfers if not handled carefully.

**Recommendation:** The multisig owners should establish strict internal procedures and multiple-party review for any changes to LayerZero configurations. Thoroughly test configuration changes in a staging environment before applying them to production. Consider time-locks for critical configuration changes.


### `I-01` — Front-running Risk with ERC20Permit  *(Severity: Informational · Status: Unresolved)*

The `ERC20Permit` functionality allows users to sign off-chain approvals, which can then be submitted on-chain by anyone. This introduces a potential front-running vector where a malicious actor could observe a signed `permit` message, front-run the transaction to use the approval themselves, or cause the original transaction to fail, leading to a poor user experience.

**Recommendation:** Users should be educated on the risks associated with `permit` functionality, especially regarding transaction submission. Off-chain relayers should implement anti-front-running measures (e.g., using a trusted relayer, setting strict gas price limits, or using commit-reveal schemes if applicable) to protect users.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x539a...b140`](https://bscscan.com/address/0x539ae81a166e5e80aed211731563e549c411b140) |
| **Network** | BNB Chain |
| **Price** | $0.05328 |
| **24h Volume** | $1.52M |
| **Liquidity** | $237.1K |
| **Volume / Liquidity** | 6.4× |
| **Token Age** | 1y |
| **Top-10 Holders** | 95.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 9448 buys / 11268 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xfa7421f1ed6ad1548316a847e8437af7219a8f18)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/trustaai-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-13*
