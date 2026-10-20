---
token: CC
ticker: CC
network: ethereum
risk_score: 51
status: medium
date: 2026-10-20
---

# CC (CC) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 51/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cc-eth)

---

## Audit Summary

The ArtCoinsTokenV2 is a standard ERC-20 token with additional administrative controls for metadata management and transfer restrictions. The architecture is straightforward, utilizing a centralized admin model for configuration. No critical vulnerabilities were identified in the provided code map; however, the centralized control over transfer rules represents a significant trust requirement for token holders.

> **Final Recommendation:** The protocol is secure in its current implementation. It is recommended to transition the admin role to a multi-signature wallet or a decentralized governance contract to mitigate the risks associated with a single point of failure. 

Additionally, ensure that the canonicalHook and poolManager addresses are carefully managed, as they possess privileged access to the transfer allowance mechanism. Regular monitoring of administrative actions is advised to maintain transparency with the community.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements standard ERC-20 functionality with clean, modular logic. 7.1 Architecture is robust, utilizing clear separation between state management and token transfers. 7.2 Code Security… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance risks are centered on the centralized admin role. The admin has the power to modify transfer rules via setAllowed, which could effectively freeze user assets or… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades are not applicable as the contract is not a proxy. 7.8 Operations are handled via standard administrative functions. The lack of upgradeability ensures immutability of the core logic… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 6 Informational_

### `QA-POWERS` — What the token's controller can do  *(Severity: High · Status: Acknowledged)*

The contract lets its controller — an owner key — pause all transfers. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xbd04…3c64 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 86.5% of supply. What remains: 9.0% in wallets, 77.5% in other contracts. 91 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

91 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $93K (DexScreener, all pools). 24h trading volume $131K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner key. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $93K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x28ef...c789`](https://etherscan.io/address/0x28ef14a55dc93cdcb9001fa038a184967146c789) |
| **Network** | Ethereum |
| **Price** | $0.00009706 |
| **24h Volume** | $131.4K |
| **Liquidity** | $92.7K |
| **Volume / Liquidity** | 1.4× |
| **Token Age** | 9h |
| **Top-10 Holders** | 86.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 403 buys / 162 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xefc18ac111d3cc075f7518574971951fc5907ab2e802cc2617f267a32240aa3e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cc-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
