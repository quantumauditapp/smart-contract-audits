---
token: Avail (Wormhole)
ticker: AVAIL
network: base
risk_score: 61
status: high
date: 2026-08-12
---

# Avail (Wormhole) (AVAIL) — Smart Contract Security Analysis | Base

> **Risk Score: 61/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/avail-wormhole-base)

---

## Audit Summary

The Avail (Wormhole) token contract is an upgradeable ERC20 token utilizing OpenZeppelin's AccessControlDefaultAdminRules for robust access management. While the technical implementation is sound, significant risks stem from the centralized minting authority and the inherent dependency on the Wormhole bridge for token backing. The contract's upgradeability and administrative roles are well-secured by a multisig and time-locked mechanisms.

> **Final Recommendation:** Implement robust operational security measures for the `MINTER_ROLE` to prevent unauthorized token inflation, such as multi-signature control or time-locks for minting operations. Conduct thorough due diligence and continuous monitoring of the Wormhole bridge's security, as it represents a critical external dependency for the token's value. Consider implementing an emergency pause mechanism to mitigate risks during critical bridge incidents or other unforeseen circumstances.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The contract leverages battle-tested OpenZeppelin upgradeable libraries for ERC20, ERC20Permit, and AccessControl (7.1 Architecture). The implementation of `mint` and `burn` functions is… |
| **Governance / Economics** | 2/10 | High | Access control is robust, utilizing OpenZeppelin's `AccessControlDefaultAdminRulesUpgradeable` which enforces time-locks for `DEFAULT_ADMIN_ROLE` changes, enhancing governance security (7.3 Access… |
| **Upgrades** | 1/10 | High | The contract is implemented as a TransparentUpgradeableProxy, following OpenZeppelin's upgradeable pattern. The `initialize` function correctly uses `reinitializer(2)`, and the constructor disables… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 3-of-5 |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.1% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Centralization Risk: Unlimited Minting by MINTER_ROLE  *(Severity: High · Status: Unresolved)*

The `mint` function allows an address with the `MINTER_ROLE` to mint an arbitrary amount of tokens to any account. This introduces a significant centralization risk, as a compromise of the `MINTER_ROLE` key or malicious action by its holder could lead to hyperinflation of the token supply, devaluing existing tokens and potentially causing a loss of user funds. This is a common pattern for wrapped tokens but represents a critical point of failure.

**Recommendation:** Implement strict operational security for the `MINTER_ROLE` address. Consider adding additional controls such as multi-signature requirements for minting transactions, rate limits on minting, or time-locks for large mints. Clearly communicate the implications of this centralized control to users.


### `H-02` — External Dependency Risk: Wormhole Bridge Security  *(Severity: High · Status: Unresolved)*

The Avail (Wormhole) token is a wrapped asset whose value is directly dependent on the security and integrity of the underlying Avail token and the Wormhole bridge. Any vulnerability, exploit, or operational failure within the Wormhole bridge could lead to a de-pegging event, where the wrapped token loses its backing and value. This is an inherent risk for bridged assets and is outside the scope of this contract's direct control.

**Recommendation:** Conduct continuous monitoring and due diligence on the security posture of the Wormhole bridge. Establish clear emergency response plans in case of a bridge compromise. Users should be made fully aware of the risks associated with relying on external bridging solutions.


### `L-01` — Lack of Emergency Pause Mechanism  *(Severity: Low · Status: Unresolved)*

The contract lacks a mechanism to pause critical operations (e.g., transfers, minting, burning) in emergency situations. While not strictly required for a basic ERC20, a pause function can be crucial for mitigating damage during unforeseen events, such as a critical vulnerability discovery, a bridge exploit affecting the underlying asset, or other black swan events.

**Recommendation:** Consider implementing an `PausableUpgradeable` mechanism from OpenZeppelin. This would allow a designated role (e.g., the `DEFAULT_ADMIN_ROLE` or a dedicated `PAUSER_ROLE` controlled by the multisig) to temporarily halt contract operations, providing a safety switch during emergencies.


### `I-01` — Usage of `reinitializer(2)`  *(Severity: Informational · Status: Unresolved)*

The `initialize()` function uses `reinitializer(2)`. This allows the function to be called multiple times during the contract's lifecycle, specifically after an upgrade, as long as the version number is incremented. While this is an intended feature for complex upgrade scenarios in OpenZeppelin's upgradeable pattern, it requires careful management to prevent unintended re-initialization or state corruption if not used correctly.

**Recommendation:** Ensure that all future upgrades correctly manage the initializer versioning. Document the intended use cases for re-initialization and ensure that any state changes made during re-initialization are thoroughly tested and do not conflict with existing storage or logic.


### `I-02` — Correct Use of `_disableInitializers()` in Constructor  *(Severity: Informational · Status: Unresolved)*

The contract correctly calls `_disableInitializers()` in its constructor. This is a crucial best practice for upgradeable contracts, as it prevents the constructor from being called on the implementation contract directly, which could lead to a 'shadow' state or bypass initialization logic when the contract is deployed as an implementation behind a proxy.

**Recommendation:** No action required. This is a correctly implemented best practice.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd89d...057a`](https://basescan.org/address/0xd89d90d26b48940fa8f58385fe84625d468e057a) |
| **Network** | Base |
| **Price** | $0.002466 |
| **24h Volume** | $75.6K |
| **Liquidity** | $71.8K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 94.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 719 buys / 716 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xff0df9b15c29542fa5d7efe169452507b4d648c2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/avail-wormhole-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-12*
