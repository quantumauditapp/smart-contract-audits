---
token: Relics
ticker: RELICS
network: ethereum
risk_score: 37
status: medium
date: 2026-08-11
---

# Relics (RELICS) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 37/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/relics-eth)

---

## Audit Summary

The RelicsToken contract implements an ERC20 token with custom logic for tracking 'active holders' and interacting with an NFT system. The audit identified a critical operational flaw related to the contract's configurability given its renounced ownership status, alongside a high-severity reentrancy risk. Several informational points regarding economic design and external dependencies were also noted. The prefill indicates ownership is renounced, which significantly impacts the contract's operational flexibility.

> **Final Recommendation:** It is crucial to ensure all critical configuration parameters (`relicsNFT`, `relicSyncPool`, `relicLocker`) are correctly set during the contract's deployment or immediately after, prior to ownership renunciation. Implement a robust reentrancy guard for the `_update` function to protect against re-entrant calls from external contracts during standard ERC20 transfers. Thoroughly review the economic implications of the fixed low token supply within the broader protocol context.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract demonstrates good adherence to ERC20 standards and uses OpenZeppelin's Ownable for access control (7.3). Custom error messages enhance clarity, and `unchecked` blocks for counters are… |
| **Governance / Economics** | 5/10 | Medium | The economic design includes a fixed, relatively low supply of 10,000 tokens (7.4 Economic), which could lead to high volatility. The `HOLDER_THRESHOLD` mechanism for 'active holders' is a core… |
| **Upgrades** | 8/10 | Low | The RelicsToken contract is not designed as an upgradeable proxy (7.7 Upgrades). It is a standard implementation contract, meaning its logic cannot be modified after deployment. This eliminates… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · ⚪ 1 Informational_

### `C-01` — Critical Unconfigurable Parameters Due to Renounced Ownership  *(Severity: Critical · Status: Unresolved)*

The `relicsNFT`, `relicSyncPool`, and `relicLocker` addresses are critical for the contract's functionality, enabling interactions with the NFT system and defining special accounts. These addresses are set via `onlyOwner` functions (`setRelicsNFT`, `setRelicSyncPool`, `setRelicLocker`). The prefill data indicates that ownership of the contract is renounced. If these parameters are not configured during the initial deployment transaction or immediately thereafter (before ownership renunciation), they can never be set, rendering core functionalities like `transferRelicToken`, `_update`'s `syncBalances` call, and `_syncHolder` exclusions permanently non-functional or severely limited. This rep…

**Recommendation:** Ensure that all critical configuration parameters (`relicsNFT`, `relicSyncPool`, `relicLocker`) are set either within the constructor or through `onlyOwner` functions immediately after deployment, and *before* ownership is renounced. A multi-signature wallet or a time-locked governance mechanism could be used to manage these settings if ownership is not renounced, but given the renounced status, initial setup is paramount. Consider a deployment script that atomically sets these values.


### `H-01` — Reentrancy Risk in `_update` via External Call to `IRelicsNFT.syncBalances`  *(Severity: High · Status: Unresolved)*

The `_update` function, which is called during every ERC20 transfer (e.g., `transfer`, `transferFrom`), makes an external call to `IRelicsNFT(nft).syncBalances(from, to)`. While the `_relicTransferInProgress` flag is used to prevent reentrancy specifically during `transferRelicToken` calls, it does not protect against re-entrant calls initiated by standard ERC20 transfers. If the `relicsNFT` contract is malicious or compromised, it could re-enter `RelicsToken` (e.g., by calling `transfer` again) before the `_update` function completes, leading to unexpected state changes or token manipulation (7.2 Code Security).

**Recommendation:** Implement a reentrancy guard (e.g., OpenZeppelin's `ReentrancyGuard` or a simple mutex) around the `_update` function, or specifically around the external call to `IRelicsNFT(nft).syncBalances`. This would prevent re-entrant calls from external contracts during any token transfer operation.


### `M-01` — Low Fixed Supply and Potential for Price Volatility  *(Severity: Medium · Status: Unresolved)*

The `RelicsToken` has a `FIXED_SUPPLY` of 10,000 tokens (10,000 ether). This is a relatively small total supply for an ERC20 token. While not a direct code vulnerability, a low supply can contribute to higher price volatility and potentially make the token more susceptible to market manipulation, especially if liquidity is also low. The economic impact depends heavily on the token's intended utility and role within the broader Relics ecosystem (7.4 Economic).

**Recommendation:** While changing the fixed supply is not possible post-deployment, it is important to acknowledge and manage the implications of a low supply. Implement robust liquidity provisions and consider mechanisms to mitigate extreme price fluctuations if the token is intended for broad market use. Clearly communicate the economic model and potential volatility to users.


### `I-01` — Dependency on External `IRelicsNFT` Contract  *(Severity: Informational · Status: Unresolved)*

The `RelicsToken` contract has a significant dependency on the `IRelicsNFT` interface and its implementation. Functions like `_update` call `IRelicsNFT(nft).syncBalances(from, to)`, and `_requireHoldsNoRelics` calls `IRelicsNFT(nft).balanceOf(account)`. The security and correct functioning of `RelicsToken` are directly tied to the security, behavior, and availability of the `IRelicsNFT` contract. Any vulnerabilities, unexpected behavior, or upgrade issues in `IRelicsNFT` could directly impact `RelicsToken` (7.6 External).

**Recommendation:** Ensure that the `IRelicsNFT` contract is thoroughly audited, well-maintained, and deployed at a trusted address. Implement robust monitoring for the `IRelicsNFT` contract to detect any anomalies or compromises that could affect `RelicsToken`.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8f29...2da9`](https://etherscan.io/address/0x8f294a99a0609822c233b24867f331c292ce2da9) |
| **Network** | Ethereum |
| **Price** | $75.3000 |
| **24h Volume** | $165.9K |
| **Liquidity** | $226.8K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 7d |
| **Top-10 Holders** | 27.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 461 buys / 416 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x33d9b4089069272e5aeaeccf24bc710a7ee8cf65f4ecde682187a2fc355531ed)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/relics-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
