---
token: Uriel
ticker: URIEL
network: ethereum
risk_score: 72
status: high
date: 2026-11-02
---

# Uriel (URIEL) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 72/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/uriel-eth)

---

## Audit Summary

GuardToken is a standard ERC-20 token with centralized administrative controls. The protocol allows the owner to manage trading status, tax exemptions, and liquidity pool configurations. A designated minter role has the authority to increase the total supply up to a defined cap. The contract is not upgradeable, and the ownership is currently held by an EOA.

> **Final Recommendation:** The protocol should consider transitioning ownership to a multi-signature wallet or a decentralized governance contract to mitigate single-point-of-failure risks. Additionally, implementing a timelock on sensitive administrative functions like openTrading would provide transparency to token holders regarding changes to trading rules.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract implements standard ERC-20 functionality with robust input validation in administrative functions. 7.1 Architecture is straightforward, utilizing OpenZeppelin standards. 7.2 Code… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance risks are centered on the high degree of centralization. The owner has total control over trading availability and tax logic, which could be used to restrict… |
| **Upgrades** | 2/10 | High | 7.7 Upgrades are not supported as the contract is immutable. 7.8 Operations are managed via EOA, which carries inherent key management risks. No proxy patterns are utilized. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 4 Medium · ⚪ 4 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The minter address has the power to create new tokens at will up to the CAP. This allows the controller to dilute the value of existing holdings without community consent.

**Recommendation:** Restrict the minting capability to a multi-signature wallet or implement a hard-coded minting schedule that cannot be altered by a single address.


### `CP-05` — Centralized Trading Control  *(Severity: Medium · Status: Unresolved)*

The owner can toggle the trading status via the openTrading function. This gives the owner the ability to halt all transfers or sales, effectively freezing user assets.

**Recommendation:** Remove the ability to halt trading once it has been opened, or implement a timelock to ensure that any changes to trading status are announced in advance.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x4fd2…ac88 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $77K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 96.3% of supply. Of that, 74.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 3.3% in wallets, 18.8% in other contracts. 55 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

55 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: 3% on buy, 3% on sell. Market: $9K of DEX liquidity across 3 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x114c...e407`](https://etherscan.io/address/0x114c3473d43d320c4f093f5ce5ecf32f2a2ee407) |
| **Network** | Ethereum |
| **Price** | $0.001418 |
| **24h Volume** | $75.9K |
| **Liquidity** | $8.8K |
| **Volume / Liquidity** | 8.6× |
| **Token Age** | 7h |
| **Top-10 Holders** | 96.3% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 316 buys / 253 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x22216a3c79d90c0ed5c445400d31d251fd62883c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/uriel-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
