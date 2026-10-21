---
token: FTT
ticker: FTX TOKEN
network: ethereum
risk_score: 53
status: medium
date: 2026-09-21
---

# FTT (FTX TOKEN) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 53/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ftt-eth)

---

## Audit Summary

The FTT token contract implements a standard ERC20 token with burnable functionality, utilizing SafeMath for arithmetic operations. The contract is straightforward, lacking complex external interactions or advanced DeFi mechanisms. Key strengths include the use of SafeMath to prevent integer overflows/underflows and adherence to the ERC20 standard. Identified issues primarily relate to the initial centralized token distribution and the inherent ERC20 approve race condition, which are common considerations for such token designs.

> **Final Recommendation:** It is recommended to carefully manage the initial token distribution, ensuring transparency and clear communication regarding the deployer's holdings and intended use. For users interacting with the token, it is advisable to prioritize the use of `increaseAllowance` and `decreaseAllowance` functions over the direct `approve` function to mitigate potential front-running risks associated with allowance changes. Consider migrating to a more recent Solidity compiler version in future deployments to leverage newer language features and security improvements.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical implementation of the FTT token is robust for its intended purpose (7.2 Code Security). It correctly implements the ERC20 standard and incorporates SafeMath for all arithmetic… |
| **Governance / Economics** | 1/10 | High | The economic model involves an initial mint of 350 million FTT tokens directly to the contract deployer (7.4 Economic). This centralized initial distribution grants significant control over the token… |
| **Upgrades** | 7/10 | Low | The FTT token contract is not designed to be upgradeable (7.7 Upgrades). It does not implement any proxy patterns (e.g., UUPS, Transparent, Beacon). This eliminates upgrade-related risks such as… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.3% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Centralized Initial Token Supply  *(Severity: Medium · Status: Unresolved)*

The `FTT` contract's constructor mints the entire initial supply of 350,000,000 FTT tokens to `msg.sender` (the contract deployer). This design choice centralizes the initial token distribution, giving the deployer significant control over the token's supply and potential market influence. While there are no further minting capabilities, the initial concentration of tokens represents a single point of control.

**Recommendation:** Ensure that the initial distribution strategy is clearly communicated to the community. If decentralization is a long-term goal, consider implementing a phased distribution or vesting schedule for the initial supply to reduce immediate centralization risks. Implement robust operational security for the address holding the initial supply.


### `L-01` — ERC20 `approve` Race Condition  *(Severity: Low · Status: Unresolved)*

The standard ERC20 `approve` function is susceptible to a known race condition. If a user calls `approve(spender, newAmount)` while a `spender` is concurrently trying to spend the `oldAmount`, the `spender` might be able to spend both `oldAmount` and `newAmount` if the `newAmount` is greater than `oldAmount`. While `increaseAllowance` and `decreaseAllowance` functions are provided, the direct `approve` function remains available.

**Recommendation:** Educate users to always set the allowance to zero (`approve(spender, 0)`) before setting a new non-zero allowance, or preferably, to use `increaseAllowance` and `decreaseAllowance` functions which are designed to prevent this specific race condition. No code change is strictly required for this standard ERC20 behavior, but user education is key.


### `I-01` — Older Solidity Compiler Version  *(Severity: Informational · Status: Unresolved)*

The contract is compiled using Solidity version `^0.5.2`. While this version is functional, it is an older release. Newer Solidity versions (e.g., 0.8.x) include various language improvements, optimizer enhancements, and additional security checks (like default checked arithmetic, which SafeMath already addresses here).

**Recommendation:** For future contract deployments or significant updates, consider migrating to a more recent and actively maintained Solidity compiler version (e.g., 0.8.x). This allows leveraging the latest language features, security improvements, and compiler optimizations.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x50d1...a4c9`](https://etherscan.io/address/0x50d1c9771902476076ecfc8b2a83ad6b9355a4c9) |
| **Network** | Ethereum |
| **Price** | $0.2836 |
| **24h Volume** | $1.01M |
| **Liquidity** | $132.2K |
| **Volume / Liquidity** | 7.6× |
| **Token Age** | 5y |
| **Top-10 Holders** | 93.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1884 buys / 1824 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x7825de5586e4d2fd04459091bbe783fa243e1bf3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ftt-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-21*
