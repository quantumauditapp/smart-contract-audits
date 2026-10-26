---
token: Fuse Cat
ticker: FUSECAT
network: ethereum
risk_score: 29
status: low
date: 2026-09-14
---

# Fuse Cat (FUSECAT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fuse-cat-eth)

---

## Audit Summary

The PairPadLauncherToken and PairPadLaunchDeployer contracts implement an ERC20 token with a temporary launch guard mechanism and a factory for its deployment. The contracts leverage OpenZeppelin standards and immutable variables for security. Key findings include centralized control over the guard list initialization, potential DoS for large guard lists, and reliance on an external configuration interface for guard parameters. The overall risk is assessed as Medium.

> **Final Recommendation:** It is recommended to carefully manage the `creator` address, as it holds significant power for the one-time initialization of the guard list. Consider implementing a multi-signature wallet for the `creator` role if the guard list is critical. Evaluate the potential gas costs for `initGuardList` with expected list sizes to ensure it remains within block gas limits. Thoroughly audit the `IGuardConfig` contract that the `PairPadLaunchDeployer` interacts with, as its security directly impacts the guard configuration of deployed tokens.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The technical architecture (7.1) is sound, utilizing OpenZeppelin's ERC20 and ERC20Burnable for core token functionality, which enhances code security (7.2). Immutable variables are used for critical… |
| **Governance / Economics** | 4/10 | Medium | Access control (7.3) for the `initGuardList` function is centralized to the `creator` address, allowing a single entity to define the initial guard whitelist. While this is a one-time action… |
| **Upgrades** | 9/10 | Low | The contracts are not designed to be upgradeable (7.7), meaning their logic is immutable once deployed. This simplifies the security model by eliminating risks associated with upgrade mechanisms… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Potential DoS for `initGuardList` with Large Input  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initGuardList` function iterates through the `list` array to set `guardAllowed` for each address. If the `list.length` is excessively large, the transaction could consume too much gas and exceed the block gas limit, leading to a denial-of-service (7.2) for the `creator` attempting to initialize the guard list. This would prevent the guard list from being set, potentially leaving the token in an unintended state regarding transfer restrictions.

**Recommendation:** Implement a maximum limit for the `list.length` parameter in `initGuardList` to prevent gas limit issues. Alternatively, consider a paginated approach or a Merkle tree for large whitelists if the list size is expected to be very large.


### `M-02` — Reliance on External `IGuardConfig` for Critical Parameters  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `PairPadLaunchDeployer` contract relies on an external interface, `IGuardConfig(factory)`, to fetch `guardSecondsOf` and `guardListOf` parameters for newly deployed tokens (7.6). If the `factory` contract (which implements `IGuardConfig`) is compromised or returns incorrect values, it could lead to tokens being deployed with unintended or malicious guard configurations, affecting their transferability and economic behavior (7.4). This introduces a trust dependency on the security of the `factory` contract.

**Recommendation:** Ensure that the `factory` contract implementing `IGuardConfig` is thoroughly audited and secured. Implement robust validation or circuit breakers in the `PairPadLaunchDeployer` if possible, to mitigate risks from a potentially compromised `IGuardConfig` interface, although direct validation of external contract logic is challenging.


### `M-03` — Centralized Control Over Guard List Initialization  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initGuardList` function, which sets the whitelist for transfers during the guard period, can only be called once by the `creator` (the `msg.sender` of the constructor). If the `creator` address is compromised, a malicious actor could set an arbitrary guard list, potentially allowing unauthorized transfers during the active guard period. Although the guard period is short (60 seconds), this is a critical access control point (7.3).

**Recommendation:** If the `creator` address is an EOA, consider using a multi-signature wallet for this role to enhance security. Ensure robust key management practices for the `creator` address. Alternatively, if the guard list is intended to be immutable and known at deployment, consider passing it directly in the constructor.


### `L-01` — Very Short Guard Window Limits Effectiveness  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `MAX_GUARD_SECONDS` constant is set to 60 seconds. While a short guard period limits the duration of potential issues related to the guard mechanism, it also significantly reduces its practical effectiveness (7.4) in providing a meaningful 'launch guard' against immediate post-launch volatility, sniping, or other rapid market manipulations. The guard's utility as a protective measure is minimal due to its brevity.

**Recommendation:** Review the intended purpose and desired duration of the launch guard. If a longer protection period is desired, consider increasing `MAX_GUARD_SECONDS`. If the current duration is intentional, ensure this limitation is clearly communicated to users.


### `I-01` — `owner()` Function Returns `address(0)`  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `owner()` function, commonly found in OpenZeppelin's `Ownable` contracts, is implemented to explicitly return `address(0)` (7.5). This design choice indicates that the token contract itself does not have a single owner with special privileges post-deployment. While this promotes decentralization, it might be unexpected for users familiar with `Ownable` patterns and means no single entity can perform administrative actions on the token contract (e.g., pausing, upgrading, if it were a proxy).

**Recommendation:** Ensure that this design choice aligns with the project's decentralization goals and that users are aware of the lack of a traditional owner for the token contract. No action is required if this is the intended design.


### `I-02` — Metadata String Length Limits Enforced  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `PairPadLaunchDeployer` contract enforces maximum length limits for metadata fields such as `MAX_NAME_LENGTH`, `MAX_SYMBOL_LENGTH`, `MAX_LOGO_LENGTH`, `MAX_DESCRIPTION_LENGTH`, and `MAX_SOCIAL_LENGTH` (7.2). This is a good practice to prevent excessive gas costs associated with storing and processing very long strings, and to ensure the generated JSON metadata remains manageable. It also helps prevent potential denial-of-service vectors related to oversized data.

**Recommendation:** No specific action is required as this is a positive security measure. Ensure that these limits are appropriate for the intended use cases and user experience.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x926e...1111`](https://etherscan.io/address/0x926e5912181e849e0a08599d18e9c17aa0a11111) |
| **Network** | Ethereum |
| **Price** | $0.00005776 |
| **24h Volume** | $132.2K |
| **Liquidity** | $32.2K |
| **Volume / Liquidity** | 4.1× |
| **Token Age** | 2d |
| **Top-10 Holders** | 52.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 521 buys / 378 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x031804b9dc7dd6efa4abc3f17f4f3e7b4f9bd20daa2d404bb69928adafe2c8b7)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fuse-cat-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-14*
