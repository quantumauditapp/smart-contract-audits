---
token: Player 8453
ticker: PLAYER
network: base
risk_score: 53
status: medium
date: 2026-10-28
---

# Player 8453 (PLAYER) — Smart Contract Security Analysis | Base

> **Risk Score: 53/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/player-8453-base)

---

## Audit Summary

The DopplerERC20V1 contract is a standard ERC-20 token with governance voting capabilities, deployed as an EIP-1167 minimal clone. The architecture is immutable, preventing logic upgrades. While the core token functionality is standard, the contract includes centralized administrative controls that allow the owner to restrict transfers and manage balance limits. The protocol is currently at a medium risk level due to these centralized controls and the inability to recover accidentally sent ETH.

> **Final Recommendation:** The protocol should consider implementing a 'withdrawETH' function restricted to the owner to recover any funds accidentally sent to the contract address. Additionally, to improve decentralization, the owner should consider transitioning the 'lockPool' and 'disableBalanceLimit' functions to a multi-signature wallet or a governance-controlled DAO contract rather than a single EOA.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin libraries for ERC-20 and governance, ensuring robust base logic. 7.1 Architecture is fixed via EIP-1167, providing high security against upgrade-related… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily influenced by the owner's ability to lock pools and modify transfer rules. While this allows for emergency response, it introduces significant… |
| **Upgrades** | 7/10 | Low | 7.7 Upgrades are not supported as this is an EIP-1167 minimal clone. The logic is immutable, which eliminates the risk of malicious implementation swaps. 7.8 Operations are stable, though the lack of… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 62.4% |
| **Top-3 Unlocked** | ⚠️ 97.5% |

## Security Findings

_🟡 3 Medium · ⚪ 5 Informational_

### `CD-01` — Inability to Withdraw ETH  *(Severity: Medium · Status: Unresolved)*

The contract accepts ETH transfers but lacks any function to withdraw or transfer these funds out of the contract. Any ETH sent to the contract address will be permanently locked.

**Recommendation:** Add an 'emergencyWithdraw' or 'withdrawETH' function that allows the owner to recover accidentally sent ETH to a secure address.


### `CP-05` — Centralized Control Over Token Transfers  *(Severity: Medium · Status: Unresolved)*

The contract owner or a designated controller can unilaterally stop or enable token transfers by calling 'lockPool', 'unlockPool', or 'disableBalanceLimit'. This allows the administrator to freeze user funds or restrict trading at their discretion.

**Recommendation:** Implement a time-lock mechanism for these administrative functions or transition control to a decentralized governance body to prevent arbitrary restriction of user assets.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 4 address(es) other than the owner/deployer. One of them — a wallet, 0x8160…287d — holds 62.4% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 70.8% of supply. What remains: 2.8% in wallets, 68.0% in other contracts. 210 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

210 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $54K (DexScreener, all pools). 24h trading volume $222K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: vote delegation in its code. Tokenomics — Supply: fixed — the contract has no mint function. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $54K of DEX liquidity across 7 pools. Launch: under a day of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x442d...fee1`](https://basescan.org/address/0x442d624be3a2b2f430b75f390bb7458c05b4fee1) |
| **Network** | Base |
| **Price** | $0.00007162 |
| **24h Volume** | $221.9K |
| **Liquidity** | $53.8K |
| **Volume / Liquidity** | 4.1× |
| **Token Age** | 3h |
| **Top-10 Holders** | 70.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 995 buys / 1764 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xf0c5795cde743a850df0440ad586a978582ee59d0afc0a10564ed537fd19a5cc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/player-8453-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
