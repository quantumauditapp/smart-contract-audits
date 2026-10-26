---
token: Wrapped Frax
ticker: WFRAX
network: ethereum
risk_score: 11
status: low
date: 2026-10-11
---

# Wrapped Frax (WFRAX) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 11/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wrapped-frax-eth)

---

## Audit Summary

The WFRAXTokenOFTUpgradeable contract functions as a cross-chain ERC-20 token, leveraging the LayerZero OFT standard. The audit identified a medium-severity issue where an external 'endpoint' address possesses the capability to mint new tokens, potentially leading to token dilution. The contract is upgradeable via a TransparentUpgradeableProxy, with administrative control managed by a Timelock and the implementation owner by a multisig.

> **Final Recommendation:** It is recommended to carefully review the control mechanisms and security posture of the 'endpoint' address responsible for token minting. Implement robust monitoring and access controls for this address to mitigate the risk of unauthorized token supply increases. Additionally, consider implementing a timelock or multi-signature control for the 'endpoint' address itself, if feasible, to add an extra layer of security against potential compromises.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The WFRAXTokenOFTUpgradeable contract implements the ERC-20 standard and LayerZero's OFT functionality, enabling cross-chain transfers (7.1 Architecture). The code leverages established upgradeable… |
| **Governance / Economics** | 9/10 | Low | The contract's economic model (7.4 Economic) is directly impacted by the minting capability. While the primary owner (a 3/5 multisig) controls administrative settings, the ability to mint tokens… |
| **Upgrades** | 6/10 | Medium | The contract is deployed behind a TransparentUpgradeableProxy (7.7 Upgrades), allowing for future logic upgrades. The proxy's admin is controlled by a Timelock… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Timelock |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_⚪ 5 Informational_

### `CP-01` — External Endpoint Can Mint New Tokens  *(Severity: Informational · Status: Unresolved)*

The WFRAXTokenOFTUpgradeable contract allows an external address, referred to as the 'endpoint', to create new tokens. Specifically, the `send`, `lzReceiveSimulate`, and `lzReceive` functions, which are restricted to this 'endpoint', can increase the total supply of WFRAX tokens. This means that if the 'endpoint' address is compromised or misused, new tokens could be minted, diluting the value for all existing token holders.

**Recommendation:** Token holders should be aware that the 'endpoint' address has the power to mint new WFRAX tokens. It is crucial for the project team to ensure the security of this 'endpoint' address through strong operational security practices, such as multi-signature control or a timelock, to prevent unauthorized minting and protect the token's value.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 95.7% of supply. What remains: 27.3% in wallets, 68.4% in other contracts. 942 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Wrapped FRAX (WFRAX), market cap $14M. Its owner (0xb174…3f27) controls 2 issuer-backed coins CoinGecko lists on ethereum, $232M together, among them Legacy Frax Dollar: one issuer's programme, read on-chain. 942 holders. Verified by: issuer programme.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $2.6M (DexScreener, all pools). 24h trading volume $1.3M (CoinGecko, all markets, daily snapshot). 24h trading volume $404K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $4.40 on 2025-05-19; the price is now 92.5186% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Wrapped-Tokens. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 3-of-5 multisig. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $2.6M of DEX liquidity across 3 pools. Launch: 495 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x04ac...977f`](https://etherscan.io/address/0x04acaf8d2865c0714f79da09645c13fd2888977f) |
| **Network** | Ethereum |
| **Price** | $0.3304 |
| **24h Volume** | $336.0K |
| **Liquidity** | $2.10M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 95.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 272 buys / 226 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x0fe046a9027d8ce9a909f0c93ea2ddcfd8090f87)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wrapped-frax-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-11*
