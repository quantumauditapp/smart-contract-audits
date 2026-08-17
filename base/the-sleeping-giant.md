---
token: the sleeping giant
ticker: TSG
network: base
risk_score: 40
status: medium
date: 2026-08-17
---

# the sleeping giant (TSG) — Smart Contract Security Analysis | Base

> **Risk Score: 40/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/the-sleeping-giant-base)

---

## Audit Summary

The DERC20 token contract implements an ERC20 token with voting, permit, and ownership functionalities. It includes a vesting mechanism for initial token distribution and an inflation mechanism controlled by the owner. The contract leverages well-audited OpenZeppelin libraries, enhancing its foundational security. Key areas of concern include the significant centralized control retained by the owner over critical functions and a specific constraint in the constructor regarding vested token amounts.

> **Final Recommendation:** It is recommended to carefully manage the owner's multisig keys and ensure robust operational procedures for critical functions like `unlockPool()` and `updateMintRate()`. Consider reviewing the `MaxTotalVestedExceeded` constraint in the constructor to ensure it aligns with the project's long-term distribution strategy. While precision loss in integer arithmetic is common, ensure stakeholders are aware of its minor implications for vesting and inflation calculations. Thoroughly document all owner-controlled parameters and their intended use.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The DERC20 contract demonstrates good technical architecture, building upon battle-tested OpenZeppelin standards for ERC20, ERC20Votes, ERC20Permit, and Ownable. This significantly reduces the risk… |
| **Governance / Economics** | 4/10 | Medium | The contract's economic model includes an inflationary mechanism with a configurable yearly mint rate, capped at 2% of the total supply. The owner, a multisig address, holds significant control over… |
| **Upgrades** | 7/10 | Low | The DERC20 contract is not designed as an upgradeable proxy (7.7 Upgrades). Its logic is immutable once deployed. However, certain parameters like the `yearlyMintRate`, `tokenURI`, and the `pool`… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 66.8% |
| **Top-3 Unlocked** | ⚠️ 94.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 3 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control by Owner  *(Severity: High · Status: Unresolved)*

The contract utilizes the Ownable pattern, granting the owner significant control over critical functions. The owner can `lockPool`/`unlockPool`, `burn` tokens, `updateMintRate` (within a cap), trigger `mintInflation` (minting to themselves), and `updateTokenURI`. While the owner is identified as an OZ_ProxyAdmin with a 3/6 multisig, the concentration of these powers still represents a high risk if the multisig itself is compromised or mismanaged. The ability to control inflation and freeze pool transfers are particularly sensitive.

**Recommendation:** Ensure the multisig controlling the owner address has robust security practices, including strong key management, regular audits, and clear operational procedures. Consider implementing time-locks or additional governance mechanisms for highly sensitive operations like `updateMintRate` or `unlockPool` to introduce a delay, allowing for community review or emergency intervention.


### `M-01` — Constructor Constraint on Vested Tokens  *(Severity: Medium · Status: Unresolved)*

The constructor includes a `require(vestedTokens < initialSupply, MaxTotalVestedExceeded(...));` statement. This condition prevents the total amount of pre-minted and vested tokens (`vestedTokens`) from being equal to the `initialSupply`. This implies that a portion of the `initialSupply` must always be minted directly to the `recipient` without vesting. This design choice might limit flexibility if the project intends to vest 100% of the initial supply or could lead to unexpected behavior if the `initialSupply` is small and `vestedTokens` approaches it.

**Recommendation:** Review this constraint to confirm it aligns with the intended token distribution strategy. If the intention is to allow for 100% of the initial supply to be vested, change the condition to `vestedTokens <= initialSupply`. If the current behavior is intentional, ensure it is clearly documented.


### `L-01` — Precision Loss in Vesting and Inflation Calculations  *(Severity: Low · Status: Unresolved)*

The `computeAvailableVestedAmount` and `mintInflation` functions perform calculations involving multiplication followed by integer division. For example, `totalAmount * (block.timestamp - vestingStart) / vestingDuration` and `(supply * yearlyMintRate_ * timeLeftInCurrentYear) / (1 ether * 365 days)`. Integer division truncates any fractional part, effectively rounding down. This can lead to minor precision loss, resulting in slightly less than perfectly proportional amounts being released for vesting or minted for inflation over time.

**Recommendation:** While this is a common characteristic of integer arithmetic in Solidity and often acceptable for minor discrepancies, it's important to be aware of its implications. For higher precision, consider using fixed-point arithmetic libraries (e.g., ABDKMathQuad) if the minor precision loss is deemed unacceptable. Otherwise, ensure this behavior is understood and communicated to users.


### `L-02` — External Dependency on Permit2 Contract  *(Severity: Low · Status: Unresolved)*

The `allowance` function grants `type(uint256).max` allowance to a specific `PERMIT_2` address (`0x000000000022D473030F116dDEE9F6B43aC78BA3`). This is a common integration with the Permit2 contract, enabling gas-efficient approvals. However, it introduces an external dependency. Any vulnerability or compromise within the Permit2 contract itself could indirectly affect the security of funds approved to this DERC20 token via Permit2.

**Recommendation:** Acknowledge the inherent risk associated with integrating external protocols. While Permit2 is widely used and audited, it's crucial to monitor its security status. No direct action is required on this contract, but awareness of the dependency is important for overall risk assessment.


### `L-03` — Operational Dependency for Inflation Mechanism Start  *(Severity: Low · Status: Unresolved)*

The `currentYearStart` and `lastMintTimestamp` variables, which are essential for the `mintInflation()` function to operate, are only initialized when the `unlockPool()` function is called by the owner. If `unlockPool()` is never invoked, `mintInflation()` will consistently revert with `MintingNotStartedYet()`, preventing any token inflation from occurring. This creates an operational dependency where the owner must perform an explicit action to enable the core inflation mechanism.

**Recommendation:** Ensure that the operational team is aware of this dependency and has a clear procedure for calling `unlockPool()` at the appropriate time to initiate the inflation schedule. Document the intended timing and conditions for this action.


### `I-01` — Ambiguity in `initialSupply` Interpretation  *(Severity: Informational · Status: Unresolved)*

The constructor uses `initialSupply` as a base for calculating `maxPreMintPerAddress` and `maxTotalPreMint` (e.g., `initialSupply * MAX_PRE_MINT_PER_ADDRESS_WAD / 1 ether`). The term `initialSupply` could be interpreted in multiple ways: as the total supply minted at deployment, or as a base amount from which other distributions are derived. The `vestedTokens < initialSupply` check further implies `initialSupply` acts as a hard cap for total initial distribution. Clarity on this interpretation is important for understanding the token's economic model.

**Recommendation:** Add explicit NatSpec documentation to the `initialSupply` parameter in the constructor, clearly defining its role and how it relates to `vestedTokens` and the `recipient`'s initial balance. This will prevent potential misinterpretations by future auditors or developers.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4c43...eba3`](https://basescan.org/address/0x4c433f4ef87fe506a7eed2fd1d822cbed411eba3) |
| **Network** | Base |
| **Price** | $0.00000142 |
| **24h Volume** | $126.8K |
| **Liquidity** | $166.6K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 3mo |
| **Top-10 Holders** | 53.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 427 buys / 709 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x5e4c78bf666d78fa1e751abc84cf9933d17b1736d4605f400173ac63ac52b1f8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/the-sleeping-giant-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-17*
