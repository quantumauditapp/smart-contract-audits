---
token: Zest
ticker: ZEST
network: base
risk_score: 49
status: high
date: 2026-08-11
---

# Zest (ZEST) — Smart Contract Security Analysis | Base

> **Risk Score: 49/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/zest-base)

---

## Audit Summary

The FactoryBurnMintERC20 contract implements a standard ERC20 token with controlled minting and burning capabilities, leveraging well-audited OpenZeppelin and Chainlink libraries. The contract demonstrates robust technical security, including proper access control for sensitive operations and immutable supply limits. While a few minor informational and low-severity findings were identified, the overall risk posture is considered low, especially given the owner is a multisig.

> **Final Recommendation:** It is recommended to maintain strict security practices for the multisig controlling the owner role, including regular audits of its participants and operational procedures. While the deprecated ERC20 functions are minor, consider removing them for clarity and adherence to modern standards. For any future administrative roles, evaluate the potential for gas limit issues if the number of participants is expected to be very large.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract exhibits strong technical security (7.2 Code Security) by utilizing battle-tested OpenZeppelin and Chainlink libraries, and compiling with Solidity 0.8.x, which includes built-in… |
| **Governance / Economics** | 4/10 | Medium | The economic model (7.4 Economic) is straightforward, with an immutable `maxSupply` set at deployment, preventing uncontrolled inflation unless `maxSupply` is explicitly set to zero. Governance (7.5… |
| **Upgrades** | 4/10 | Medium | The contract is not designed as an upgradeable proxy (7.7 Upgrades). Therefore, there are no upgrade-specific risks such as proxy storage collisions or improper initialization. Any changes to the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟢 1 Low · ⚪ 2 Informational_

### `L-01` — Use of Deprecated ERC20 `increaseApproval`/`decreaseApproval` Functions  *(Severity: Low · Status: Unresolved)*

The contract includes `increaseApproval` and `decreaseApproval` functions, which are deprecated in modern ERC20 standards. While these functions correctly delegate to `increaseAllowance` and `decreaseAllowance` respectively, their presence can lead to confusion or suggest outdated practices to users and integrators.

**Recommendation:** Consider removing the `increaseApproval` and `decreaseApproval` functions. Users should be encouraged to interact directly with `increaseAllowance` and `decreaseAllowance` for clarity and adherence to current ERC20 best practices.


### `I-01` — Significant Centralized Control by Owner  *(Severity: Informational · Status: Unresolved)*

The `owner` role possesses extensive control over critical functions, including granting/revoking minter and burner roles, and setting the `ccipAdmin` address. This centralization means that a compromise of the owner's private key could lead to unauthorized minting, burning, or manipulation of the `ccipAdmin` role. The pre-filled data indicates the owner is a multisig, which significantly mitigates this risk (7.3 Access Control, 7.8 Operations).

**Recommendation:** While mitigated by a multisig, it is crucial to maintain robust security practices for the multisig signers. Regularly review and audit the multisig setup and its participants. Consider implementing time-locks for critical administrative actions if the protocol's risk profile increases.


### `I-02` — Potential Gas Limit Exceedance for Role Enumeration  *(Severity: Informational · Status: Unresolved)*

The `getMinters()` and `getBurners()` functions return an array of all addresses with the respective roles using `EnumerableSet.values()`. If the number of minters or burners were to grow excessively large (e.g., hundreds or thousands), calling these functions could potentially exceed the block gas limit, rendering them unusable (7.2 Code Security).

**Recommendation:** For roles that are expected to remain limited (e.g., administrative roles), this is a low concern. If the design ever anticipates a very large number of minters/burners, consider alternative methods for querying roles, such as individual `isMinter`/`isBurner` checks, or pagination if a UI needs to display all roles.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7297...7fc2`](https://basescan.org/address/0x7297968ffb753dd12e4f6b1f18d9865c76707fc2) |
| **Network** | Base |
| **Price** | $0.1645 |
| **24h Volume** | $1.15M |
| **Liquidity** | $179.0K |
| **Volume / Liquidity** | 6.4× |
| **Token Age** | 1y |
| **Top-10 Holders** | 99.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 8144 buys / 9323 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x3693022bd390e147d8dd89a05403c80ff21dd64b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/zest-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
