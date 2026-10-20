---
token: zkCLOB
ticker: Z
network: ethereum
risk_score: 0
status: low
date: 2026-10-04
---

# zkCLOB (Z) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/zkclob-eth)

---

## Audit Summary

The zkCLOB contract is a standard ERC-20 token. A key security strength is that ownership has been renounced on-chain. This action permanently deactivates all functions previously restricted to the owner, such as `excludeFromEnable` and `transferOwnership`, thereby eliminating central control risks and ensuring the contract's immutability.

> **Final Recommendation:** Token holders should be aware that the contract's logic is immutable due to renounced ownership and the absence of upgradeability features. Users should always adhere to standard security practices when interacting with ERC-20 tokens, such as carefully verifying transaction details and granting allowances only to trusted addresses and for necessary amounts.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract implements standard ERC-20 token functionality, including core transfer and approval mechanisms. A significant strength is the renounced ownership, which renders the `excludeFromEnable`… |
| **Governance / Economics** | 10/10 | Low | The economic model is a straightforward ERC-20 token without complex fee structures, rebasing, or other dynamic economic parameters. With ownership renounced, there are no active governance functions… |
| **Upgrades** | 10/10 | Low | The zkCLOB contract is not implemented using a proxy pattern and does not include any upgradeability mechanisms (7.7 Upgrades). This design choice ensures that the contract's logic is immutable and… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 99.9% — TeamFinance |
| **Top-1 Unlocked Holder** | 0.1% |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, LP lock/burn state, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 74.5% of supply. Of that, 23.4% burned, 13.0% locked, 15.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.0% in wallets, 22.3% in other contracts. 758 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as zkCLOB (Z), rank #4933. 758 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked, lock term not visible  *(Severity: Informational · Status: Acknowledged)*

99.9% of the pool's LP is burned or time-locked. 99.9% is held by TeamFinance, but the lock's end date is not published in the data we can read — its duration is unverified. 0.1% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $140K (DexScreener, all pools). 24h trading volume $33K (CoinGecko, all markets, daily snapshot). 24h trading volume $36K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.0789 on 2026-01-04; the price is now 94.5639% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $140K of DEX liquidity across 1 pools. Launch: 327 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1c13...fe48`](https://etherscan.io/address/0x1c13522ca36e5e13c591c0803083d5bb9282fe48) |
| **Network** | Ethereum |
| **Price** | $0.004442 |
| **24h Volume** | $35.6K |
| **Liquidity** | $139.9K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 10mo |
| **Top-10 Holders** | 74.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 156 buys / 127 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x46af68bee5212318b3f30ae14b4ee03fd49fb147)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/zkclob-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-04*
