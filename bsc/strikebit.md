---
token: StrikeBit
ticker: STRIKE
network: bsc
risk_score: 41
status: medium
date: 2026-10-10
---

# StrikeBit (STRIKE) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 41/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/strikebit-bsc)

---

## Audit Summary

The BurnableTeamToken contract implements a standard ERC-20 token with burnable functionality and owner-controlled metadata. No critical or high-severity vulnerabilities were identified during the audit. The contract's design is straightforward, and its core functionalities adhere to expected ERC-20 behavior.

> **Final Recommendation:** The BurnableTeamToken contract demonstrates a robust implementation of an ERC-20 token with standard burnable features. To maintain security, it is recommended to ensure the owner's private key is securely managed and to carefully vet any new owner address during `transferOwnership`. Regular monitoring of the contract's activity on the blockchain is also advised.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract, `BurnableTeamToken`, is an ERC-20 compliant token with burnable capabilities, inheriting from `Ownable` and `ERC20Burnable`. Its core `transfer` and `transferFrom` functions are… |
| **Governance / Economics** | 2/10 | High | The contract utilizes the `Ownable` pattern, granting a single owner address control over specific administrative functions. The owner can `transferOwnership` to a new address or `renounceOwnership`… |
| **Upgrades** | 6/10 | Medium | The `BurnableTeamToken` contract is not designed as an upgradeable proxy. It is a standard, non-upgradeable implementation, meaning its logic cannot be modified post-deployment (7.7 Upgrades). This… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 46.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 3 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $20K (DexScreener, all pools). 24h trading volume $89K (CoinGecko, all markets, daily snapshot). 24h trading volume $44K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.144 on 2026-04-20; the price is now 99.5057% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 94.8% of supply. What remains: 4.1% in wallets, 90.7% in other contracts. 6,610 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as StrikeBit AI (STRIKE), rank #5310. 6,610 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $20K of DEX liquidity across 2 pools. Launch: 376 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2aa8...c1af`](https://bscscan.com/address/0x2aa89a0113bcbbcdc5812c6df794e2d9650fc1af) |
| **Network** | BNB Chain |
| **Price** | $0.0007996 |
| **24h Volume** | $43.9K |
| **Liquidity** | $20.3K |
| **Volume / Liquidity** | 2.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 94.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2126 buys / 2021 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xfb1c06dd94c9a65f2c6715397c31790e8f10bed2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/strikebit-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-10*
