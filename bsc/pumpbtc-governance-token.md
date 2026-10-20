---
token: pumpBTC Governance token
ticker: PUMP
network: bsc
risk_score: 67
status: high
date: 2026-10-05
---

# pumpBTC Governance token (PUMP) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 67/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pumpbtc-governance-token-bsc)

---

## Audit Summary

The PUMP token contract is an ERC-20 standard token with an owner-controlled minting capability. The primary security concern identified is the ability of a designated minter to increase the total supply, which could dilute existing token holders. The contract implements standard ERC-20 functionality and secure ownership transfer mechanisms.

> **Final Recommendation:** Token holders should be aware that the contract owner has the ability to designate an address as a 'minter' using the `setMinter` function. This designated minter can then create new tokens via the `mint` function, increasing the total supply of PUMP tokens. This capability could potentially dilute the value of existing holdings. It is crucial for the project team to clearly communicate their minting policy and for token holders to understand the implications of this feature. The project team should ensure robust operational security for the owner and minter addresses to prevent unauthorized minting.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The PUMP contract implements standard ERC-20 functionality and inherits `Ownable2Step` for secure ownership transfer (7.2 Code Security). Access control (7.3 Access Control) is properly enforced for… |
| **Governance / Economics** | 1/10 | High | The economic model (7.4 Economic) of the PUMP token includes a minting mechanism, which allows for the creation of new tokens up to a `MAX_SUPPLY`. This capability, controlled by the contract owner… |
| **Upgrades** | 3/10 | High | The PUMP contract is not designed with an upgrade proxy pattern (7.7 Upgrades) and therefore cannot be upgraded. This eliminates upgrade-related risks such as proxy misconfigurations or logic errors… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 65.9% |
| **Top-3 Unlocked** | ⚠️ 92.0% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `CP-01` — Privileged Address Can Mint New Tokens  *(Severity: Medium · Status: Unresolved)*

The PUMP token contract allows a specially designated address, known as a 'minter,' to create new tokens. This is controlled by the contract owner, who can assign or revoke the minter role using the `setMinter(address,bool)` function. Once an address is a minter, it can call the `mint(address,uint256)` function to increase the total supply of PUMP tokens. This action can dilute the value of tokens held by existing holders.

**Recommendation:** Token holders should understand that the project team has the power to increase the token supply. It is important for the project to clearly communicate its minting policy and any plans for future token creation. For the project team, ensure that the address designated as the minter is highly secured, ideally a multi-signature wallet, and that minting operations are transparently communicated to the community.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 6 address(es) other than the owner/deployer. One of them — a contract, 0x5d23…5555 — holds 65.9% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 95.9% of supply. Of that, 1.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 66.1% in wallets, 28.3% in other contracts. 28,242 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as PumpBTC (PUMP), market cap $3M. 28,242 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $207K (DexScreener, all pools). 24h trading volume $14.0M (CoinGecko, all markets, daily snapshot). 24h trading volume $1.5M (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.577 on 2025-09-22; the price is now 98.3604% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 2-of-3 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $207K of DEX liquidity across 10 pools. Launch: 552 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb7c0...3f0c`](https://bscscan.com/address/0xb7c0007ab75350c582d5eab1862b872b5cf53f0c) |
| **Network** | BNB Chain |
| **Price** | $0.01313 |
| **24h Volume** | $1.32M |
| **Liquidity** | $200.2K |
| **Volume / Liquidity** | 6.6× |
| **Token Age** | 1y |
| **Top-10 Holders** | 95.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2783 buys / 2270 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x90345fbe6da637322015129de38d3166f98aac9c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pumpbtc-governance-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-05*
