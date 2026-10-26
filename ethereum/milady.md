---
token: Milady
ticker: LADYS
network: ethereum
risk_score: 19
status: low
date: 2026-09-22
---

# Milady (LADYS) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 19/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/milady-eth)

---

## Audit Summary

The LadysToken contract is an ERC20 token with custom features for blacklisting and holding limits. The audit identified a critical vulnerability related to unchecked arithmetic for token balances and total supply, which could lead to severe financial loss. High-risk issues include centralized control via blacklisting and potentially problematic `minHoldingAmount` logic.

> **Final Recommendation:** Address the critical unchecked arithmetic vulnerability by removing `unchecked` blocks for additions to `_totalSupply` and `_balances` to ensure overflow protection. Re-evaluate the `minHoldingAmount` logic to clarify its intended behavior and potential impact on user experience. Consider implementing a multi-signature wallet for ownership to mitigate centralized control risks and enhance security for critical functions like blacklisting and rule changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract implements a standard ERC20 token with custom transfer hooks for blacklisting and holding limits. It leverages Solidity 0.8.0+ features. A critical vulnerability exists where `unchecked`… |
| **Governance / Economics** | 4/10 | Medium | The contract uses the Ownable pattern, granting the deployer significant centralized control over key parameters. The owner can blacklist any address, including users or the LP pair, posing a high… |
| **Upgrades** | 7/10 | Low | The contract is not designed to be upgradeable, which simplifies its architecture by avoiding proxy-related complexities. This eliminates risks associated with upgradeability patterns such as storage… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.8% (≈ permanent lock) |
| **LP Locked** | 99.8% — Null Address |

## Security Findings

_🟡 4 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Holding Limit Bypass for Direct Transfers  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `limited` holding amount rules (`maxHoldingAmount`, `minHoldingAmount`) are only enforced when tokens are transferred `from == uniswapV2Pair`. This design allows users to bypass these limits by transferring tokens directly between wallets or by transferring tokens *to* the LP pair without restriction. While this might be an intentional design choice, it reduces the overall effectiveness of the holding limits if the goal is to restrict total holdings.

**Recommendation:** If the intention is to enforce holding limits universally, modify the `_beforeTokenTransfer` logic to apply `maxHoldingAmount` and `minHoldingAmount` checks to all transfers, regardless of the `from` address. If the current behavior is intentional, document this limitation clearly.


### `M-02` — Unchecked Arithmetic for Total Supply and Balances  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_mint`, `_burn`, and `_transfer` functions explicitly use `unchecked` blocks for additions to `_totalSupply` and `_balances`. In Solidity 0.8.0+, arithmetic operations default to checked, preventing overflows. By using `unchecked` for additions, if `_totalSupply` or any account's `_balances` were to exceed `type(uint256).max`, the value would wrap around to zero. This could lead to an incorrect total supply, token inflation, or users losing their tokens due to balance manipulation.

**Recommendation:** Remove the `unchecked` blocks around additions to `_totalSupply` and `_balances` in `_mint`, `_burn`, and `_transfer` functions. Allow Solidity's default checked arithmetic to prevent overflows, which is the safer behavior for token balances.


### `M-03` — Centralized Control and Blacklisting Risk  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract utilizes the `Ownable` pattern, granting the deployer (owner) exclusive control over critical functions. Specifically, the `blacklist` function allows the owner to prevent any address from sending or receiving tokens. This introduces a high level of centralization, enabling potential censorship, freezing of user funds, or manipulation of market dynamics by blacklisting liquidity pools or exchanges.

**Recommendation:** Consider decentralizing control by implementing a multi-signature wallet or a time-locked contract for ownership. If blacklisting is deemed necessary, define clear, transparent criteria for its use and consider a community-governed mechanism or a timelock for such actions to reduce immediate impact.


### `M-04` — Ambiguous/Problematic `minHoldingAmount` Logic  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_beforeTokenTransfer` function includes a `minHoldingAmount` check (`super.balanceOf(to) + amount >= minHoldingAmount`) that applies only to transfers originating `from == uniswapV2Pair`. If `minHoldingAmount` is set to a non-zero value, it could prevent users from acquiring tokens from the LP if their resulting balance would be below this threshold. This could effectively lock out smaller investors or create unexpected barriers to entry for legitimate token acquisition.

**Recommendation:** Clarify the intended purpose of `minHoldingAmount`. If it's meant to ensure a minimum holding, consider if applying it only to transfers from the LP is the desired behavior. If the goal is to prevent users from holding less than a certain amount, the logic might need to be adjusted to cover all transfers or be removed if it creates unintended restrictions.


### `L-01` — Lack of Event for `setRule` Function  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `setRule` function, which modifies critical parameters such as `limited`, `uniswapV2Pair`, `maxHoldingAmount`, and `minHoldingAmount`, does not emit an event. This makes it difficult for off-chain applications, block explorers, and users to track changes to these important contract configurations, hindering transparency and auditability.

**Recommendation:** Emit an event (e.g., `RuleSet(bool limited, address uniswapV2Pair, uint256 maxHoldingAmount, uint256 minHoldingAmount)`) whenever the `setRule` function is called. This will provide a clear, auditable history of parameter changes.


### `I-01` — Fixed Decimals Value  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `decimals()` function is hardcoded to return `18`. While 18 decimals is a common standard for ERC20 tokens, this value cannot be changed after deployment. This is an observation rather than a vulnerability.

**Recommendation:** No action required if 18 decimals is the intended and permanent configuration.


### `I-02` — Initial Token Distribution to EOAs  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The constructor mints a significant portion of the total supply (94% to `_lpWallet`, 1% to `_airdropWallet`, 5% to `_ecoWallet`) to specific addresses. If these addresses are Externally Owned Accounts (EOAs), they represent single points of failure for the initial token distribution and control over a large supply.

**Recommendation:** Consider using multi-signature wallets or timelock contracts for these critical distribution addresses to enhance security and reduce the risk associated with a single point of control.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1297...46bf`](https://etherscan.io/address/0x12970e6868f88f6557b76120662c1b3e50a646bf) |
| **Network** | Ethereum |
| **Price** | $0.00000001 |
| **24h Volume** | $40.4K |
| **Liquidity** | $937.7K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 3y |
| **Top-10 Holders** | 73.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 87 buys / 82 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xcbe856765eeec3fdc505ddebf9dc612da995e593)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/milady-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-22*
