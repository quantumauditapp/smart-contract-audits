---
token: Flying Tulip
ticker: FT
network: ethereum
risk_score: 57
status: medium
date: 2026-10-04
---

# Flying Tulip (FT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/flying-tulip-eth)

---

## Audit Summary

The FT contract is an ERC-20 token with LayerZero OFT capabilities, inheriting from multiple base contracts including Ownable and Pausable. The contract exhibits a robust set of standard token functionalities. However, the audit identified a high-severity issue related to state variable shadowing and a medium-severity issue concerning privileged token minting, which could lead to token dilution if not properly managed. The contract is not upgradeable, which simplifies its lifecycle but means any discovered vulnerabilities would require a new deployment.

> **Final Recommendation:** It is crucial to address the identified shadowing state variable to prevent unexpected behavior and ensure the contract operates as intended. Furthermore, the access control for the token minting functions (`send`, `lzReceiveSimulate`, `lzReceive`) should be rigorously reviewed. Consider implementing additional governance oversight or stricter controls over the 'endpoint' address to mitigate the risk of unauthorized token dilution. Ensure that the multisig owner has a clear and secure process for managing all privileged roles.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The FT contract implements ERC-20 token standards and integrates LayerZero OFT functionalities, demonstrating a complex architecture (7.1 Architecture). The contract includes owner-restricted… |
| **Governance / Economics** | 2/10 | High | The contract employs an `Ownable` pattern, where a multisig wallet with a 3-of-5 threshold controls critical administrative functions, enhancing security against single points of failure (7.5… |
| **Upgrades** | 4/10 | Medium | The FT contract is not designed as an upgradeable proxy, meaning its logic cannot be modified after deployment (7.7 Upgrades). This eliminates upgrade-related risks such as proxy misconfigurations or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 31.3% |
| **Top-3 Unlocked** | ⚠️ 87.6% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 4 Informational_

### `CD-01` — Shadowing State Variable Detected  *(Severity: High · Status: Unresolved)*

The contract contains a state variable that is 'shadowing' another variable, likely from an inherited contract. This means two variables with the same name exist in different scopes, which can lead to confusion, unexpected behavior, or logical errors if the wrong variable is accessed or modified in certain contexts. This could impact how the contract stores and retrieves critical data.

**Recommendation:** Token holders should be aware that a technical issue with state variable management exists. It is strongly recommended to identify and rename the shadowed state variable to ensure unique identification and prevent potential bugs. This will improve the contract's reliability and predictability, ensuring that all operations, including transfers and balances, function correctly.


### `CP-01` — Privileged Address Can Mint New Tokens  *(Severity: Medium · Status: Unresolved)*

The 'endpoint' address has the ability to create new tokens by calling functions such as `send(SendParam,MessagingFee,address)`, `lzReceiveSimulate(Origin,bytes32,bytes,address,bytes)`, and `lzReceive(Origin,bytes32,bytes,address,bytes)`. This means that the total supply of tokens can be increased without explicit governance approval, which could dilute the value for existing token holders.

**Recommendation:** Token holders should be aware that the 'endpoint' address can mint new tokens. It is recommended to ensure that the 'endpoint' address is controlled by a secure, multi-signature wallet or a robust governance mechanism. Consider implementing additional checks or a time-lock for minting operations to provide transparency and allow token holders to react.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 7 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 40% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 98.8% of supply. What remains: 0.0% in wallets, 98.8% in other contracts. 936 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Flying Tulip (FT), market cap $72M, rank #376. 936 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.0M (DexScreener, all pools). 24h trading volume $234K (CoinGecko, all markets, daily snapshot). 24h trading volume $182K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 3-of-5 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.0M of DEX liquidity across 10 pools. Launch: 223 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5dd1...082c`](https://etherscan.io/address/0x5dd1a7a369e8273371d2dbf9d83356057088082c) |
| **Network** | Ethereum |
| **Price** | $0.15 |
| **24h Volume** | $150.9K |
| **Liquidity** | $402.2K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 7mo |
| **Top-10 Holders** | 98.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 79 buys / 61 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x68102ff5406475881462880a8da3c9bc9181ad6c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/flying-tulip-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-04*
