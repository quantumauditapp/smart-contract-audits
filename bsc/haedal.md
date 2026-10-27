---
token: Haedal
ticker: HAEDAL
network: bsc
risk_score: 73
status: high
date: 2026-10-27
---

# Haedal (HAEDAL) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 73/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/haedal-bsc)

---

## Audit Summary

The BridgeToken contract is a standard ERC-20 implementation utilizing a Beacon proxy pattern. The contract exhibits standard token behavior with centralized administrative control over minting and metadata updates. No critical vulnerabilities were identified during the static analysis of the implementation logic.

> **Final Recommendation:** The protocol should transition the owner role to a multi-signature wallet or a decentralized governance contract to mitigate single-point-of-failure risks. Ensure that the Beacon proxy owner is also secured with similar multi-party authorization to prevent unauthorized implementation changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows a standard Beacon proxy pattern, ensuring consistent implementation across instances. 7.1 Architecture is robust, utilizing OpenZeppelin-style standards for ERC-20… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance risks are centered on the centralized owner address. The owner has the authority to mint new tokens and modify metadata, which could impact token supply and identity.… |
| **Upgrades** | 1/10 | High | 7.7 Upgrades are managed via a Beacon proxy, which is a secure and standard approach for multi-contract deployments. This allows for efficient implementation updates without migrating user balances.… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x9f82…c193 — holds 99.9% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-POWERS` — What the token's controller can do  *(Severity: Medium · Status: Acknowledged)*

The contract lets its controller — a contract — mint new supply. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 96.5% of supply. Of that, 5.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 89.9% in wallets, 1.0% in other contracts. 2,622 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Haedal Protocol (HAEDAL), market cap $4M, rank #1740. 2,622 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $205K (DexScreener, all pools). 24h trading volume $9.4M (CoinGecko, all markets, daily snapshot). 24h trading volume $348K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.3 on 2025-07-16; the price is now 92.7106% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Liquid Staking Governance Tokens. Tokenomics — Supply: mintable with no on-chain cap found. Control: a contract. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $205K of DEX liquidity across 2 pools. Launch: 547 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3d9b...4967`](https://bscscan.com/address/0x3d9be0ac1001cd81c32464276d863d2ffdca4967) |
| **Network** | BNB Chain |
| **Price** | $0.02761 |
| **24h Volume** | $347.9K |
| **Liquidity** | $205.5K |
| **Volume / Liquidity** | 1.7× |
| **Token Age** | 1y |
| **Top-10 Holders** | 96.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3908 buys / 3443 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x8063181179b613b7b28f2c208146b701a184f672)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/haedal-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
