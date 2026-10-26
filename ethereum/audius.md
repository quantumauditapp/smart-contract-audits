---
token: Audius
ticker: AUDIO
network: ethereum
risk_score: 59
status: medium
date: 2026-09-28
---

# Audius (AUDIO) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 59/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/audius-eth)

---

## Audit Summary

The AudiusToken contract, deployed as an upgradeable proxy, contains critical vulnerabilities related to its initialization mechanism and access control. The `proxyAdmin` variable, crucial for initialization, is never set, preventing the contract from being properly initialized. Additionally, the `addMinter` and `addPauser` functions lack access control, allowing any caller to grant themselves or others powerful roles, leading to unauthorized token minting or pausing of all token operations. These issues pose severe risks to the token's functionality, integrity, and security.

> **Final Recommendation:** Immediately address the critical initialization flaw by ensuring the `proxyAdmin` variable in the `Initializable` contract is correctly set during deployment or by adopting a standard, audited `Initializable` contract from a reputable library like OpenZeppelin. Implement robust access control for all role management functions (`addMinter`, `removeMinter`, `addPauser`, `removePauser`), restricting their execution to a trusted owner or multi-signature wallet. Consider upgrading the Solidity compiler version to `0.8.x` or higher to benefit from built-in overflow checks and other security enhancements.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract utilizes the SafeMath library, which effectively prevents integer overflow/underflow vulnerabilities (7.2 Code Security). However, a critical flaw exists where the `proxyAdmin` variable… |
| **Governance / Economics** | 2/10 | High | The economic model relies on controlled minting and pausing capabilities. While the `_mint` and `_burn` functions are internal and `pause`/`unpause` are restricted by `onlyPauser` (7.4 Economic), the… |
| **Upgrades** | 1/10 | High | The contract is designed to be upgradeable via a UUPS proxy pattern, indicated by the `Initializable` base contract and `______gap` variables for storage compatibility (7.7 Upgrades). However, the… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.3% |
| **Top-3 Unlocked** | ⚠️ 99.9% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low_

### `M-01` — Unset `proxyAdmin` Prevents Contract Initialization  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `Initializable` base contract includes a private state variable `proxyAdmin` which is checked in the `initializer` modifier (`require(msg.sender == proxyAdmin, "Only proxy admin can initialize")`). However, this `proxyAdmin` variable is never assigned a value within the provided contract code. As a result, `proxyAdmin` defaults to `address(0)`. This makes it impossible for the `AudiusToken`'s `initialize` function to ever be called successfully, as `msg.sender` can never be `address(0)` in a transaction. This prevents the token from being properly configured (name, symbol, decimals, initial supply, minters, pausers

**Recommendation:** Ensure the `proxyAdmin` variable in the `Initializable` contract is correctly set during the deployment or initialization process. A common pattern for UUPS proxies is to not have an `Initializable` contract with its own `proxyAdmin` for initialization, but rather rely on the proxy's admin for upgrade authorization. If this `proxyAdmin` is intended for initialization, it must be set via a constructor or an accessible setter function, or consider using a battle-tested `Initializable` contract fr…


### `M-02` — Public `addMinter` and `addPauser` Functions Lack Access Control  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `addMinter(address account)` and `addPauser(address account)` functions in `MinterRole` and `PauserRole` contracts, respectively, are declared `public` and do not include any access control modifiers (e.g., `onlyOwner`, `onlyAdmin`). This allows any external caller to invoke these functions and grant themselves or any arbitrary address the `Minter` or `Pauser` role. A malicious actor could become a Minter to mint an unlimited supply of tokens, or become a Pauser to halt all token transfers, minting, and burning operations, leading to severe economic manipulation or denial of service.

**Recommendation:** Implement strict access control for `addMinter`, `removeMinter`, `addPauser`, and `removePauser` functions. These functions should only be callable by a highly trusted entity, such as a contract owner (e.g., `onlyOwner` modifier) or a multi-signature wallet. Consider a robust governance mechanism for managing these critical roles.


### `M-03` — Potential for Re-initialization of Roles  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). While the main `AudiusToken.initialize` function is protected by the `initializer` modifier, the `MinterRole.initialize` and `PauserRole.initialize` functions are also `public initializer`. If the critical initialization flaw (C-01) were resolved, and assuming the `proxyAdmin` is set, these role-specific `initialize` functions could potentially be called directly via `delegatecall` from the proxy by an attacker if the `proxyAdmin` is compromised or if the `initializer` modifier's `initialized` check is bypassed in a specific scenario. This could lead to re-setting the initial minter or pauser, potentially overriding le

**Recommendation:** Ensure that role-specific `initialize` functions are either internal and called only once by the main contract's `initialize` function, or that their `initializer` modifier correctly prevents re-execution in all upgrade scenarios. A robust `Initializable` pattern should prevent any `initialize` function from being called more than once on the same logical contract instance.


### `L-01` — Use of Older Solidity Compiler Version  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract is compiled with Solidity version `^0.5.0`. While `SafeMath` is used to mitigate integer overflow/underflow, newer Solidity versions (e.g., `0.8.x` and above) include built-in overflow/underflow checks by default, reducing reliance on external libraries for this specific concern. Newer compilers also offer various optimizations, bug fixes, and improved security features.

**Recommendation:** Consider upgrading the Solidity compiler version to `0.8.x` or higher. This would allow for the removal of `SafeMath` (as arithmetic operations would revert on overflow/underflow by default) and provide access to the latest language features and security improvements. Thorough testing would be required after such an upgrade.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x18aa...b998`](https://etherscan.io/address/0x18aaa7115705e8be94bffebde57af9bfc265b998) |
| **Network** | Ethereum |
| **Price** | $0.01695 |
| **24h Volume** | $451.7K |
| **Liquidity** | $515.7K |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 6y |
| **Top-10 Holders** | 64.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 467 buys / 393 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xc730ef0f4973da9cc0ab8ab291890d3e77f58f79)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/audius-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-28*
