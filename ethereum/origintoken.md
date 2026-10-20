---
token: OriginToken
ticker: OGN
network: ethereum
risk_score: 37
status: medium
date: 2026-10-09
---

# OriginToken (OGN) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 37/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/origintoken-eth)

---

## Audit Summary

The OriginToken contract is an ERC-20 compliant token with additional features like pausing transfers, whitelisting transactors, and minting new tokens. The contract is owned by a Timelock with a 48-hour delay, which provides a window for community review before critical operations are executed. Key functionalities such as minting new tokens, pausing all transfers, and adjusting whitelist expiration are controlled by this Timelock owner. The audit identified medium-level risks related to the owner's ability to dilute token supply through minting and to halt all token transfers, alongside a low-level risk concerning the owner's ability to modify whitelist expiration.

> **Final Recommendation:** Token holders should be aware of the significant centralized control retained by the contract owner, particularly the ability to mint new tokens and pause all transfers. While the owner is a Timelock with a 48-hour delay, providing a window for community review, the potential for supply dilution and operational halts remains. It is recommended that the project clearly communicates the scope and limitations of the owner's privileges to its community. For future iterations, consider implementing a multi-signature wallet for critical owner functions or exploring mechanisms to further decentralize control, if appropriate for the project's goals.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The OriginToken contract implements the ERC-20 standard, inheriting from several OpenZeppelin-like base contracts to provide standard token functionalities, pausing, and whitelisting. The `transfer`… |
| **Governance / Economics** | 1/10 | High | The contract's economic model allows the owner to `mint` new tokens, which directly increases the total supply and can dilute existing token holders (7.4 Economic). The owner also has the power to… |
| **Upgrades** | 4/10 | Medium | The OriginToken contract is not designed with an upgrade mechanism, such as a proxy pattern. This means the contract's logic is immutable once deployed, eliminating risks associated with… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `CP-01` — Owner Can Mint New Tokens  *(Severity: Medium · Status: Unresolved)*

The contract owner has the ability to call the `mint(address,uint256)` function. This function creates new tokens and adds them to the total supply, as well as to a specified address's balance. This means the owner can increase the total number of tokens in existence at any time, potentially diluting the value of existing tokens.

**Recommendation:** Token holders should understand that the value of their tokens could be diluted if the owner decides to mint a large number of new tokens. Projects should clearly communicate their minting policy and any plans for future token issuance to maintain transparency with the community.


### `CP-04` — Owner Can Pause All Token Transfers  *(Severity: Medium · Status: Unresolved)*

The contract owner can call the `pause()` function to stop all token transfers, and `unpause()` to resume them. This means the owner has the power to completely halt all movement of tokens, which could severely impact liquidity and usability for token holders.

**Recommendation:** Token holders should be aware that the owner can unilaterally stop all token transfers. Projects should provide clear reasons and policies for when and why transfers might be paused, ensuring transparency with the community.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x6e3f…d1dc — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-08` — Owner Can Change Whitelist Expiration  *(Severity: Low · Status: Unresolved)*

The contract owner can call the `setWhitelistExpiration(uint256)` function to modify the timestamp after which the whitelist for transfers is no longer active. This allows the owner to extend or set the duration of the whitelisting period, which directly affects who can transfer tokens.

**Recommendation:** Token holders should be aware that the owner can control the duration of the whitelisting period. Projects should clearly communicate any changes to the whitelist expiration and the rationale behind such adjustments to maintain trust and transparency.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 69.7% of supply. What remains: 25.9% in wallets, 43.8% in other contracts. 44,337 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Origin Token (OGN), market cap $32M, rank #652. Traded on Binance, Coinbase. 44,337 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.6M (DexScreener, all pools). 24h trading volume $266.0M (CoinGecko, all markets, daily snapshot). 24h trading volume $3.2M (DexScreener, all pools). CoinGecko's record for this coin: all-time high $3.35 on 2021-04-08; the price is now 98.7149% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a timelock with a 48h delay. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.6M of DEX liquidity across 8 pools. Launch: 2334 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8207...ae26`](https://etherscan.io/address/0x8207c1ffc5b6804f6024322ccf34f29c3541ae26) |
| **Network** | Ethereum |
| **Price** | $0.03874 |
| **24h Volume** | $3.04M |
| **Liquidity** | $1.54M |
| **Volume / Liquidity** | 2.0× |
| **Token Age** | 6y |
| **Top-10 Holders** | 69.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 718 buys / 557 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x56a344f1aa03943f536b94436de6a6e10116cf86)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/origintoken-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-09*
