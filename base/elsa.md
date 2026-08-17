---
token: Elsa
ticker: ELSA
network: base
risk_score: 45
status: medium
date: 2026-08-17
---

# Elsa (ELSA) — Smart Contract Security Analysis | Base

> **Risk Score: 45/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/elsa-base)

---

## Audit Summary

The ELSA token contract implements ERC20, ERC20Permit, and ERC3009 (Transfer With Authorization). It leverages OpenZeppelin libraries for robust and standard-compliant functionality. The primary risks identified relate to the initial centralized token distribution and the inherent front-running potential of EIP-3009's `transferWithAuthorization` function.

> **Final Recommendation:** It is recommended to carefully consider the implications of the highly centralized initial token distribution. If decentralization is a long-term goal, a plan for gradual distribution or a multi-signature wallet for the deployer's address should be implemented. For EIP-3009 authorizations, users should be educated on the front-running risks associated with `transferWithAuthorization` and advised to use private transaction relays or monitor the mempool if sensitive to execution order.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical implementation of the ELSA token contract is robust, utilizing battle-tested OpenZeppelin libraries for ERC20, ERC20Permit, and EIP712 functionalities. The custom ERC3009 extension… |
| **Governance / Economics** | 1/10 | High | The economic model of the ELSA token involves minting the entire `TOTAL_SUPPLY` of 1 billion tokens to the contract deployer during construction (7.4 Economic). This creates a highly centralized… |
| **Upgrades** | 6/10 | Medium | The ELSA token contract is not designed with upgradeability in mind, as it does not implement any proxy patterns (7.7 Upgrades). This means the contract's logic is immutable once deployed… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Initial Token Distribution  *(Severity: High · Status: Unresolved)*

The `ELSA` contract's constructor mints the entire `TOTAL_SUPPLY` (1 billion tokens) to the `msg.sender` (the deployer). This results in a highly centralized initial distribution of all tokens to a single address. This concentration of power can lead to significant economic and governance risks, including potential market manipulation, lack of decentralization, and single point of failure if the deployer's key is compromised (7.4 Economic, 7.5 Governance).

**Recommendation:** If a decentralized token distribution is desired, consider implementing a vesting schedule, a multi-signature wallet for the initial supply, or a distribution mechanism (e.g., airdrop, liquidity pool seeding) to spread ownership. Clearly communicate the intended use and security measures for the deployer's address holding the entire supply.


### `M-01` — Front-Running Risk for `transferWithAuthorization`  *(Severity: Medium · Status: Unresolved)*

The `transferWithAuthorization` function, as per EIP-3009 design, allows any third party to execute a valid signed authorization. If a signed `transferWithAuthorization` message is broadcast publicly (e.g., via a relayer or mempool), an attacker could observe it and front-run the intended transaction by submitting their own transaction with a higher gas price, effectively executing the transfer before the intended party (7.2 Code Security). While `receiveWithAuthorization` is protected by a `msg.sender != to` check, `transferWithAuthorization` lacks such a restriction.

**Recommendation:** Educate users about the front-running risks associated with `transferWithAuthorization`. For sensitive transactions, advise users to utilize private transaction relays (e.g., Flashbots) to prevent their signed messages from being exposed in the public mempool before execution. Implement monitoring for potential front-running attempts if possible.


### `L-01` — Reliance on `block.timestamp` for Authorization Validity  *(Severity: Low · Status: Unresolved)*

The `_validateAuthorization` function uses `block.timestamp` to check `validAfter` and `validBefore` parameters. While standard practice for time-based validity, `block.timestamp` can be manipulated by miners within a small window (e.g., up to 900 seconds on Ethereum mainnet, though typically less on faster chains). This could potentially allow a miner to slightly extend or shorten the validity window of an authorization (7.2 Code Security).

**Recommendation:** Acknowledge that `block.timestamp` is subject to minor miner manipulation. For most use cases, this level of precision is acceptable. If extremely precise time-based validity is critical, consider alternative time sources or design patterns, though this often introduces additional complexity or centralization.


### `I-01` — Lack of Emergency Pause Mechanism  *(Severity: Informational · Status: Unresolved)*

The `ELSA` token contract, being a standard ERC20 implementation with EIP-3009 extensions, does not include any emergency pause functionality. In the event of a critical vulnerability discovered in the token itself, or in a protocol that heavily relies on it, there is no mechanism to temporarily halt transfers or other operations (7.8 Operations).

**Recommendation:** Consider whether an emergency pause mechanism (e.g., using OpenZeppelin's `Pausable` contract) would be beneficial for the project's risk management strategy. While adding complexity and a point of control, it can provide a crucial safety switch in unforeseen circumstances. If implemented, ensure the pause functionality is controlled by a robust, multi-signature governance mechanism.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x29cc...bdca`](https://basescan.org/address/0x29cc30f9d113b356ce408667aa6433589cecbdca) |
| **Network** | Base |
| **Price** | $0.04201 |
| **24h Volume** | $158.8K |
| **Liquidity** | $304.6K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 6mo |
| **Top-10 Holders** | 89.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1752 buys / 1936 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x83f3aca29bc79b048b99c56013475570acc97ccf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/elsa-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-17*
