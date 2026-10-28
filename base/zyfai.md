---
token: ZyFAI
ticker: ZFI
network: base
risk_score: 46
status: medium
date: 2026-10-28
---

# ZyFAI (ZFI) — Smart Contract Security Analysis | Base

> **Risk Score: 46/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/zyfai-base)

---

## Audit Summary

The ZyfaiOFT contract is an Omnichain Fungible Token (OFT) implementation using LayerZero standards. The architecture is robust, leveraging established libraries for cross-chain messaging. The primary risk involves the minting capability inherent in the OFT standard, which allows for supply expansion during cross-chain transfers.

> **Final Recommendation:** The protocol is well-structured. We recommend maintaining the multisig threshold and ensuring that the LayerZero endpoint configuration remains audited and monitored for any updates to the underlying messaging protocol.

Users should be aware that the total supply of the token is dynamic due to the OFT cross-chain minting mechanism. Ensure that the multisig signers are geographically and organizationally distributed to mitigate single-point-of-failure risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard LayerZero OFT libraries, ensuring 7.1 Architecture and 7.2 Code Security compliance. 7.3 Access Control is correctly implemented using Ownable for administrative… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance risks are centered on the minting mechanism. While necessary for cross-chain functionality, the ability to mint tokens via lzReceive introduces potential dilution… |
| **Upgrades** | 3/10 | High | The contract is not upgradeable (7.7 Upgrades), which eliminates risks associated with proxy logic flaws. 7.8 Operations are managed via standard ownership patterns. No further upgradeability… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.6% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `CP-01` — Dynamic Token Supply via Cross-Chain Minting  *(Severity: Medium · Status: Unresolved)*

The functions send, lzReceiveSimulate, and lzReceive allow for the minting of new tokens as part of the cross-chain transfer process. This increases the total supply of the token, which can lead to the dilution of existing holders if the cross-chain bridge is compromised or if minting parameters are misconfigured.

**Recommendation:** Monitor the total supply and cross-chain activity closely. Ensure that the LayerZero endpoint and peer configurations are strictly managed by the multisig and that any changes to enforced options are thoroughly tested on a testnet before deployment.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 3 address(es) other than the owner/deployer. One of them — a contract, 0xdb60…f7d7 — holds 99.6% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 67.1% of supply. Of that, 10.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 3.7% in wallets, 52.8% in other contracts. 4,278 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Zyfai (ZFI), market cap $2M, rank #2390. 4,278 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $264K (DexScreener, all pools). 24h trading volume $9K (CoinGecko, all markets, daily snapshot). 24h trading volume $53K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. The class itself adds no points; the contract and market facts decide the score. Basis: a copy of the coin from its home chain (zksync), minted here by LayerZero (lzReceive). Tokenomics — Supply: minted here by LayerZero (lzReceive) against tokens locked or burned on other chains. Control: a 3-of-5 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $264K of DEX liquidity across 6 pools. Launch: 509 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd080...d5ae`](https://basescan.org/address/0xd080ed3c74a20250a2c9821885203034acd2d5ae) |
| **Network** | Base |
| **Price** | $0.01051 |
| **24h Volume** | $52.7K |
| **Liquidity** | $261.4K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 67.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 314 buys / 235 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xc6f63e4bea6682aa502ed94c1301b56230fc03d2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/zyfai-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
