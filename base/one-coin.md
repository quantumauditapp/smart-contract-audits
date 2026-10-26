---
token: one coin
ticker: ONECOIN
network: base
risk_score: 50
status: medium
date: 2026-10-26
---

# one coin (ONECOIN) — Smart Contract Security Analysis | Base

> **Risk Score: 50/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/one-coin-base)

---

## Audit Summary

The PangeaOFTV2 contract is an Omnichain Fungible Token (OFT) implementation on the Base network. The architecture relies on LayerZero for cross-chain messaging and includes specific roles for metadata management and supply reporting. While the core ERC-20 functionality is standard, the protocol grants significant power to privileged roles, specifically the supplyReporter, which can influence token supply metrics.

> **Final Recommendation:** The protocol should implement a multi-signature wallet or a timelock contract for the 'supplyReporter' and 'owner' roles to mitigate the risk of single-point-of-failure compromises. Additionally, ensure that the addresses assigned to these roles are monitored for anomalous activity.

Regularly audit the LayerZero endpoint configurations and peer settings to ensure cross-chain integrity. Maintain transparency regarding the 'supplyReporter' role's actions to ensure the community is aware of any supply-related adjustments.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes a robust LayerZero OFT architecture, ensuring standard cross-chain interoperability. 7.1 Architecture is well-defined, leveraging established OApp patterns. 7.2 Code Security is… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic and 7.5 Governance aspects are centralized under specific roles. The supplyReporter role has the authority to report supply changes, which could impact tokenomics if compromised. 7.6… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not explicitly implemented via proxy patterns in this contract. 7.8 Operations are managed through owner-restricted functions for setting peers and delegates. The lack of… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 93.3% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Privileged Supply Manipulation Risk  *(Severity: Medium · Status: Unresolved)*

The 'supplyReporter' role has the authority to call 'reportSupply', which can influence the reported token supply. Additionally, the LayerZero endpoint can trigger minting via 'lzReceive' and 'send' functions. If these privileged addresses are compromised, the total supply could be manipulated, leading to token dilution.

**Recommendation:** Restrict the 'supplyReporter' role to a multi-signature wallet or a decentralized governance contract. Implement strict monitoring and alerting for any calls to 'reportSupply' that result in significant supply changes.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 3 address(es) other than the owner/deployer. One of them — a wallet, 0x5b1c…5b46 — holds 93.3% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 37.4% of supply. What remains: 1.4% in wallets, 36.0% in other contracts. 99 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

99 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $24K (DexScreener, all pools). 24h trading volume $204K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $24K of DEX liquidity across 3 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x456a...e6ea`](https://basescan.org/address/0x456ac19c8a72aed16376d57c367640d69ff9e6ea) |
| **Network** | Base |
| **Price** | $0.0000636 |
| **24h Volume** | $204.3K |
| **Liquidity** | $24.5K |
| **Volume / Liquidity** | 8.3× |
| **Token Age** | 1d |
| **Top-10 Holders** | 37.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1280 buys / 1172 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x957a3862984613d312d3ae47976762b8e4d0ee24652c7575ed9dca1427d99436)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/one-coin-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
