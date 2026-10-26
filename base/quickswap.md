---
token: QuickSwap
ticker: QUICK
network: base
risk_score: 64
status: medium
date: 2026-10-26
---

# QuickSwap (QUICK) — Smart Contract Security Analysis | Base

> **Risk Score: 64/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/quickswap-base)

---

## Audit Summary

The OptimismMintableERC20 contract is a standard ERC-20 token implementation designed for cross-chain bridging on the Base network. The architecture relies on a bridge-controlled minting mechanism, which is standard for L2 canonical tokens. The code is clean and follows established OpenZeppelin patterns, though the centralization of minting power remains a structural risk.

> **Final Recommendation:** The contract is well-implemented and follows standard practices for L2 token bridging. No immediate code changes are required as the minting functionality is a core requirement for its intended purpose.

Users and stakeholders should monitor the security of the bridge contract, as it is the single point of failure for token supply integrity. Ensure that the bridge contract's governance and access control mechanisms are audited and maintained to the highest standards.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes robust, battle-tested OpenZeppelin libraries for ERC-20 functionality. 7.1 Architecture is modular, separating token logic from bridge-specific minting requirements. 7.2 Code… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic risk is primarily driven by the minting capability of the bridge. While necessary for cross-chain functionality, it introduces potential supply inflation if the bridge contract is… |
| **Upgrades** | 3/10 | High | 7.7 Upgrades are not natively supported by this contract instance as it is not a proxy. 7.8 Operations are straightforward, relying on the standard bridge interaction flow. The lack of upgradeability… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 81.2% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The mint(address,uint256) function allows a privileged bridge address to create new tokens at will. This increases the total supply and dilutes the value of existing holdings.

**Recommendation:** Ensure the bridge contract is secured by a multi-signature wallet or a decentralized governance process to prevent unauthorized minting.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0xeddf…07bd — holds 81.2% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 72% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 92.7% of supply. What remains: 5.0% in wallets, 87.7% in other contracts. 1,609 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Quickswap (QUICK), market cap $3M, rank #1955. 1,609 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $126K (DexScreener, all pools). 24h trading volume $1.8M (CoinGecko, all markets, daily snapshot). 24h trading volume $57K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.23 on 2022-05-05; the price is now 97.908% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $126K of DEX liquidity across 10 pools. Launch: 447 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7094...b305`](https://basescan.org/address/0x7094c27f342dbadfbbed005b219431595e33b305) |
| **Network** | Base |
| **Price** | $0.003122 |
| **24h Volume** | $42.3K |
| **Liquidity** | $91.5K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 1y |
| **Top-10 Holders** | 92.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 313 buys / 510 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xbe50cc9cf0905cac4f8f8453bb6c9798898658bd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/quickswap-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
