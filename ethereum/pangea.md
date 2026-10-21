---
token: Pangea
ticker: PANGEA
network: ethereum
risk_score: 65
status: high
date: 2026-10-21
---

# Pangea (PANGEA) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 65/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pangea-eth)

---

## Audit Summary

The PangeaOFT contract implements an Omnichain Fungible Token (OFT) standard. The architecture relies on LayerZero for cross-chain messaging and includes specific roles for supply reporting and metadata management. While the core ERC-20 logic is standard, the protocol grants significant power to external roles, specifically the supplyReporter, which can influence token supply dynamics.

> **Final Recommendation:** It is recommended to implement a multi-signature wallet or a time-locked governance contract for the supplyReporter and metadataAuthority roles to mitigate the risk of single-point-of-failure compromises. Ensure that the addresses assigned to these roles are monitored for unauthorized activity.

Furthermore, maintain strict operational security for the private keys associated with these privileged roles. Consider implementing an event-monitoring system to alert stakeholders whenever the supplyReporter triggers a supply update, ensuring transparency for the community.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract utilizes the established LayerZero OFT standard, ensuring robust cross-chain interoperability. 7.1 Architecture follows standard OApp patterns, while 7.2 Code Security reflects clean… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic and 7.5 Governance risks are centered on the supplyReporter role. This role has the authority to report supply changes, which directly impacts the token's total supply. While limited by… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not implemented via proxy patterns in this contract. The contract is immutable in its logic, which eliminates risks associated with malicious implementation updates. 7.8 Operations… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The supplyReporter role has the authority to call reportSupply, which can increase the total supply of the token. Additionally, the LayerZero endpoint can trigger minting via lzReceive. This allows these entities to dilute existing token holders by increasing the circulating supply.

**Recommendation:** Transition the supplyReporter role to a decentralized governance contract or a multi-signature wallet. Implement a hard cap on the total supply that cannot be overridden by any role to provide stronger guarantees to token holders.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xb644…5475 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 21.1% of supply. What remains: 12.2% in wallets, 9.0% in other contracts. 180 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

180 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $125K (DexScreener, all pools). 24h trading volume $567K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $125K of DEX liquidity across 9 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6434...96ea`](https://etherscan.io/address/0x6434e57e8d12b92bb4d0b1efb3274748b75196ea) |
| **Network** | Ethereum |
| **Price** | $0.001332 |
| **24h Volume** | $566.8K |
| **Liquidity** | $123.6K |
| **Volume / Liquidity** | 4.6× |
| **Token Age** | 4h |
| **Top-10 Holders** | 21.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 878 buys / 576 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xbece910c27445aaec41c4ce87e0f10bbba2124909ce7997038b575fdd373c91c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pangea-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
