---
token: OFFLINE RESEARCH
ticker: OFFR
network: base
risk_score: 82
status: high
date: 2026-11-01
---

# OFFLINE RESEARCH (OFFR) — Smart Contract Security Analysis | Base

> **Risk Score: 82/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/offline-research-base)

---

## Audit Summary

The DopplerERC20V1 contract is a standard ERC-20 token with governance voting capabilities, deployed as an EIP-1167 minimal clone. The contract implements centralized control mechanisms over transfer logic and balance limits. While the code is structurally sound and follows standard OpenZeppelin patterns, the presence of administrative switches that can halt transfers or modify token rules introduces significant centralization risk. Additionally, the contract lacks a mechanism to recover accidentally sent ETH.

> **Final Recommendation:** The protocol should consider implementing a multi-signature wallet or a timelock contract for the owner address to mitigate the risks associated with centralized control over transfer logic. This would provide transparency and prevent unilateral actions by a single compromised key.

Furthermore, adding a function to withdraw accidentally sent ETH would improve the contract's robustness and prevent permanent loss of funds. Ensure that all administrative actions are logged and monitored to maintain accountability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes well-tested OpenZeppelin libraries for ERC-20 and governance functionality. 7.1 Architecture: EIP-1167 clone pattern ensures immutable logic. 7.2 Code Security: Logic is clean… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic: The token includes balance limits and pool locking mechanisms. 7.5 Governance: The owner holds significant power to restrict liquidity and modify token behavior. These controls allow… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades: The contract is an EIP-1167 minimal clone, meaning the implementation logic is fixed and cannot be upgraded. 7.8 Operations: Administrative functions are restricted to the owner or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 75.3% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · ⚪ 5 Informational_

### `CD-01` — Locked ETH in Contract  *(Severity: Medium · Status: Unresolved)*

The contract is capable of receiving ETH but lacks any function to withdraw or transfer it out. Any ETH sent to the contract address will be permanently locked.

**Recommendation:** Add an owner-restricted function to withdraw ETH from the contract to prevent permanent loss of funds.


### `CP-05` — Centralized Control Over Token Transfers  *(Severity: Medium · Status: Unresolved)*

The owner and controller have the ability to toggle transfer restrictions and lock liquidity pools via functions like lockPool, unlockPool, and disableBalanceLimit. This allows the administrator to unilaterally halt trading or restrict user access to their tokens.

**Recommendation:** Implement a timelock for all administrative functions that modify transfer rules to provide users with notice before changes take effect.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0x511a…ac0c — holds 75.3% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 86.9% of supply. What remains: 12.2% in wallets, 74.7% in other contracts. 89 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

89 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $38K (DexScreener, all pools). 24h trading volume $76K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: vote delegation in its code. Tokenomics — Supply: fixed — the contract has no mint function. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $38K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xee90...1ba3`](https://basescan.org/address/0xee9069e8f520652e59674fad2120f6dea2671ba3) |
| **Network** | Base |
| **Price** | $0.00000054 |
| **24h Volume** | $76.0K |
| **Liquidity** | $38.4K |
| **Volume / Liquidity** | 2.0× |
| **Token Age** | 2h |
| **Top-10 Holders** | 86.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 638 buys / 1037 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x822911a8b8b2a68f4c1309ef75d41c17f669c07886e5c1956f77f2ddf49f456b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/offline-research-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-01*
