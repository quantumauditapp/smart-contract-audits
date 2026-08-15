---
token: ACEToken
ticker: ACE
network: bsc
risk_score: 92
status: critical
date: 2026-08-15
---

# ACEToken (ACE) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 92/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/acetoken-bsc)

---

## Audit Summary

The ACEToken contract is a wrapped ERC-20 token built upon OpenZeppelin's battle-tested ERC20 implementation. Its primary function is to allow a designated 'bridge' address to mint and burn tokens, facilitating cross-chain operations. The contract's code is minimal, well-structured, and leverages standard, audited libraries. Key risks identified relate to the centralized control of token supply by the bridge and the inherent dependency on the security of this external bridge contract, which was not part of this audit. Operational diligence during deployment is crucial due to the immutable nature of the bridge address.

> **Final Recommendation:** Prioritize a comprehensive security audit of the external bridge contract that interacts with ACEToken, as its security directly dictates the integrity of the token's supply. Implement robust operational procedures for the deployment of ACEToken, ensuring the correct and secure bridge address is set, given its immutable nature. Educate users on the use of `increaseAllowance` and `decreaseAllowance` to mitigate standard ERC-20 front-running risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The `ACEToken` contract is a minimal wrapper around `WrappedERC20`, which extends OpenZeppelin's battle-tested `ERC20` implementation (7.1). The custom logic for `mint` and `burn` is correctly… |
| **Governance / Economics** | 1/10 | High | The economic model of `ACEToken` is highly centralized, with the `bridge` address holding exclusive control over the `mint` and `burn` functions (7.4). This design is typical for wrapped tokens but… |
| **Upgrades** | 3/10 | High | The `ACEToken` and `WrappedERC20` contracts are not designed with upgradeability patterns (e.g., proxies). They are deployed as immutable implementations. This eliminates risks associated with… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control of Token Supply by Bridge  *(Severity: High · Status: Unresolved)*

The `WrappedERC20` contract, and thus `ACEToken`, grants the `bridge` address exclusive control over `mint` and `burn` functions. This centralization means the security of the `ACEToken`'s supply is entirely dependent on the security and integrity of the `bridge` contract. A compromise of the `bridge` could lead to arbitrary minting or burning of `ACEToken`, severely impacting its value and ecosystem (7.3, 7.4).

**Recommendation:** While inherent to wrapped token designs, it's crucial to ensure the `bridge` contract itself undergoes rigorous security audits and implements robust security measures (e.g., multi-signature, time-locks, circuit breakers). Users should be aware of this centralized control point.


### `M-01` — Dependency on External Bridge Contract Security  *(Severity: Medium · Status: Unresolved)*

The `ACEToken` contract's functionality, particularly its supply management, is entirely reliant on an external `bridge` contract whose code was not provided for this audit. The security posture of the `ACEToken` is therefore directly tied to the security of this external `bridge`. Any vulnerabilities in the `bridge` contract could directly impact the integrity and functionality of `ACEToken` (7.6).

**Recommendation:** The `bridge` contract should be thoroughly audited for common vulnerabilities, including reentrancy, access control, and logic errors. Implement robust monitoring and incident response for the bridge.


### `L-01` — Standard ERC-20 Front-Running Risks  *(Severity: Low · Status: Unresolved)*

The `approve` function in the underlying OpenZeppelin ERC20 contract is susceptible to a known front-running attack vector. If a user approves an amount, and then attempts to decrease that approval, a malicious actor could front-run the decrease transaction, spending the original approved amount before the decrease takes effect. This could lead to the malicious actor spending more than the user intended. While mitigated by `increaseAllowance` and `decreaseAllowance`, the base `approve` function still exists (7.2).

**Recommendation:** Users should be advised to use `increaseAllowance` and `decreaseAllowance` functions instead of directly calling `approve` to modify existing allowances, as these functions are not susceptible to this specific front-running attack.


### `I-01` — Immutability of Bridge Address  *(Severity: Informational · Status: Unresolved)*

The `bridge` address is declared as `immutable` in `WrappedERC20.sol` and set during construction. This prevents any modification of the bridge address after deployment, which is generally good for security as it removes a potential point of attack for unauthorized changes. However, it also means that if the initially configured `bridge` address is incorrect or becomes compromised and unrecoverable, there is no on-chain mechanism to update it, potentially rendering the token's mint/burn functionality permanently unusable or controlled by a defunct address (7.8).

**Recommendation:** Ensure extreme diligence in verifying the `bridge` address during deployment. Consider off-chain emergency procedures or a migration plan in case the bridge becomes permanently inoperable.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc27a...def4`](https://bscscan.com/address/0xc27a719105a987b4c34116223cae8bd8f4b5def4) |
| **Network** | BNB Chain |
| **Price** | $0.2567 |
| **24h Volume** | $35.5K |
| **Liquidity** | $42.8K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 2y |
| **Top-10 Holders** | 83.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 635 buys / 650 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x2fdf9b25df26e81598c09ef7482a82e2ec6eb68c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/acetoken-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-15*
