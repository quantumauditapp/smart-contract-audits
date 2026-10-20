---
token: e0e.fun
ticker: E0E
network: ethereum
risk_score: 51
status: medium
date: 2026-10-20
---

# e0e.fun (E0E) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 51/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/e0efun-eth)

---

## Audit Summary

The e0e contract is a standard ERC-20 implementation lacking administrative controls or upgradeability. The architecture is simple, but a critical initialization flaw prevents the token from functioning as intended, as the state variable tracking balances is never populated.

> **Final Recommendation:** The contract must be redeployed with a proper constructor or initialization function to populate the initial supply of tokens. Without this, the _held mapping remains empty, rendering all transfer functions unusable as they will consistently revert due to insufficient balance checks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements standard ERC-20 functionality with safe arithmetic via unchecked blocks. 7.1 Architecture is monolithic and 7.2 Code Security is hampered by a critical initialization failure.… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic and 7.5 Governance factors are not applicable as the contract lacks administrative functions or complex economic mechanisms. The token supply logic is currently non-functional due to the… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not supported as the contract is a standard, immutable deployment. 7.8 Operations are limited to standard token transfers, which are currently blocked by the initialization issue. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 4 Informational_

### `CD-01` — Uninitialized State Variable  *(Severity: High · Status: Unresolved)*

The contract fails to initialize the _held mapping, which tracks user balances. Because no tokens are minted or assigned during deployment, the transfer and transferFrom functions will always fail when checking for sufficient balances.

**Recommendation:** Implement a constructor that assigns the total supply to the deployer's address or a designated initial holder.


### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 41.2% of supply. What remains: 39.7% in wallets, 1.5% in other contracts. The deployer/owner wallet itself holds 25.9%. A holder that also controls the contract can sell into its own liquidity. 86 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x7973…108a — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

86 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $70K (DexScreener, all pools). 24h trading volume $66K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $70K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0d3b...157c`](https://etherscan.io/address/0x0d3b9f4d2f46424174686f9279794f36d73e157c) |
| **Network** | Ethereum |
| **Price** | $0.0001569 |
| **24h Volume** | $65.6K |
| **Liquidity** | $69.9K |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 23h |
| **Top-10 Holders** | 41.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 185 buys / 80 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x77e76e976b7a183df42ea75b2a6b95ba66df3fae6888c5fed9c47575fa4852e1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/e0efun-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
