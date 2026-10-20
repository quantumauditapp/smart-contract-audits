---
token: CARV
ticker: CARV
network: base
risk_score: 58
status: medium
date: 2026-10-05
---

# CARV (CARV) — Smart Contract Security Analysis | Base

> **Risk Score: 58/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/carv-base)

---

## Audit Summary

The CarvToken is an ERC-20 compatible token with LayerZero OFT (Omnichain Fungible Token) capabilities, enabling cross-chain transfers. The contract is owned by a 3/5 multisig, which controls administrative functions. Key findings include a medium-severity issue where an external LayerZero endpoint can mint new tokens, potentially diluting existing holders, and a low-severity issue related to potential rounding loss in an internal function.

> **Final Recommendation:** It is crucial to ensure the security and integrity of the LayerZero endpoint that interacts with the CarvToken contract, as it possesses the capability to mint new tokens. Implement robust monitoring and access controls for this endpoint to prevent unauthorized token creation. Additionally, review the `_removeDust` function to mitigate potential rounding losses, ensuring precise token calculations.

Consider implementing a timelock for critical administrative actions controlled by the multisig owner to provide a delay for review and potential intervention, enhancing overall security and decentralization.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The CarvToken contract implements ERC-20 standards for fungible tokens and integrates LayerZero's OFT for cross-chain functionality. The architecture allows for token transfers and administrative… |
| **Governance / Economics** | 2/10 | High | The contract's ownership is retained by a 3/5 multisig, which has control over critical administrative functions such as `setMsgInspector`, `setEnforcedOptions`, `setPreCrime`, `setPeer`, and… |
| **Upgrades** | 4/10 | Medium | The CarvToken contract is not designed as an upgradeable proxy, meaning its logic cannot be modified post-deployment. This provides immutability and reduces the risk of future logic changes… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 48.6% |
| **Top-3 Unlocked** | ⚠️ 96.1% |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `CP-01` — External System Can Create New Tokens  *(Severity: Medium · Status: Unresolved)*

The CarvToken contract allows an external system, specifically the LayerZero endpoint, to create new tokens. This means that the `send`, `lzReceiveSimulate`, and `lzReceive` functions, when called by the endpoint, can increase the total supply of CarvTokens. If this endpoint is compromised or misused, it could lead to an uncontrolled increase in token supply, diluting the value of tokens held by existing holders.

**Recommendation:** Token holders should be aware that the total supply of CarvTokens can be increased by the LayerZero endpoint. It is critical for the project team to implement stringent security measures, monitoring, and access controls for the LayerZero endpoint to prevent unauthorized or malicious token minting.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 5 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 71% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CD-01` — Potential for Small Token Losses Due to Calculation Order  *(Severity: Low · Status: Unresolved)*

The `_removeDust` function in the contract performs a division operation before a multiplication. In Solidity, integer division truncates any decimal part, which can lead to a small loss of precision. While typically minor, this rounding loss could accumulate over many operations or affect very small token amounts, potentially leading to a slight discrepancy in calculations.

**Recommendation:** Token holders should understand that very small amounts of tokens might be lost due to rounding in specific internal calculations. The project team should review the `_removeDust` function to reorder operations (multiply before divide) or use a fixed-point math library to ensure maximum precision and prevent any potential rounding losses.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 87.3% of supply. What remains: 66.5% in wallets, 20.7% in other contracts. 242,063 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as CARV (CARV), market cap $34M, rank #656. 242,063 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $383K (DexScreener, all pools). 24h trading volume $24.0M (CoinGecko, all markets, daily snapshot). 24h trading volume $733K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $1.36 on 2024-11-02; the price is now 96.2358% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 3-of-5 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $383K of DEX liquidity across 9 pools. Launch: 725 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc08c...aa8c`](https://basescan.org/address/0xc08cd26474722ce93f4d0c34d16201461c10aa8c) |
| **Network** | Base |
| **Price** | $0.05418 |
| **24h Volume** | $253.7K |
| **Liquidity** | $271.4K |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 2y |
| **Top-10 Holders** | 87.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3390 buys / 3528 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xff862675c47b6a2c9072dcbe2f37a78a445c4f37)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/carv-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-05*
