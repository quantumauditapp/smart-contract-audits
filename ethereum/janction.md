---
token: Janction
ticker: JCT
network: ethereum
risk_score: 62
status: medium
date: 2026-10-25
---

# Janction (JCT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 62/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/janction-eth)

---

## Audit Summary

The security audit evaluated the BurnMintERC20Upgrade system across key dimensions including 7.1 Architecture, 7.2 Code Security, 7.3 Access Control, 7.4 Economic, 7.5 Governance, 7.6 External, 7.7 Upgrades, and 7.8 Operations. The protocol demonstrates robust foundation with a multi-sig owner, 2-step ownership transfers, and standard ERC-20 transfer logic with zero transfer taxes. However, technical analysis revealed state variable shadowing across inherited contracts and centralized token minting capabilities that could dilute token holders.

> **Final Recommendation:** Resolve the state variable shadowing issue immediately by inspecting all inherited contracts and renaming or removing overlapping variables to ensure storage layout consistency across proxy upgrades. Additionally, introduce transparent minting constraints, such as a timelock or rate-limited minting schedule, to protect token holders from unannounced supply inflation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | Under 7.1 Architecture and 7.2 Code Security, the contract demonstrates robust foundational structure using standard OpenZeppelin upgradeable building blocks and safe arithmetic. Standard transfer… |
| **Governance / Economics** | 1/10 | High | In 7.4 Economic and 7.5 Governance, ownership is properly controlled via a 5-of-7 multi-signature scheme and enforced through Ownable2StepUpgrade, mitigating unilateral key compromise. Operational… |
| **Upgrades** | 1/10 | High | Reviewing 7.7 Upgrades alongside 7.1 Architecture, the implementation leverages the established UUPS proxy standard (ERC-1967) to enable secure implementation updates. Access to upgradeTo and… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 69.5% |
| **Top-3 Unlocked** | ⚠️ 98.4% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 4 Informational_

### `CD-01` — State Variable Shadowing Across Inherited Base Contracts  *(Severity: High · Status: Unresolved)*

The contract defines state variables that duplicate names already declared in its parent or base contracts. This causes compiler-level shadowing where internal logic and proxy storage slots can diverge or overwrite each other, potentially leading to unintended state corruption during contract execution or future upgrades.

**Recommendation:** Review all variable declarations across inherited contracts, eliminate duplicate variable names, and verify storage layout continuity across the implementation hierarchy.


### `CP-01` — Privileged Token Minting Enabling Supply Dilution  *(Severity: Medium · Status: Unresolved)*

Addresses assigned the minter role through grantMintRole or grantMintAndBurnRoles can call mint(address,uint256) to issue new tokens directly to any address up to i_maxSupply. This administrative capability can dilute the value and voting power of existing token holders without requiring community consensus or timelock delays.

**Recommendation:** Bind the mint function to a verifiable timelock contract or enforce an on-chain programmatic rate limit on minting volume to give holders advance notice of supply increases.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 4 address(es) other than the owner/deployer. One of them — a contract, 0xb0f3…6e73 — holds 69.5% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 52% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 0.0% in wallets, 100.0% in other contracts. 735 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Janction (JCT), market cap $73M, rank #341. 735 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $30K (DexScreener, all pools). 24h trading volume $85.0M (CoinGecko, all markets, daily snapshot). 24h trading volume $127K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable, capped at 26.0% of supply per year. Control: a 5-of-7 multisig. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $30K of DEX liquidity across 14 pools. Launch: 348 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc477...7549`](https://etherscan.io/address/0xc477b6dfd26ec2460b3b92de18837fd476ea7549) |
| **Network** | Ethereum |
| **Price** | $0.006449 |
| **24h Volume** | $115.8K |
| **Liquidity** | $15.7K |
| **Volume / Liquidity** | 7.4× |
| **Token Age** | 11mo |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 321 buys / 247 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xe6a44fb93ada9ac57d1e735dc507011b95e48332412206f5cd405e1a6fff88d2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/janction-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
