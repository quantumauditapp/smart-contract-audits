---
token: NIGHT
ticker: NIGHT
network: bsc
risk_score: 72
status: high
date: 2026-10-03
---

# NIGHT (NIGHT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 72/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/night-bsc)

---

## Audit Summary

The WrappedToken contract is an ERC-20 token with standard functionalities and additional minting capabilities. Ownership is retained by an OZ_ProxyAdmin address, allowing centralized control over key administrative functions. The audit identified a high-severity issue related to shadowing state and a medium-severity issue concerning the owner's ability to mint new tokens, which could lead to token dilution.

> **Final Recommendation:** It is recommended to carefully review the implications of the owner's ability to mint new tokens and consider implementing a multi-signature wallet or a time-locked mechanism for such critical functions to enhance security and decentralization. Address the identified shadowing state issue to prevent potential unexpected behavior or vulnerabilities. Ensure that the owner address is secured with robust operational practices, as it holds significant control over the token's supply and administrative parameters.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract implements the ERC-20 standard, including `transfer` and `transferFrom` functions, which operate as expected (7.2 Code Security). Ownership is managed via Ownable, allowing the owner to… |
| **Governance / Economics** | 1/10 | High | The contract exhibits a centralized governance model, with an `OZ_ProxyAdmin` address retaining full ownership (7.5 Governance). This owner has the power to `mint` new tokens (CP-01), which directly… |
| **Upgrades** | 4/10 | Medium | The WrappedToken contract is not deployed as a proxy (7.1 Architecture) and therefore does not have an upgrade mechanism (7.7 Upgrades). This means the contract's logic is immutable once deployed… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 61.0% |
| **Top-3 Unlocked** | 73.8% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 4 Informational_

### `CD-01` — Potential for unexpected behavior due to shadowed state variables.  *(Severity: High · Status: Unresolved)*

The contract contains a 'shadowing state' issue. This means that a variable in the contract might have the same name as a variable in an inherited contract, potentially leading to confusion or unexpected behavior when the contract attempts to access or modify these variables. This could cause functions to operate differently than intended, impacting the reliability and security of the token.

**Recommendation:** Token holders should be aware that this technical issue could lead to unpredictable contract behavior. It is recommended that the contract developers resolve this by renaming the conflicting variables to ensure clarity and prevent any unintended interactions within the contract's logic.


### `CP-01` — Owner can create new tokens, diluting existing holders.  *(Severity: Medium · Status: Unresolved)*

The `mint` function allows the contract owner to create an unlimited number of new tokens and assign them to any address. This capability, restricted to the owner and `onlyMeaningfulValue`, means that the total supply of the token can be arbitrarily increased at any time. This action would dilute the value of all existing token holders without their consent.

**Recommendation:** Token holders should be aware that the contract owner has the power to increase the token supply. To mitigate this risk, consider advocating for the owner to renounce the minting capability if it's not essential for the token's long-term utility, or to implement a community-governed mechanism for minting decisions.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 88.6% is held, unlocked, by 10 address(es) other than the owner/deployer. One of them — a wallet, 0xf949…0298 — holds 61.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 61% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 90.3% of supply. What remains: 65.6% in wallets, 24.7% in other contracts. 15,416 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Midnight (NIGHT), market cap $831M, rank #86. 15,416 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $75K (DexScreener, all pools). 24h trading volume $116.7M (CoinGecko, all markets, daily snapshot). 24h trading volume $573K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $75K of DEX liquidity across 17 pools. Launch: 298 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfe93...224f`](https://bscscan.com/address/0xfe930c2d63aed9b82fc4dbc801920dd2c1a3224f) |
| **Network** | BNB Chain |
| **Price** | $0.05021 |
| **24h Volume** | $393.6K |
| **Liquidity** | $45.9K |
| **Volume / Liquidity** | 8.6× |
| **Token Age** | 9mo |
| **Top-10 Holders** | 90.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1076 buys / 1131 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x85533288f67ec74878444c273c00254eea74c2c3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/night-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-03*
