---
token: Kyber Network Crystal v2
ticker: KNC
network: ethereum
risk_score: 80
status: high
date: 2026-09-14
---

# Kyber Network Crystal v2 (KNC) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 80/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kyber-network-crystal-v2-eth)

---

## Audit Summary

The Kyber Network Crystal v2 (KNC) token contract, implemented as an upgradeable ERC20, was audited for security vulnerabilities. The contract leverages OpenZeppelin's upgradeable standards for token functionality and access control. Key features include a dedicated minter role, a migration mechanism from an old KNC token, and an owner-controlled emergency drain function. While the architecture is standard for upgradeable tokens, a significant access control issue was identified where the owner lacks direct control over the minter role, posing a centralization risk. A potential reentrancy vector in the migration function was also noted.

> **Final Recommendation:** It is strongly recommended to review and adjust the access control mechanisms, particularly concerning the `minter` role. The `owner` should have the ability to revoke or reassign the `minter` to mitigate the risk of a single point of failure. Additionally, the `mintWithOldKnc` function should be refactored to adhere to the Checks-Effects-Interactions pattern to prevent potential reentrancy. Implementing these changes will significantly enhance the contract's security posture and reduce governance risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes well-vetted OpenZeppelin upgradeable libraries for ERC20, Ownable, and Burnable functionalities, enhancing code security (7.2). The use of `SafeERC20` for external transfers… |
| **Governance / Economics** | 2/10 | High | The contract defines distinct `owner` and `minter` roles for access control (7.3). The `owner` has the power to recover accidentally sent ERC20 tokens via `emergencyERC20Drain`, which is a positive… |
| **Upgrades** | 1/10 | High | The contract is designed as an upgradeable proxy using OpenZeppelin's `AdminUpgradeabilityProxy` and `initializer` pattern, which is a robust architecture (7.1, 7.7). The `owner` and… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Other-Contract |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 1 Informational_

### `M-01` — Potential Reentrancy in `mintWithOldKnc`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `mintWithOldKnc` function performs an external call `IERC20Burnable(oldKNC).burnFrom(msg.sender, amount)` before updating the contract's internal state (`super._mint(msg.sender, amount)`). This violates the Checks-Effects-Interactions pattern (7.2, 7.6). If the `oldKNC` token contract is malicious or has a reentrant `burnFrom` implementation, it could potentially call back into `mintWithOldKnc` before the `_mint` operation completes, leading to `msg.sender` receiving more new KNC tokens than intended for a single burn.

**Recommendation:** Reorder the operations within `mintWithOldKnc` to follow the Checks-Effects-Interactions pattern. First, perform all checks, then update the contract's state (mint the new tokens), and finally, interact with external contracts (burn the old tokens). Consider adding a reentrancy guard if the `oldKNC` contract is not fully trusted.


### `M-02` — Minter Role Autonomy and Owner's Limited Control  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `changeMinter` function is restricted to `onlyMinter`, meaning only the current `minter` address can transfer the `minter` role. The contract `owner` (who controls upgrades and `emergencyERC20Drain`) cannot directly revoke or reassign the `minter` role. This creates a significant access control limitation for the `owner` and a single point of failure for token supply control (7.3, 7.5).

**Recommendation:** Modify the `changeMinter` function to allow the `owner` to also change the `minter` role. Alternatively, implement a multi-signature wallet for the `minter` role or a time-locked mechanism for `minter` changes to provide a recovery mechanism and enhance security.


### `I-01` — Centralized Control of Critical Roles  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `minter` role has the sole authority to mint new tokens, and the `owner` role has the sole authority to drain any ERC20 tokens accidentally sent to the contract (7.1, 7.3). While these are standard patterns for token contracts, they represent significant centralized control. Compromise of the `minter` key leads to arbitrary token minting, and compromise of the `owner` key leads to loss of funds sent to the contract.

**Recommendation:** For critical roles like `minter` and `owner`, consider implementing multi-signature wallets or a robust governance mechanism to distribute control and reduce the risk associated with a single point of failure.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xdefa...7202`](https://etherscan.io/address/0xdefa4e8a7bcba345f687a2f1456f5edd9ce97202) |
| **Network** | Ethereum |
| **Price** | $0.1389 |
| **24h Volume** | $142.8K |
| **Liquidity** | $845.4K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 3d |
| **Top-10 Holders** | 67.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 240 buys / 60 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x115103a95a279b80b66c993a853495a94fe3cf2c7baa054959c4ed511c5d76e6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kyber-network-crystal-v2-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-14*
