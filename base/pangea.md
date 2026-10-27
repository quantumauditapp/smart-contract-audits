---
token: Pangea
ticker: PANGEA
network: base
risk_score: 65
status: high
date: 2026-10-21
---

# Pangea (PANGEA) — Smart Contract Security Analysis | Base

> **Risk Score: 65/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pangea-base)

---

## Audit Summary

The PangeaOFT contract implements an Omnichain Fungible Token (OFT) standard on the Base network. The architecture relies on LayerZero for cross-chain messaging and utilizes specific roles for metadata management and supply reporting. While the code follows standard library patterns, the presence of privileged minting capabilities requires careful monitoring of the designated roles.

> **Final Recommendation:** The protocol should ensure that the addresses assigned to the 'supplyReporter' and 'metadataAuthority' roles are secured via multi-signature wallets or timelock contracts. This mitigates the risk of unauthorized supply adjustments or metadata manipulation.

Regular monitoring of the 'reportedSupply' and 'metadataURI' changes is advised to ensure transparency for token holders. No further code changes are required as the current implementation adheres to the intended design patterns.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract leverages established LayerZero OFT standards for cross-chain interoperability. 7.1 Architecture is modular, utilizing OApp components for secure message handling. 7.2 Code Security is… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic and 7.5 Governance risks are centered on the supplyReporter role. This role has the authority to influence supply reporting, which impacts tokenomics. 7.6 External dependencies are… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not implemented via proxy patterns in this contract. 7.8 Operations are managed through owner-restricted functions for configuration. The contract is immutable regarding its logic… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Privileged Token Minting Authority  *(Severity: Medium · Status: Unresolved)*

The functions send, lzReceiveSimulate, lzReceive, and reportSupply allow privileged roles (endpoint or supplyReporter) to mint new tokens or adjust the total supply. This capability can lead to the dilution of existing token holders if the privileged addresses are compromised or act maliciously.

**Recommendation:** Restrict the 'supplyReporter' role to a multi-signature wallet or a decentralized governance contract. Implement a strict upper bound on supply increases and consider adding a timelock to any supply-altering operations.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x5fe5…7e38 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 16.6% of supply. What remains: 9.1% in wallets, 7.4% in other contracts. 294 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Pangea (PANGEA), market cap $20M, rank #828. 294 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $161K (DexScreener, all pools). 24h trading volume $1.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. The class itself adds no points; the contract and market facts decide the score. Basis: a copy of the coin from its home chain (solana), minted here by LayerZero (lzReceive). Tokenomics — Supply: mintable with no on-chain cap found. Control: a contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $161K of DEX liquidity across 4 pools. Launch: under a day of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa551...86ea`](https://basescan.org/address/0xa551def8a44ea423caa58da45b3f5764004286ea) |
| **Network** | Base |
| **Price** | $0.002238 |
| **24h Volume** | $1.20M |
| **Liquidity** | $161.1K |
| **Volume / Liquidity** | 7.4× |
| **Token Age** | 5h |
| **Top-10 Holders** | 16.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2320 buys / 1878 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xfd3272623e21c9ef661119d582b4c13ec4a0243e6f7bc13452fe57bee9304a59)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pangea-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
