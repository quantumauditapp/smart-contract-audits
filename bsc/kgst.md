---
token: KGST
ticker: KGST
network: bsc
risk_score: 71
status: high
date: 2026-10-06
---

# KGST (KGST) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 71/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kgst-bsc)

---

## Audit Summary

This audit covers a Stablecoin contract deployed as an upgradeable proxy. The contract implements standard ERC-20 functionality with additional features like pausing transfers, freezing individual accounts, and minting new tokens. All these critical functions are restricted to a multisig owner, which enhances security. However, the existence of these powerful owner-controlled functions introduces centralized risks that token holders should be aware of.

> **Final Recommendation:** It is crucial for token holders to understand the extensive control the multisig owner retains over the Stablecoin contract, including the ability to mint new tokens, pause all transfers, and freeze individual accounts. While the use of a multisig wallet for ownership and upgrade administration significantly enhances security by requiring multiple approvals for critical actions, the inherent centralization of these powers means that the security of the protocol heavily relies on the integrity and operational security of the multisig signers. Regular communication and transparency from the multisig signers regarding their operational policies and any planned actions are recommended to maintain trust within the community.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The Stablecoin contract is built on established OpenZeppelin standards, inheriting `ERC20Upgradeable`, `PausableUpgradeable`, and `Ownable2StepUpgradeable`, ensuring a robust architectural foundation… |
| **Governance / Economics** | 1/10 | High | The economic stability of the token is directly influenced by the owner's ability to `mint` new tokens, which can dilute existing holders (7.4 Economic). Furthermore, the owner can `pause` all… |
| **Upgrades** | 1/10 | High | The contract is deployed as an EIP-1967 Transparent Proxy, managed by an OpenZeppelin `ProxyAdmin` contract (7.7 Upgrades). The `ProxyAdmin` itself is owned by a 2-of-5 multisig wallet, providing a… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 2-of-5 |
| **Implementation** | ✅ Verified source |

## Security Findings

_🟡 3 Medium · ⚪ 4 Informational_

### `CP-01` — The project's controller can create new tokens.  *(Severity: Medium · Status: Unresolved)*

The `mint` function allows the contract owner to create an unlimited number of new tokens at any time. This means the total supply of tokens can be increased, which could dilute the value of existing tokens held by you and other users.

**Recommendation:** Token holders should be aware that the project's controller, a multisig wallet, has the power to increase the token supply. This power should be exercised transparently and with clear communication to the community to avoid unexpected dilution.


### `CP-04` — The project's controller can stop all token transfers.  *(Severity: Medium · Status: Unresolved)*

The `pause` and `unpause` functions allow the contract owner to completely stop all token transfers on the network. If transfers are paused, you would be unable to move or sell your tokens until the owner decides to unpause them.

**Recommendation:** Token holders should understand that the project's controller, a multisig wallet, can temporarily halt all token activity. This feature is often used in emergencies but could also restrict your access to your funds.


### `CP-06` — The project's controller can block specific token holders.  *(Severity: Medium · Status: Unresolved)*

The `freeze` and `unfreeze` functions allow the contract owner to prevent specific addresses from transferring their tokens. If your address is frozen, you would be unable to move or sell your tokens, even if general transfers are not paused.

**Recommendation:** Token holders should be aware that the project's controller, a multisig wallet, has the ability to selectively block individual accounts from transacting. This power should be used with extreme caution and only for legitimate security or regulatory reasons.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 100.0% in wallets, 0.0% in other contracts. 1 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Kyrgyz Som Stablecoin (KGST), market cap $9M, rank #1391. 1 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $182K (DexScreener, all pools). 24h trading volume $1.6M (CoinGecko, all markets, daily snapshot). 24h trading volume $1.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Stablecoin — issuer-backed (fiat reserves)  *(Severity: Informational · Status: Acknowledged)*

A token designed to hold a fixed value (usually $1). Its safety rests on what backs it and on who can mint, freeze or pause it. Its identity is not independently verified, so it gets none of the allowances an established stablecoin gets: every power its owner holds over supply and transfers is scored in full, because a peg is only as good as whoever can mint. Basis: CoinGecko category: Fiat-backed Stablecoin. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 2-of-5 multisig. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $182K of DEX liquidity across 30 pools. Launch: 284 days of market history.

**Recommendation:** Check what backs the peg and who controls supply: reserve attestations for an issuer-backed coin, collateral and governance for a protocol coin.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x94be...f828`](https://bscscan.com/address/0x94be0bba8e1e303fe998c9360b57b826f1a4f828) |
| **Network** | BNB Chain |
| **Price** | $0.01145 |
| **24h Volume** | $1.17M |
| **Liquidity** | $170.1K |
| **Volume / Liquidity** | 6.9× |
| **Token Age** | 9mo |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6769 buys / 6974 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x9d7dae710545ccbe39cf7b5c4ebc55d116f05f44)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kgst-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-06*
