---
token: PVE
ticker: PVE
network: ethereum
risk_score: 67
status: high
date: 2026-10-22
---

# PVE (PVE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 67/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pve-eth)

---

## Audit Summary

The PangeaOFT contract implements an Omnichain Fungible Token (OFT) standard. The architecture relies on LayerZero for cross-chain messaging and utilizes specific roles for supply reporting and metadata management. While the core logic is standard, the ability for privileged roles to influence supply metrics introduces centralized trust requirements.

> **Final Recommendation:** The protocol should consider implementing a multi-signature wallet or a timelock controller for the 'supplyReporter' and 'metadataAuthority' roles to mitigate the risk of single-point-of-failure. Ensure that the addresses assigned to these roles are monitored for unauthorized activity.

Regularly audit the LayerZero endpoint configurations to ensure that cross-chain messaging parameters remain secure. Maintain transparency regarding the supply reporting mechanism to ensure token holders are aware of how the total supply is managed.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract follows the established LayerZero OFT standard, ensuring robust cross-chain interoperability. 7.1 Architecture and 7.2 Code Security are well-implemented using standard libraries. 7.3… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic and 7.5 Governance aspects are centralized. The supplyReporter role has the authority to influence supply reporting, which could impact tokenomics. 7.8 Operations are managed by the… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not implemented via proxy patterns in this contract. The logic is immutable, reducing the risk of unauthorized logic changes. Future changes would require a full contract migration. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The 'supplyReporter' role and the LayerZero endpoint have the ability to mint tokens or influence supply reporting. This allows these privileged entities to potentially dilute the value of existing token holdings by increasing the total supply.

**Recommendation:** Restrict the 'supplyReporter' role to a multi-signature wallet or a decentralized governance contract. Implement a hard cap on the total supply to prevent excessive minting beyond intended limits.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xa6f3…e168 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 14.2% of supply. What remains: 1.3% in wallets, 12.9% in other contracts. 100 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

100 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $19K (DexScreener, all pools). 24h trading volume $150K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $19K of DEX liquidity across 1 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5fa3...f6ea`](https://etherscan.io/address/0x5fa358b0449f32afbe28d39e96d729f7229af6ea) |
| **Network** | Ethereum |
| **Price** | $0.00004116 |
| **24h Volume** | $150.4K |
| **Liquidity** | $18.9K |
| **Volume / Liquidity** | 8.0× |
| **Token Age** | 1d |
| **Top-10 Holders** | 14.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 290 buys / 319 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x32a4c067036b254c848fb71d5901f567b621a903e9f280572a0cd4d503004db0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pve-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
