---
token: Claus
ticker: CLAUS
network: ethereum
risk_score: 78
status: high
date: 2026-10-06
---

# Claus (CLAUS) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 78/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/claus-eth)

---

## Audit Summary

This audit covers the BurnableToken proxy and its implementation. The contract functions as an upgradeable ERC-20 token with burn capabilities. The implementation utilizes standard OpenZeppelin libraries, and no critical or high-severity vulnerabilities were identified during the audit.

> **Final Recommendation:** The BurnableToken contract demonstrates a robust implementation of an upgradeable ERC-20 token. Given the centralized control by an EOA owner for upgrades and metadata changes, it is crucial to ensure the security of the owner's private key. Implement multi-signature wallets for critical administrative roles, especially for the `ProxyAdmin` owner, to enhance security and mitigate single points of failure. Regularly review and test upgrade procedures to ensure smooth and secure transitions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The BurnableToken contract is an upgradeable ERC-20 token with standard burn functionality. It inherits from OpenZeppelin's `ERC20Upgradeable` and `Ownable2StepUpgradeable`, ensuring robust and… |
| **Governance / Economics** | 1/10 | High | The contract's economic model is straightforward, functioning as a standard ERC-20 token with burn capabilities. There are no complex economic mechanisms or parameters that can be manipulated by… |
| **Upgrades** | 1/10 | High | The contract utilizes an EIP-1967 Transparent Proxy pattern, managed by an OpenZeppelin `ProxyAdmin` contract (7.1 Architecture). The `ProxyAdmin` is owned by an EOA, which allows for future upgrades… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → EOA |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | ⚠️ 2 |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by the token's owner/deployer (0xbb14…f1c5) — they can pull that liquidity at any moment. This is the rug-pull path. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 51% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 19.9% of supply. What remains: 6.6% in wallets, 13.3% in other contracts. 3,193 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

3,193 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.1M (DexScreener, all pools). 24h trading volume $10.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a single wallet (EOA). Code: upgradeable proxy. Fees: no buy or sell tax. Market: $1.1M of DEX liquidity across 26 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1b54...a6b8`](https://etherscan.io/address/0x1b54e762aa34cf6e28e9c082f2848e28e45da6b8) |
| **Network** | Ethereum |
| **Price** | $0.01079 |
| **24h Volume** | $4.67M |
| **Liquidity** | $541.6K |
| **Volume / Liquidity** | 8.6× |
| **Token Age** | 1d |
| **Top-10 Holders** | 19.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 10097 buys / 2786 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xfaa42866f7667e3a1a10d783f3b629171febd45f056336b8df766d74afc0f0f7)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/claus-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-06*
