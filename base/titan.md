---
token: Titan
ticker: TITN
network: base
risk_score: 59
status: medium
date: 2026-10-17
---

# Titan (TITN) — Smart Contract Security Analysis | Base

> **Risk Score: 59/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/titan-base)

---

## Audit Summary

The Titn contract is an ERC-20 token with Omnichain Fungible Token (OFT) capabilities, allowing cross-chain transfers via LayerZero. The contract is owned by a 2/3 multisig. Key findings include the ability for a privileged LayerZero endpoint to mint new tokens, potentially diluting existing holders, and the owner's control over a switch that can lock all token transfers.

> **Final Recommendation:** It is recommended to thoroughly review the security of the LayerZero endpoint responsible for minting tokens to prevent unauthorized supply inflation. Consider implementing a timelock or multi-signature approval process for critical owner-controlled functions, especially those affecting transferability or token supply, to enhance security and decentralization. Ensure clear documentation and communication regarding the implications of the `isBridgedTokensTransferLocked` switch and the `transferAllowedContract`.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The Titn contract implements the ERC-20 standard and integrates LayerZero's Omnichain Fungible Token (OFT) functionality, enabling cross-chain token transfers. The `_validateTransfer` function allows… |
| **Governance / Economics** | 2/10 | High | The contract's ownership is retained by a 2/3 multisig, which is a positive for decentralized control compared to a single EOA. The owner has significant administrative control over various… |
| **Upgrades** | 4/10 | Medium | The Titn contract is not deployed as a proxy, and no explicit upgrade mechanism is present within the provided code (7.7 Upgrades). This means the contract's logic is immutable once deployed… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 57.1% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 3 Medium · ⚪ 3 Informational_

### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 97.5% of supply. What remains: 9.7% in wallets, 87.7% in other contracts. The deployer/owner wallet itself holds 45.9%. A holder that also controls the contract can sell into its own liquidity. 3,740 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `CP-01` — A privileged address can mint new tokens  *(Severity: Medium · Status: Unresolved)*

A privileged function increases the total supply, diluting every holder. Functions: send(SendParam,MessagingFee,address), lzReceiveSimulate(Origin,bytes32,bytes,address,bytes), lzReceive(Origin,bytes32,bytes,address,bytes). Restricted to: endpoint.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `CP-05` — A privileged address controls a switch that decides whether transfers go through  *(Severity: Medium · Status: Unresolved)*

An on/off setting checked in the transfer path can be changed by a privileged function; depending on its value, transfers or sales are allowed or refused. Functions: setBridgedTokenTransferLocked. Restricted to: owner.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 3 address(es) other than the owner/deployer. One of them — a wallet, 0x73e5…91ad — holds 57.1% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 88% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as THORWallet (TITN), rank #3744. 3,740 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $337K (DexScreener, all pools). 24h trading volume $69K (CoinGecko, all markets, daily snapshot). 24h trading volume $78K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.351 on 2026-01-19; the price is now 96.8442% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 2-of-3 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $337K of DEX liquidity across 5 pools. Launch: 227 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe62b...5b06`](https://basescan.org/address/0xe62bfbe57763ec24c0f130426f34dbce11fc5b06) |
| **Network** | Base |
| **Price** | $0.009619 |
| **24h Volume** | $55.6K |
| **Liquidity** | $296.8K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 7mo |
| **Top-10 Holders** | 97.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 365 buys / 266 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x611865e603862a3d1cd29146458564a684e1cbbb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/titan-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-17*
