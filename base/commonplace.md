---
token: Commonplace
ticker: COMMONPLACE
network: base
risk_score: 63
status: medium
date: 2026-10-31
---

# Commonplace (COMMONPLACE) — Smart Contract Security Analysis | Base

> **Risk Score: 63/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/commonplace-base)

---

## Audit Summary

The DopplerERC20V1 contract is a standard ERC-20 token with governance voting capabilities, deployed as an EIP-1167 minimal clone. The contract implements centralized control mechanisms that allow the owner and controller to restrict token transfers and manage balance limits. While the core ERC-20 logic is standard, the presence of administrative switches and the inability to recover trapped ETH represent the primary security considerations.

> **Final Recommendation:** It is recommended to implement a recovery function for trapped ETH to prevent loss of funds sent to the contract address by mistake. Additionally, consider documenting the specific conditions under which the owner or controller will exercise their power to lock pools or disable balance limits to ensure transparency for token holders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-tested OpenZeppelin libraries for ERC-20 and governance functionality. 7.1 Architecture: The EIP-1167 clone pattern ensures immutable logic. 7.2 Code Security: The… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic: The protocol introduces centralized control over token liquidity via pool locking mechanisms. 7.5 Governance: Voting power is integrated via ERC20Votes, though administrative… |
| **Upgrades** | 7/10 | Low | 7.7 Upgrades: The contract is an immutable EIP-1167 clone; it cannot be upgraded. 7.8 Operations: Administrative functions are clearly defined and restricted. No further upgrade path exists for the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 78.8% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · ⚪ 5 Informational_

### `CD-01` — Inability to Withdraw Trapped ETH  *(Severity: Medium · Status: Unresolved)*

The contract is capable of receiving ETH but lacks any functionality to withdraw or transfer it out. Any ETH sent to the contract address will be permanently locked.

**Recommendation:** Add an owner-restricted function to withdraw ETH from the contract balance to ensure funds are not permanently trapped.


### `CP-05` — Centralized Control Over Token Transfers  *(Severity: Medium · Status: Unresolved)*

The contract includes administrative functions (lockPool, unlockPool, disableBalanceLimit, release) that allow the owner or controller to restrict or enable token transfers. This grants the privileged addresses the ability to halt trading or modify transfer rules at their discretion.

**Recommendation:** Implement a timelock for administrative actions or move these controls to a decentralized governance contract to reduce the impact of a single point of failure.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0x0092…294f — holds 78.8% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 61.5% of supply. What remains: 8.6% in wallets, 52.9% in other contracts. 302 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

302 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $94K (DexScreener, all pools). 24h trading volume $501K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: vote delegation in its code. Tokenomics — Supply: fixed — the contract has no mint function. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $94K of DEX liquidity across 8 pools. Launch: under a day of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x334d...5ba3`](https://basescan.org/address/0x334dbefdedc6ff68d5a883e5ea27a37a137d5ba3) |
| **Network** | Base |
| **Price** | $0.00000207 |
| **24h Volume** | $501.0K |
| **Liquidity** | $93.8K |
| **Volume / Liquidity** | 5.3× |
| **Token Age** | 17h |
| **Top-10 Holders** | 61.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3449 buys / 5409 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x2aee7f290cfec8ea9539c6fcce90e4983aa31e168dc30e74c6c06f01c954ee70)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/commonplace-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
