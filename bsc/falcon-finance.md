---
token: Falcon Finance
ticker: FF
network: bsc
risk_score: 78
status: critical
date: 2026-08-12
---

# Falcon Finance (FF) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 78/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/falcon-finance-bsc)

---

## Audit Summary

The BurnMintERC20 contract implements a standard ERC-20 token with minting and burning capabilities, leveraging OpenZeppelin's AccessControl for role management. The contract exhibits good adherence to established patterns and includes checks to prevent self-locking of tokens. However, a critical design flaw exists where initializing the token with a `maxSupply` of zero effectively bypasses the maximum supply limit, allowing for unlimited minting. Additionally, the contract relies on a centralized `DEFAULT_ADMIN_ROLE` for critical operations, posing a single point of control risk. Immutable token parameters, while providing stability, also limit future adaptability.

> **Final Recommendation:** It is crucial to ensure that the `maxSupply_` parameter in the constructor is always initialized to a non-zero value greater than `preMint` if a maximum supply limit is intended. Implement robust operational procedures for the `DEFAULT_ADMIN_ROLE` to mitigate the risks associated with centralized control, including multi-signature wallets or time-locks for critical actions. Consider the implications of immutable parameters and ensure they align with long-term project goals before deployment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract is built upon well-audited OpenZeppelin libraries (ERC20, ERC20Burnable, AccessControl), contributing to strong code security (7.2). It includes robust checks in `_transfer`, `_approve`… |
| **Governance / Economics** | 1/10 | High | The economic model (7.4) is based on a standard ERC-20 token with a configurable maximum supply and pre-minting. A key economic risk is the potential for unlimited token supply if `i_maxSupply` is… |
| **Upgrades** | 3/10 | High | The contract is not designed as an upgradeable proxy (7.7). Therefore, there are no specific upgrade safety issues to assess. Any changes to the contract logic would require a new deployment and… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.4% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 1 Informational_

### `H-01` — Max Supply Bypass if Zero  *(Severity: High · Status: Unresolved)*

The `mint` function includes a check `if (i_maxSupply != 0 && totalSupply() + amount > i_maxSupply) revert MaxSupplyExceeded(...)`. If `i_maxSupply` is initialized to `0` in the constructor, the condition `i_maxSupply != 0` evaluates to `false`. Due to short-circuiting in the `&&` operator, the second part of the condition (`totalSupply() + amount > i_maxSupply`) is never evaluated. This effectively bypasses the maximum supply check, allowing for an unlimited supply of tokens to be minted if `maxSupply_` is set to `0` during deployment, contrary to the apparent intent of having a `maxSupply` parameter.

**Recommendation:** Modify the `mint` function's condition to explicitly check for a positive `maxSupply` before enforcing the limit. For example, change `if (i_maxSupply != 0 && ...)` to `if (i_maxSupply > 0 && ...)` or restructure the logic to handle `i_maxSupply == 0` as an 'unlimited' case if that is the intended behavior, or revert in the constructor if `maxSupply_` is 0 and a limit is always expected.


### `M-01` — Centralized Control by DEFAULT_ADMIN_ROLE  *(Severity: Medium · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE` holds significant power within the contract. The address with this role can grant and revoke `MINTER_ROLE` and `BURNER_ROLE`, effectively controlling the token's supply. Additionally, the `setCCIPAdmin` function, which transfers the `s_ccipAdmin` role, is also restricted to the `DEFAULT_ADMIN_ROLE`. This centralization introduces a single point of failure, where compromise of the `DEFAULT_ADMIN_ROLE` key could lead to unauthorized minting, burning, or administrative changes.

**Recommendation:** Consider implementing a multi-signature wallet for the `DEFAULT_ADMIN_ROLE` to distribute control and reduce the risk associated with a single point of failure. For critical operations like granting/revoking roles or changing the `ccipAdmin`, consider adding time-locks to allow for community review or emergency intervention periods.


### `I-01` — Immutable Token Parameters  *(Severity: Informational · Status: Unresolved)*

The `i_decimals` and `i_maxSupply` variables are declared as `immutable`, meaning their values are set once in the constructor and cannot be changed thereafter. While this provides stability and predictability for the token's core properties, it also means that these parameters cannot be adjusted in the future, even if unforeseen circumstances or evolving protocol requirements necessitate a change.

**Recommendation:** Ensure that the chosen `decimals` and `maxSupply` values are thoroughly reviewed and confirmed to meet all current and anticipated future requirements of the protocol. If future flexibility for these parameters is desired, consider an upgradeable contract pattern or a mechanism to migrate to a new token contract.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xac23...4db2`](https://bscscan.com/address/0xac23b90a79504865d52b49b327328411a23d4db2) |
| **Network** | BNB Chain |
| **Price** | $0.06531 |
| **24h Volume** | $7.19M |
| **Liquidity** | $3.76M |
| **Volume / Liquidity** | 1.9× |
| **Token Age** | 10mo |
| **Top-10 Holders** | 97.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4856 buys / 4611 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x9f8f4615ff5143aee365fa34f34196fb85be7650)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/falcon-finance-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-12*
