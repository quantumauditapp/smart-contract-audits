---
token: Reservoir
ticker: DAM
network: bsc
risk_score: 68
status: high
date: 2026-10-12
---

# Reservoir (DAM) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 68/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/reservoir-bsc)

---

## Audit Summary

The DamOft contract is an Omnichain Fungible Token (OFT) that extends ERC-20 functionality, enabling cross-chain transfers. A key finding indicates that a privileged external address (the LayerZero endpoint) can mint new tokens, which could lead to token dilution for existing holders.

> **Final Recommendation:** It is crucial to carefully manage the LayerZero endpoint's permissions and ensure its security, as it holds the power to mint new tokens. Consider implementing additional safeguards or monitoring mechanisms around the `send`, `lzReceiveSimulate`, and `lzReceive` functions to prevent unauthorized or unintended token minting. Review the overall access control strategy to ensure that all privileged functions are necessary and appropriately restricted.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The DamOft contract implements the Omnichain Fungible Token (OFT) standard, inheriting from ERC-20 and LayerZero components. This architecture (7.1 Architecture) facilitates cross-chain token… |
| **Governance / Economics** | 1/10 | High | The contract retains ownership, with an EOA (`0xb7570e32ded63b25163369d5eb4d8e89e70e5602`) acting as the owner. This owner has control over various administrative functions, including… |
| **Upgrades** | 3/10 | High | The DamOft contract is not deployed as a proxy (7.7 Upgrades), meaning its logic cannot be directly upgraded or modified after deployment. This eliminates upgrade-related risks such as proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 51.3% |
| **Top-3 Unlocked** | ⚠️ 98.0% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `CP-01` — A privileged address can mint new tokens  *(Severity: Medium · Status: Unresolved)*

A privileged function increases the total supply, diluting every holder. Functions: send(SendParam,MessagingFee,address), lzReceiveSimulate(Origin,bytes32,bytes,address,bytes), lzReceive(Origin,bytes32,bytes,address,bytes). Restricted to: endpoint.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 5 address(es) other than the owner/deployer. One of them — a wallet, 0x3b0c…3fcd — holds 51.3% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 90.0% of supply. Of that, 12.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 66.8% in wallets, 10.5% in other contracts. 2,140 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Reservoir (DAM), market cap $1M, rank #2745. 2,140 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $139K (DexScreener, all pools). 24h trading volume $575K (CoinGecko, all markets, daily snapshot). 24h trading volume $630K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.149 on 2025-09-18; the price is now 95.6757% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. The class itself adds no points; the contract and market facts decide the score. Basis: a copy of the coin from its home chain (ethereum), minted here by LayerZero (lzReceive). Tokenomics — Supply: mintable with no on-chain cap found. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $139K of DEX liquidity across 4 pools. Launch: 419 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf9ca...abf8`](https://bscscan.com/address/0xf9ca3fe094212ffa705742d3626a8ab96aababf8) |
| **Network** | BNB Chain |
| **Price** | $0.006383 |
| **24h Volume** | $630.4K |
| **Liquidity** | $138.8K |
| **Volume / Liquidity** | 4.5× |
| **Token Age** | 1y |
| **Top-10 Holders** | 90.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3117 buys / 3078 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xc86071ddd1b9367462af9f22d827747e1bc6f7e0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/reservoir-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-12*
