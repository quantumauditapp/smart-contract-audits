---
token: Milady Cult Coin
ticker: CULT
network: ethereum
risk_score: 55
status: medium
date: 2026-09-24
---

# Milady Cult Coin (CULT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 55/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/milady-cult-coin-eth)

---

## Audit Summary

The Cult contract implements an ERC20 token with a linear vesting mechanism. It leverages well-audited Solady libraries for core functionalities and includes a reentrancy guard. The contract is owned by a multisig, which manages vesting schedules and treasury operations. No critical or high-severity vulnerabilities were identified. Minor issues include unused variables and a potential typo in an import path.

> **Final Recommendation:** It is recommended to verify the exact source of the `ReentrancyGuard` import to ensure it refers to a trusted and audited library. The project should maintain robust security practices for the multisig owner, including secure key management and a clear process for transaction approvals, given its significant control over vesting and treasury funds. Regular review of owner actions and transparency regarding vesting schedules are also advised.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates strong technical security by utilizing battle-tested Solady libraries for ERC20, Ownable, FixedPointMathLib, and SafeTransferLib (7.2 Code Security). A ReentrancyGuard is… |
| **Governance / Economics** | 1/10 | High | The contract employs an `Ownable` access control pattern, with the owner being a multisig address (7.3 Access Control). This multisig has significant control, including the ability to set all vesting… |
| **Upgrades** | 6/10 | Medium | The Cult contract is not designed to be upgradeable. It is a standard, immutable contract deployed directly to the blockchain (7.7 Upgrades). This eliminates upgrade-related risks such as proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 98.8% |
| **Top-3 Unlocked** | ⚠️ 99.5% |

## Security Findings

_🟢 2 Low · ⚪ 2 Informational_

### `L-01` — Centralized Control over Vesting and Treasury  *(Severity: Low · Status: Unresolved)*

The `Ownable` pattern grants the contract owner (a multisig) exclusive control over critical functions. The owner can set all vesting schedules via `setVest` and manage contract funds (ETH and other ERC20 tokens) via `transferEther` and `transferToken`. This centralization means the security of the protocol heavily relies on the integrity and operational security of the multisig owner. While a multisig mitigates single points of failure, it still represents a single administrative entity.

**Recommendation:** Ensure the multisig owner's keys are managed with the highest security standards. Implement robust internal processes for transaction approval and consider transparent communication regarding owner actions, especially those affecting vesting schedules or treasury movements.


### `L-02` — Potential Typo in ReentrancyGuard Import Path  *(Severity: Low · Status: Unresolved)*

The import path for `ReentrancyGuard` is specified as `soledge/utils/ReentrancyGuard.sol`. Given that all other utility imports are from `solady/utils/`, this might be a typographical error and intended to be `solady/utils/ReentrancyGuard.sol`. If `soledge` refers to a different, potentially less-audited or custom library, it could introduce an unknown dependency risk. If it is indeed a typo and resolves to Solady's library, the risk is minimal.

**Recommendation:** Verify the exact import path and ensure that `soledge/utils/ReentrancyGuard.sol` correctly points to the intended and audited `ReentrancyGuard` implementation, preferably Solady's. If it's a typo, correct the import statement to `solady/utils/ReentrancyGuard.sol` for clarity and consistency.


### `I-01` — Unused `MESSAGE` Constant  *(Severity: Informational · Status: Unresolved)*

The `MESSAGE` constant is declared at the contract level but is not referenced or used anywhere within the contract's logic. Unused variables can increase bytecode size slightly and may indicate leftover code from previous development iterations.

**Recommendation:** Remove the `MESSAGE` constant if it serves no current or planned purpose to optimize bytecode size and improve code clarity.


### `I-02` — Unused `lastClaimTime` in Vesting Calculation  *(Severity: Informational · Status: Unresolved)*

The `lastClaimTime` field within the `Vest` struct is updated in the `pushVest` function to `block.timestamp`. However, this field is not utilized in the `FixedPointMathLib.lerp` calculation, which directly uses `block.timestamp` for determining the currently vested amount. This means `lastClaimTime` is purely informational in the current implementation and does not affect the vesting schedule or claimable amount.

**Recommendation:** Clarify the intended purpose of `lastClaimTime`. If it's not meant to influence the vesting calculation, consider if it's truly necessary or if its name implies a function it doesn't perform. If it's for future functionality, document its purpose.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0000...eca4`](https://etherscan.io/address/0x0000000000c5dc95539589fbd24be07c6c14eca4) |
| **Network** | Ethereum |
| **Price** | $0.0001407 |
| **24h Volume** | $102.5K |
| **Liquidity** | $4.16M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 1y |
| **Top-10 Holders** | 73.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 264 buys / 238 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xc4ce8e63921b8b6cbdb8fcb6bd64cc701fb926f2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/milady-cult-coin-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-24*
