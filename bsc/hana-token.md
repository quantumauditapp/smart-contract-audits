---
token: Hana Token
ticker: HANA
network: bsc
risk_score: 58
status: high
date: 2026-07-26
---

# Hana Token (HANA) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 58/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/hana-token-bsc)

---

## Audit Summary

The HanaToken contract is an ERC20 token implementing standard functionalities from OpenZeppelin, including burnable and permit extensions, with Ownable access control. The contract exhibits good code quality and leverages battle-tested libraries. Key findings include centralized control over token burning, the use of an EOA for ownership, and the absence of a timelock for critical administrative actions. These issues introduce centralization risks and potential single points of failure.

> **Final Recommendation:** To enhance the security and decentralization of the HanaToken contract, it is recommended to transition ownership from an EOA to a robust multi-signature wallet or a well-governed DAO. Additionally, consider implementing a timelock mechanism for critical administrative functions like `transferOwnership` to provide a delay for community review and reaction. Review the necessity of the `onlyOwner` modifier on burn functions; if not strictly required, consider removing it to decentralize burning capabilities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages battle-tested OpenZeppelin libraries for ERC20, Burnable, Permit, and Ownable functionalities, contributing to robust code security and adherence to standards. It utilizes a… |
| **Governance / Economics** | 1/10 | High | The token's economic model is straightforward, with a fixed `INITIAL_SUPPLY` minted once, preventing inflationary risks from further minting. However, the centralized control over token burning… |
| **Upgrades** | 6/10 | Medium | The HanaToken contract is not designed with upgradeability patterns (e.g., proxy contracts), meaning its logic cannot be modified post-deployment. This eliminates risks associated with upgrade… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control of Token Burning  *(Severity: High · Status: Unresolved)*

The `burn` and `burnFrom` functions in the `HanaToken` contract are restricted to the `onlyOwner` modifier. This grants the contract owner exclusive power to reduce the total supply of tokens. Such centralization introduces a significant risk, as a compromised owner key or a malicious owner could unilaterally impact the token's supply dynamics, potentially leading to adverse economic consequences or a loss of trust from token holders (7.3 Access Control, 7.4 Economic).

**Recommendation:** Evaluate whether the burning functionality truly requires `onlyOwner` restriction. If not, consider removing the `onlyOwner` modifier to allow any token holder to burn their own tokens, or implement a more decentralized burning mechanism. If centralized burning is a design choice, ensure the owner's address is secured by a robust multi-signature wallet or a DAO.


### `M-01` — Single Point of Failure for Ownership (EOA Owner)  *(Severity: Medium · Status: Unresolved)*

The contract's ownership is held by an Externally Owned Account (EOA), as indicated by the provided data (`owner_kind: EOA`). This creates a single point of failure. If the EOA's private key is compromised, lost, or becomes inaccessible, critical administrative functions such as `burn`, `burnFrom`, and `transferOwnership` would be at risk of unauthorized use or permanent inaccessibility, impacting the contract's long-term operational integrity (7.3 Access Control, 7.8 Operations).

**Recommendation:** It is strongly recommended to transfer ownership of the contract to a multi-signature wallet (e.g., Gnosis Safe) or a decentralized autonomous organization (DAO) controlled by a robust governance mechanism. This distributes control and significantly reduces the risk associated with a single point of failure.


### `L-01` — Lack of Timelock for Critical Administrative Actions  *(Severity: Low · Status: Unresolved)*

The `transferOwnership` function allows the current owner to immediately transfer ownership to a new address. Without a timelock mechanism, a malicious or accidental transfer of ownership cannot be reversed or prevented by the community or other stakeholders. This lack of a delay increases the risk of immediate and irreversible control loss, especially if the owner's key is compromised (7.3 Access Control, 7.5 Governance).

**Recommendation:** Consider implementing a timelock mechanism for critical administrative functions, particularly `transferOwnership`. This would introduce a mandatory delay between initiating an ownership transfer and its execution, providing a window for detection and potential intervention in case of an erroneous or malicious action.


### `I-01` — High Solidity Compiler Version Adoption  *(Severity: Informational · Status: Unresolved)*

The contract uses `pragma solidity ^0.8.28`. While newer compiler versions often include optimizations and bug fixes, very recent versions might have less extensive real-world testing and community scrutiny compared to more established and widely adopted versions (e.g., `0.8.19` or `0.8.20`). This is a minor informational point, as OpenZeppelin contracts are generally well-tested across supported compiler versions (7.2 Code Security).

**Recommendation:** While not a direct vulnerability, projects should be aware of the trade-offs when adopting the absolute latest compiler versions. Ensure that all dependencies and tools are fully compatible and that sufficient testing is conducted. For production deployments, sometimes a slightly older, more battle-tested compiler version within the `0.8.x` range is preferred for maximum stability.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6261...8353`](https://bscscan.com/address/0x6261963ebe9ff014aad10ecc3b0238d4d04e8353) |
| **Network** | BNB Chain |
| **Price** | $0.02906 |
| **24h Volume** | $1.24M |
| **Liquidity** | $1.38M |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 10mo |
| **Top-10 Holders** | 73.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 19762 buys / 18844 sells |

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

### Is Hana Token a scam?

Based on automated analysis, Hana Token scores 64/100 (High Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is Hana Token safe to buy?

Our scanner flagged a risk score of 64/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has Hana Token been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xd21bc2291c1aef340f5265e257b18aa5dafed759)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/hana-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-26*
