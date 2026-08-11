---
token: Yield Basis
ticker: YB
network: ethereum
risk_score: 42
status: medium
date: 2026-08-11
---

# Yield Basis (YB) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 42/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/yield-basis-eth)

---

## Audit Summary

The YBToken contract implements a custom ERC-20 token with an exponential emission schedule. The audit identified a critical bug in the emission calculation formula, which could lead to incorrect token minting or system failure. A high-severity access control issue exists where the emission mechanism can be permanently disabled if the minter role is not correctly configured before ownership is renounced. The contract also uses an outdated Vyper compiler version, increasing potential risks.

> **Final Recommendation:** Address the critical emission calculation bug immediately, as it directly impacts the core functionality and economic model of the token. Implement robust deployment procedures to ensure the designated minter is correctly authorized *before* ownership is renounced, preventing the irreversible bricking of the emission mechanism. Consider migrating the contract to a modern, audited Vyper version to benefit from security improvements and reduce the risk of compiler-related vulnerabilities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract implements a custom ERC-20 token with an exponential emission model. The architecture is straightforward, leveraging `snekmate` libraries for standard ERC-20 and ownership… |
| **Governance / Economics** | 4/10 | Medium | The economic model is based on a continuous exponential emission schedule, designed to deplete a fixed `reserve` over time. The `max_mint_rate` and `reserve` are set at deployment, making the core… |
| **Upgrades** | 8/10 | Low | The contract is not designed with upgradeability in mind, meaning its logic is immutable once deployed. This eliminates risks associated with upgrade mechanisms (7.7 Upgrades) but also prevents any… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 91.1% |
| **Top-3 Unlocked** | ⚠️ 99.5% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Critical Emission Calculation Bug  *(Severity: Critical · Status: Unresolved)*

The `_emissions` function, central to the token's supply mechanism, contains a syntax error and a potential logical flaw in the argument passed to `math._wad_exp`. The line `reserve * (10**18 - math._wad_exp(-dt * rate_36 uint256))` is syntactically incorrect (the `uint256` after `rate_36` is misplaced) and `rate_36` is calculated as `max_mint_rate * rate_factor`, where `max_mint_rate` is already scaled by `10**18`. This over-scaling of the `_wad_exp` argument could lead to `_wad_exp` returning 0 prematurely, causing `amount` to be equal to `reserve` (minting the entire reserve in one go), or causing reverts due to extreme input values, effectively bricking the emission mechanism.

**Recommendation:** Correct the syntax error in the `_emissions` function. Carefully review the scaling of `rate_36` and the expected input for `math._wad_exp` to ensure the emission formula behaves as intended. The argument to `_wad_exp` typically represents a rate per unit time, often requiring division by `10**18` if the rate itself is WAD-scaled.


### `H-01` — Irreversible Minter Bricking Risk  *(Severity: High · Status: Unresolved)*

The `renounce_ownership` function transfers ownership to the zero address, making the contract ownerless. Concurrently, it sets `erc20.is_minter[msg.sender] = False`, revoking the deployer's minting privileges. If the `set_minter` function (which is owner-restricted) is not called by the deployer *before* renouncing ownership to grant minting rights to a designated entity (like a `GaugeController`), the contract will become permanently unable to mint new tokens, rendering its core emission functionality inoperable.

**Recommendation:** Ensure that the `set_minter` function is called by the deployer to authorize the intended minter (e.g., `GaugeController`) *before* `renounce_ownership` is executed. Implement clear deployment and post-deployment procedures to prevent this critical misconfiguration. Consider adding a check in `renounce_ownership` to ensure at least one minter is active before allowing ownership renunciation, or allow a specific role to set minters even after ownership is renounced (though this goes against the…


### `M-01` — Outdated Vyper Version and Libraries  *(Severity: Medium · Status: Unresolved)*

The contract is compiled with Vyper 0.4.3, which is an outdated version of the language. This version may contain known or undiscovered compiler bugs and lacks modern security features and optimizations present in current Vyper releases. Additionally, the `snekmate` libraries used are likely also outdated, potentially introducing further vulnerabilities or non-standard behaviors.

**Recommendation:** Migrate the contract to a modern, audited Vyper version (e.g., 0.3.x) and update to actively maintained and audited libraries. Thoroughly re-audit the contract after migration to ensure no new issues are introduced and all existing logic remains correct.


### `L-01` — Lack of Emergency Pause Mechanism  *(Severity: Low · Status: Unresolved)*

The contract lacks a mechanism to pause critical functions like `emit` in case of an emergency, such as a discovered vulnerability or an economic exploit. This could leave the protocol vulnerable to rapid exploitation without a way to mitigate ongoing damage.

**Recommendation:** Consider implementing a pause mechanism for the `emit` function. This mechanism should be controlled by a trusted multi-signature wallet or a governance process, allowing for a temporary halt of emissions in emergencies. Given the ownerless design, this would need to be integrated carefully, perhaps allowing a designated `GaugeController` or a separate governance contract to trigger a pause.


### `I-01` — Implicit Trust in Designated Minter  *(Severity: Informational · Status: Unresolved)*

The contract's design, particularly after ownership renunciation, places implicit trust in an external `GaugeController` (or similar designated minter) to manage token emissions responsibly. The `emit` function's `rate_factor` parameter allows the minter to control the percentage of inflation. The security of the token's supply and economic model heavily relies on the designated minter's implementation, its own access controls, and its resistance to manipulation.

**Recommendation:** Conduct a thorough audit of the `GaugeController` contract (or any designated minter) that will interact with this `YBToken`. Ensure its access control mechanisms are robust, its logic is sound, and it cannot be manipulated to mint tokens maliciously or in an unintended manner.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0179...45ff`](https://etherscan.io/address/0x01791f726b4103694969820be083196cc7c045ff) |
| **Network** | Ethereum |
| **Price** | $0.07647 |
| **24h Volume** | $594.1K |
| **Liquidity** | $994.5K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 9mo |
| **Top-10 Holders** | 85.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 170 buys / 364 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xec977f46467a3021785cff88894886e617abd65b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/yield-basis-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
