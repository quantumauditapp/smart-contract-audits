---
token: NEAR
ticker: NEAR
network: ethereum
risk_score: 43
status: medium
date: 2026-09-12
---

# NEAR (NEAR) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 43/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/near-eth)

---

## Audit Summary

The eNear contract serves as an ERC20 token for the NEAR-Ethereum Rainbow Bridge. It facilitates cross-chain transfers by minting tokens on Ethereum upon verified NEAR proofs and burning tokens for transfers to NEAR. The contract utilizes a robust proof verification system and standard ERC20 implementation. However, the `AdminControlled` component introduces severe centralization risks through highly privileged functions like `adminDelegatecall` and `adminSstore`, granting the administrator complete control over the contract's logic and state. This centralization, coupled with a critical external dependency on the `INearProver`, elevates the overall risk to Critical.

> **Final Recommendation:** To mitigate the severe centralization risks, it is strongly recommended to replace the single `admin` address with a robust multi-signature wallet (e.g., Gnosis Safe) for all privileged functions, especially `adminDelegatecall`, `adminSstore`, and `adminPause`. Consider removing or severely restricting the `adminDelegatecall` and `adminSstore` functions, as they grant excessive power. Additionally, conduct a thorough security audit of the `INearProver` contract and the underlying NEAR proof system, as the bridge's security is critically dependent on these external components.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical architecture (7.1) of the eNear bridge involves a standard ERC20 token integrated with a proof-based cross-chain mechanism. The `Bridge` contract implements robust proof verification… |
| **Governance / Economics** | 3/10 | High | The governance and economic model (7.5, 7.4) of the eNear contract is highly centralized. The `admin` role possesses absolute control over critical contract functions, including the ability to pause… |
| **Upgrades** | 1/10 | High | While the eNear contract is not explicitly designed with a proxy upgrade pattern, the `adminDelegatecall` function (7.7) effectively provides an uncontrolled upgrade mechanism. The administrator can… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 69.2% |
| **Top-3 Unlocked** | ⚠️ 83.3% |

## Security Findings

_🟡 4 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Limited Front-running Potential in `finaliseNearToEthTransfer`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). While the `usedProofs` mapping prevents the reuse of the same proof, an attacker could potentially front-run a legitimate user's `finaliseNearToEthTransfer` transaction if they can observe the proof data in the mempool and submit their own transaction with the same proof (if multiple parties can generate the same proof) or a different valid proof for the same recipient. This could allow an attacker to claim tokens intended for another party or to claim tokens faster.

**Recommendation:** While the impact is mitigated by the single-use nature of proofs, consider if the proof generation process can be designed to include a unique user-specific nonce or commitment to prevent one user's proof from being used by another. Ensure that the `receiptId` is sufficiently unique and tied to the intended recipient.


### `M-02` — Centralized Control via `adminDelegatecall`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `adminDelegatecall` function in the `AdminControlled` contract allows the `admin` to execute arbitrary code in the context of the `eNear` contract. This grants the administrator complete and unrestricted control over the contract's logic and state. A malicious or compromised admin could mint arbitrary tokens, drain funds, modify critical bridge parameters, or even self-destruct the contract.

**Recommendation:** Remove the `adminDelegatecall` function entirely. If dynamic functionality is required, implement a well-defined, audited, and time-locked upgrade mechanism (e.g., UUPS proxy with a governance delay) instead of arbitrary delegatecall. If removal is not feasible, restrict its usage to a multi-signature wallet with a significant delay.


### `M-03` — Arbitrary Storage Modification via `adminSstore`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `adminSstore` function allows the `admin` to write any arbitrary value to any storage slot within the contract. This means the administrator can unilaterally change any state variable, including critical parameters like the `admin` address itself, the `prover` address, `nearConnector`, `minBlockAcceptanceHeight`, the `usedProofs` mapping, or even ERC20 token balances by manipulating storage slots. This constitutes a critical backdoor.

**Recommendation:** Remove the `adminSstore` function. Direct manipulation of storage should never be exposed to an external account. All state modifications should occur through well-defined, validated functions.


### `M-04` — Critical External Dependency on `INearProver`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The security of the `finaliseNearToEthTransfer` function, which is responsible for minting eNear tokens on Ethereum, is entirely dependent on the `INearProver` contract correctly verifying proofs from the NEAR blockchain. Any vulnerability, bug, or compromise in the `INearProver` contract or the underlying NEAR proof system could lead to unauthorized or fraudulent minting of eNear tokens, directly impacting the token's supply and value.

**Recommendation:** Conduct a comprehensive security audit of the `INearProver` contract and the entire NEAR proof generation and verification mechanism. Implement robust monitoring for the `INearProver` contract's behavior and consider circuit breakers or emergency pause mechanisms that can be triggered if anomalies are detected in the proof verification process.


### `L-01` — Gas Inefficiency in `_parseAndConsumeProof` Comparison  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The comparison `keccak256(fullOutcomeProof.outcome_proof.outcome_with_id.outcome.executor_id) == keccak256(nearConnector)` involves hashing two byte arrays. While functionally correct, comparing the raw bytes directly (after ensuring length equality) could be more gas efficient if `executor_id` and `nearConnector` are expected to be of fixed or similar lengths. Hashing adds an unnecessary computational overhead if direct byte comparison is feasible.

**Recommendation:** If `executor_id` and `nearConnector` are always of the same length, consider comparing them directly after a length check to save gas. If lengths can vary, hashing is a safer approach for content comparison.


### `I-01` — Use of Older Solidity Version  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract is compiled with `pragma solidity 0.6.12`. While this version is functional, newer Solidity versions (e.g., 0.8.x) offer built-in overflow/underflow checks by default, reducing reliance on `SafeMath` (though `SafeMath` is still good practice for clarity), and include various language improvements, optimizations, and bug fixes. Using an older compiler version might miss out on these benefits.

**Recommendation:** Consider upgrading the Solidity compiler version to a more recent stable release (e.g., 0.8.x) and re-auditing the contract. Ensure all dependencies are compatible with the new compiler version.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x85f1...f6a4`](https://etherscan.io/address/0x85f17cf997934a597031b2e18a9ab6ebd4b9f6a4) |
| **Network** | Ethereum |
| **Price** | $2.3700 |
| **24h Volume** | $147.3K |
| **Liquidity** | $399.6K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 2y |
| **Top-10 Holders** | 34.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 183 buys / 194 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xee8aaa362a75fbf8e0a38a50ddc27f38551e16ea)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/near-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*
