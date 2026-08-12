---
token: noice
ticker: NOICE
network: base
risk_score: 36
status: medium
date: 2026-08-12
---

# noice (NOICE) — Smart Contract Security Analysis | Base

> **Risk Score: 36/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/noice-base)

---

## Audit Summary

The ClankerToken contract is an ERC20 token with extensions for burning, permits, and voting, and includes custom cross-chain mint/burn functionality. The contract is generally well-structured, leveraging battle-tested OpenZeppelin libraries. A key observation is the centralized and immutable `_admin` role, which controls critical token metadata and a one-time verification flag, posing a single point of failure.

> **Final Recommendation:** It is strongly recommended to implement a robust access control mechanism for the `_admin` role, such as a multi-signature wallet or a time-locked governance contract, to mitigate the risks associated with a single point of failure. Consider adding an event for the initial assignment of the `_admin` role to enhance transparency. Furthermore, ensure thorough due diligence on the `SUPERCHAIN_TOKEN_BRIDGE` to understand its security posture, as the token's cross-chain integrity directly depends on it.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates strong technical foundations by inheriting from multiple OpenZeppelin ERC20 extensions (`ERC20Permit`, `ERC20Votes`, `ERC20Burnable`), ensuring adherence to established… |
| **Governance / Economics** | 2/10 | High | The economic model involves an initial fixed supply minted on a specific chain, with `crosschainMint` and `crosschainBurn` functions enabling supply movement across chains, restricted to a… |
| **Upgrades** | 8/10 | Low | The ClankerToken contract is implemented as a standard, non-upgradeable ERC20 token (7.7 Upgrades). This design choice eliminates the complexities and potential risks associated with proxy upgrade… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.8% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized and Immutable Admin Role  *(Severity: High · Status: Unresolved)*

The `_admin` address holds significant control over critical token parameters (e.g., `updateImage`, `updateMetadata`, `verify`) and is set immutably in the constructor without any mechanism for transfer or multi-signature control (7.3 Access Control, 7.5 Governance). This creates a single point of failure; compromise or loss of this key could lead to unauthorized modifications or permanent loss of administrative control, impacting the token's integrity and user trust.

**Recommendation:** Implement a more robust access control mechanism for the `_admin` role. This could involve using a multi-signature wallet (e.g., Gnosis Safe) for the admin address or integrating a decentralized governance system. Additionally, consider adding a function to transfer the admin role to a new address, protected by a time-lock or multi-sig, to allow for operational flexibility and recovery.


### `L-01` — Missing Event for Admin Role Assignment  *(Severity: Low · Status: Unresolved)*

The `_admin` address is assigned in the constructor, but no event is emitted to log this critical assignment on-chain (7.8 Operations). While the admin is set during deployment, the absence of an event hinders transparent monitoring and auditing of the initial administrative setup, making it less straightforward to track the initial controller.

**Recommendation:** Emit an event in the constructor to explicitly log the `_admin` address upon contract deployment. For example: `event AdminSet(address indexed admin);` and then `emit AdminSet(admin_);` in the constructor.


### `I-01` — Dependency on External Superchain Token Bridge  *(Severity: Informational · Status: Unresolved)*

The `crosschainMint` and `crosschainBurn` functions are exclusively controlled by `Predeploys.SUPERCHAIN_TOKEN_BRIDGE` (7.6 External). This design means the token's supply management and overall cross-chain functionality are directly dependent on the security and integrity of this external bridge. Any vulnerability or compromise within the bridge could directly impact the token's economic model and supply across chains.

**Recommendation:** While this is a design choice, it is crucial to ensure thorough due diligence on the `SUPERCHAIN_TOKEN_BRIDGE` contract and its operational security. Understand its audit history, security practices, and potential risks. Implement robust monitoring for bridge activity relevant to this token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9cb4...0c69`](https://basescan.org/address/0x9cb41fd9dc6891bae8187029461bfaadf6cc0c69) |
| **Network** | Base |
| **Price** | $0.00001056 |
| **24h Volume** | $332.9K |
| **Liquidity** | $196.1K |
| **Volume / Liquidity** | 1.7× |
| **Token Age** | 1y |
| **Top-10 Holders** | 82.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1085 buys / 1225 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xeff7f8fe083d7a446717b992bf84391253e54789)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/noice-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-12*
