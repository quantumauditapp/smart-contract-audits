---
token: LayerZero
ticker: ZRO
network: ethereum
risk_score: 30
status: low
date: 2026-10-03
---

# LayerZero (ZRO) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 30/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/layerzero-eth)

---

## Audit Summary

The LayerZero Token contract is an OFT (Omnichain Fungible Token) implementation, inheriting ERC-20 functionality and enabling cross-chain token transfers via LayerZero. A key finding is that a privileged `endpoint` address can mint new tokens, which could dilute existing token holders. The contract owner is a multisig, providing robust control over administrative functions.

> **Final Recommendation:** It is crucial to carefully manage the `endpoint` address, as it possesses the power to mint new tokens, which directly impacts the token's supply and value. Consider implementing additional safeguards or multi-signature controls for the `endpoint` address to mitigate the risk of unauthorized or malicious minting. Transparent communication regarding the minting policy and any future minting events is also recommended to maintain token holder trust.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The LayerZero Token contract implements the ERC-20 standard and extends it with OFT capabilities for cross-chain transfers (7.1 Architecture). The contract includes standard ERC-20 functions like… |
| **Governance / Economics** | 5/10 | Medium | The contract's economic model is based on an ERC-20 token with cross-chain functionality. The `owner` has control over various administrative settings, such as `setMsgInspector` and `setPeer` (7.5… |
| **Upgrades** | 4/10 | Medium | The contract is not deployed as a proxy (7.7 Upgrades) and therefore does not have direct upgradeability mechanisms built into its deployment. Any changes to the contract logic would require… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 53.7% |
| **Top-3 Unlocked** | ⚠️ 94.8% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `CP-01` — A privileged address can mint new tokens  *(Severity: Medium · Status: Unresolved)*

A privileged function increases the total supply, diluting every holder. Functions: send(SendParam,MessagingFee,address), lzReceiveSimulate(Origin,bytes32,bytes,address,bytes), lzReceive(Origin,bytes32,bytes,address,bytes). Restricted to: endpoint.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 99.9% is held, unlocked, by 7 address(es) other than the owner/deployer. One of them — a wallet, 0x933b…b069 — holds 53.7% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 95% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 37.2% of supply. What remains: 11.9% in wallets, 25.4% in other contracts. 24,892 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as LayerZero (ZRO), market cap $614M, rank #104. Traded on Binance, Coinbase. 24,892 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $71K (DexScreener, all pools). 24h trading volume $178.6M (CoinGecko, all markets, daily snapshot). 24h trading volume $131K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 3-of-5 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $71K of DEX liquidity across 7 pools. Launch: 835 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6985...71cd`](https://etherscan.io/address/0x6985884c4392d348587b19cb9eaaf157f13271cd) |
| **Network** | Ethereum |
| **Price** | $1.8800 |
| **24h Volume** | $129.9K |
| **Liquidity** | $67.0K |
| **Volume / Liquidity** | 1.9× |
| **Token Age** | 2y |
| **Top-10 Holders** | 37.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 282 buys / 323 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x360acf12e72044ba3eaaa654e51e4725c699dcb1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/layerzero-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-03*
