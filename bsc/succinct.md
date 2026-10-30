---
token: Succinct
ticker: PROVE
network: bsc
risk_score: 67
status: high
date: 2026-10-30
---

# Succinct (PROVE) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 67/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/succinct-bsc)

---

## Audit Summary

The Succinct contract implements an Omnichain Fungible Token (OFT) standard on BSC. The architecture relies on the LayerZero endpoint for cross-chain messaging and token minting/burning. While the implementation follows standard library patterns, the ability to mint tokens via cross-chain messages introduces inherent economic risks regarding supply inflation.

> **Final Recommendation:** The protocol should implement a monitoring system to track cross-chain minting events and total supply changes in real-time to detect anomalous activity. Ensure that the multisig signers are geographically and organizationally distributed to maintain the integrity of the administrative functions.

Regularly audit the LayerZero peer configurations to ensure only authorized chains can trigger minting operations. Consider implementing a global supply cap if the tokenomics model does not explicitly require unbounded cross-chain minting.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes established LayerZero OFT libraries for cross-chain interoperability. 7.1 Architecture is modular, 7.2 Code Security is robust, and 7.3 Access Control is correctly implemented… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic risks are present due to the minting capabilities inherent in the OFT standard. 7.5 Governance is managed via a 3-of-5 multisig, providing a reasonable balance of security and… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are managed by a multisig owner, ensuring that administrative changes require consensus. No further upgradeability… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 92.3% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `CP-01` — Privileged Minting Capability via Cross-Chain Messaging  *(Severity: Medium · Status: Unresolved)*

The functions send, lzReceiveSimulate, and lzReceive allow for the minting of new tokens as part of the cross-chain transfer process. While restricted to the LayerZero endpoint, this mechanism allows the total supply to increase, which could dilute existing holders if the cross-chain bridge is compromised or misconfigured.

**Recommendation:** Implement a hard cap on the total supply or a rate-limiting mechanism on cross-chain minting to mitigate the impact of potential bridge exploits. Monitor the LayerZero endpoint interactions closely for unusual minting patterns.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0x89cf…3fa5 — holds 92.3% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 95.3% of supply. Of that, 15.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 76.3% in wallets, 3.6% in other contracts. 3,672 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Succinct (PROVE), market cap $37M, rank #544. 3,672 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $234K (DexScreener, all pools). 24h trading volume $8.2M (CoinGecko, all markets, daily snapshot). 24h trading volume $524K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. The class itself adds no points; the contract and market facts decide the score. Basis: a copy of the coin from its home chain (ethereum), minted here by LayerZero (lzReceive). Tokenomics — Supply: minted here by LayerZero (lzReceive) against tokens locked or burned on other chains. Control: a 3-of-5 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $234K of DEX liquidity across 3 pools. Launch: 452 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7ddf...5929`](https://bscscan.com/address/0x7ddf164cecfddd0f992299d033b5a11279a15929) |
| **Network** | BNB Chain |
| **Price** | $0.1918 |
| **24h Volume** | $523.9K |
| **Liquidity** | $234.4K |
| **Volume / Liquidity** | 2.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 95.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3207 buys / 3748 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x3353274e21dec3964e56cc227582e320533c5869)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/succinct-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
