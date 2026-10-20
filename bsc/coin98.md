---
token: Coin98
ticker: C98
network: bsc
risk_score: 45
status: medium
date: 2026-10-10
---

# Coin98 (C98) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 45/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/coin98-bsc)

---

## Audit Summary

The Coin98 token contract is an ERC-20 standard token with additional owner-controlled functionalities for minting new tokens and pausing all transfers. While ownership is managed by a 3/5 multisig, these centralized controls introduce potential economic and operational risks, as highlighted by the medium-severity findings related to token supply and transferability.

> **Final Recommendation:** It is recommended that the project team carefully consider the long-term implications of the centralized control over token supply and transferability. If the intention is for the token to be fully decentralized, a roadmap for renouncing minting and pausing capabilities should be established. For critical operations, ensure the multisig threshold and signers are robust and well-protected.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The Coin98 contract implements standard ERC-20 functionality and utilizes `Ownable` and `Pausable` patterns for administrative control. The internal `_transfer` function is consistently used for both… |
| **Governance / Economics** | 1/10 | High | The contract's ownership is managed by a 3/5 multisig, which enhances security by requiring multiple approvals for critical operations (7.5 Governance). Despite this, the owner retains significant… |
| **Upgrades** | 4/10 | Medium | The Coin98 contract is not designed as an upgradeable proxy, which eliminates the complexities and potential risks associated with upgrade mechanisms (7.7 Upgrades). As a non-upgradeable contract… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 92.4% |
| **Top-3 Unlocked** | ⚠️ 96.7% |

## Security Findings

_🟡 4 Medium · ⚪ 3 Informational_

### `CP-01` — Owner Can Mint New Tokens  *(Severity: Medium · Status: Unresolved)*

The owner of the Coin98 token contract has the ability to create an unlimited number of new tokens using the `mint(address,uint256)` function. This means that the total supply of Coin98 tokens can be increased at any time, potentially diluting the value of existing tokens held by users.

**Recommendation:** Token holders should be aware that the project's owner can increase the token supply. If this control is not intended to be permanent, the project team should consider implementing a mechanism to renounce or remove the minting capability, or transfer it to a more decentralized governance model.


### `CP-04` — Owner Can Pause All Token Transfers  *(Severity: Medium · Status: Unresolved)*

The owner of the Coin98 token contract can stop all token transfers by calling the `freeze()` function. Conversely, they can re-enable transfers using the `unfreeze()` function. This centralized control allows the owner to halt all trading and movement of Coin98 tokens, which could severely impact liquidity and user access to their funds.

**Recommendation:** Token holders should understand that the project's owner has the power to temporarily stop all token transactions. If this control is not intended for emergency use only, the project team should consider removing or decentralizing this pausing mechanism to ensure continuous token transferability.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 99.2% is held, unlocked, by 8 address(es) other than the owner/deployer. One of them — a wallet, 0xc5bc…fc47 — holds 92.4% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $340K (DexScreener, all pools). 24h trading volume $18.2M (CoinGecko, all markets, daily snapshot). 24h trading volume $228K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $6.42 on 2021-08-25; the price is now 99.7105% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 65.1% of supply. Of that, 2.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 62.8% in wallets, 0.0% in other contracts. 80,785 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Coin98 (C98), market cap $19M, rank #911. Traded on Binance. 80,785 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 3-of-5 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $340K of DEX liquidity across 24 pools. Launch: 1906 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xaec9...c3a6`](https://bscscan.com/address/0xaec945e04baf28b135fa7c640f624f8d90f1c3a6) |
| **Network** | BNB Chain |
| **Price** | $0.01857 |
| **24h Volume** | $225.7K |
| **Liquidity** | $329.0K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 5y |
| **Top-10 Holders** | 65.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1500 buys / 1496 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x92247860a03f48d5c6425c7ca35cdcfcb1013aa1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/coin98-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-10*
