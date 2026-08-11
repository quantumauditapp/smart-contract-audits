---
token: ETHGas
ticker: GWEI
network: bsc
risk_score: 94
status: critical
date: 2026-08-11
---

# ETHGas (GWEI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 94/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ethgas-bsc)

---

## Audit Summary

The audit of the BridgeToken implementation contract identified a critical access control vulnerability: the contract owner, who controls minting, burning, and metadata updates, cannot be changed after initialization. This poses a severe operational and security risk. Other findings include centralized control over metadata, standard ERC-20 `approve` race condition, and missing transfer hooks. The contract generally exhibits good code quality and utilizes state separation for upgradeability.

> **Final Recommendation:** It is imperative to address the critical issue of irreversible ownership. Implement a robust ownership management system, preferably using a multi-signature wallet or a well-audited governance contract for the owner role, to ensure operational continuity and security. Review the necessity of the `updateDetails` function and consider if its control should also be subject to multi-sig or governance. Adopting OpenZeppelin's `ERC20` base contract could provide additional security features and extensibility.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract demonstrates good architectural practices by separating state into `TokenState` and utilizing OpenZeppelin libraries for secure primitives (7.1 Architecture, 7.2 Code Security). However… |
| **Governance / Economics** | 1/10 | High | The economic model centers on an owner-controlled mint/burn mechanism, which is typical for a bridge token (7.4 Economic). However, the inability to transfer ownership (7.5 Governance) creates a… |
| **Upgrades** | 1/10 | High | The contract is designed as an upgradeable implementation for a Beacon Proxy, correctly using an `initializer` modifier and separating state into `TokenState`, which are strong practices for upgrade… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Irreversible Owner Assignment  *(Severity: Critical · Status: Unresolved)*

The `_state.owner` variable, which controls critical functions like `mint`, `burn`, and `updateDetails`, is set only during the `initialize` function and lacks any mechanism (e.g., `transferOwnership`) to change it. This means the initial owner address is permanently fixed.

**Recommendation:** Implement a robust ownership management mechanism, such as inheriting from OpenZeppelin's `Ownable` and including `transferOwnership` and `renounceOwnership` functions. For critical roles, consider using a multi-signature wallet or a well-tested governance contract to manage ownership.


### `M-01` — Centralized Control over Token Metadata  *(Severity: Medium · Status: Unresolved)*

The `updateDetails` function allows the `owner` to change the token's `name` and `symbol` at any time. While this might be intended for a bridge token to reflect changes on the native chain, it introduces a centralization risk where the owner can arbitrarily change the token's identity, potentially misleading users or exchanges.

**Recommendation:** Consider if this functionality is strictly necessary. If so, ensure robust governance or multi-sig control over the owner address. Document this capability clearly for users and integrate it into the protocol's risk disclosure.


### `L-01` — ERC-20 `approve` Race Condition  *(Severity: Low · Status: Unresolved)*

The `approve` function, like all standard ERC-20 `approve` implementations, is susceptible to a known front-running attack where a user's allowance can be manipulated if they approve a new amount before the spender spends the old amount. This can lead to the spender having access to an unintended amount.

**Recommendation:** While not a critical vulnerability, users should be aware of this ERC-20 standard limitation. Encourage the use of `increaseAllowance` and `decreaseAllowance` functions, which mitigate this risk, instead of direct `approve` calls when adjusting allowances.


### `I-01` — Missing `_beforeTokenTransfer` Hook  *(Severity: Informational · Status: Unresolved)*

The contract implements core ERC-20 logic directly without inheriting from OpenZeppelin's `ERC20` contract. This means it lacks the `_beforeTokenTransfer` and `_afterTokenTransfer` hooks, which are useful for adding custom logic (e.g., blacklisting, fee mechanisms, snapshotting) in future upgrades without modifying core transfer logic.

**Recommendation:** Consider inheriting from OpenZeppelin's `ERC20` contract or implementing similar internal hooks if future extensibility for custom transfer logic is desired. This can improve modularity and upgradeability.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3011...7d49`](https://bscscan.com/address/0x30117e4bc17d7b044194b76a38365c53b72f7d49) |
| **Network** | BNB Chain |
| **Price** | $0.02514 |
| **24h Volume** | $51.1K |
| **Liquidity** | $30.4K |
| **Volume / Liquidity** | 1.7× |
| **Token Age** | 6mo |
| **Top-10 Holders** | 98.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 819 buys / 767 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xa8d956401d161f61418576b375b4fdaf0e76155f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ethgas-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
