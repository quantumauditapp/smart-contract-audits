---
token: Zero Gap
ticker: ZGAP
network: base
risk_score: 54
status: medium
date: 2026-10-25
---

# Zero Gap (ZGAP) — Smart Contract Security Analysis | Base

> **Risk Score: 54/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/zero-gap-base)

---

## Audit Summary

The PangeaOFTV2 contract implements an Omnichain Fungible Token (OFT) standard on the Base network. The architecture relies on LayerZero for cross-chain messaging and utilizes a multi-role access control system for supply management and metadata updates. While the core logic follows standard OFT patterns, the presence of privileged minting capabilities requires careful monitoring of the supply reporter role.

> **Final Recommendation:** The protocol should implement a multi-signature wallet or a timelock controller for the 'supplyReporter' and 'metadataAuthority' roles to mitigate the risk of single-point-of-failure compromises. Additionally, ensure that the addresses assigned to these roles are monitored for anomalous activity.

Regular audits of the LayerZero configuration and the 'enforcedOptions' state are recommended to ensure cross-chain messaging remains secure and aligned with the protocol's intended economic parameters.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture (7.1) is robust, leveraging established LayerZero OFT standards for cross-chain interoperability. Code security (7.2) is high, with clean implementation of ERC-20 and OFT interfaces.… |
| **Governance / Economics** | 1/10 | High | Economic (7.4) and Governance (7.5) risks are centered on the supply reporter role. The ability to mint tokens via reportSupply or cross-chain messages introduces potential dilution risks for… |
| **Upgrades** | 3/10 | High | The contract is not currently deployed as a proxy (7.7), meaning the logic is immutable. This eliminates risks associated with malicious proxy upgrades. Future changes would require a full migration… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 56.1% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Privileged Minting and Supply Manipulation  *(Severity: Medium · Status: Unresolved)*

The functions 'send', 'lzReceive', 'lzReceiveSimulate', and 'reportSupply' allow privileged roles (endpoint or supplyReporter) to increase the total token supply. This capability can lead to the dilution of existing token holders if the privileged roles are compromised or act maliciously.

**Recommendation:** Restrict the 'supplyReporter' role to a multi-signature wallet or a decentralized governance contract. Implement a hard cap on the total supply if possible, or introduce a timelock for any significant supply adjustments.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a contract, 0x6fb9…43bf — holds 56.1% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 12.5% of supply. What remains: 5.2% in wallets, 7.3% in other contracts. 90 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

90 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $30K (DexScreener, all pools). 24h trading volume $192K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $30K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xdba1...96ea`](https://basescan.org/address/0xdba134ad399e15d9175ce6bc97beca7001fb96ea) |
| **Network** | Base |
| **Price** | $0.00009164 |
| **24h Volume** | $191.6K |
| **Liquidity** | $30.3K |
| **Volume / Liquidity** | 6.3× |
| **Token Age** | 7h |
| **Top-10 Holders** | 12.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1063 buys / 896 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x53bf62e3920ef10e593c8a1b24a091916ea00d076913a38b9767b3903a57c7c1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/zero-gap-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
