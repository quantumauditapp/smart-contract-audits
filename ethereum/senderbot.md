---
token: Senderbot
ticker: SENDERBOT
network: ethereum
risk_score: 68
status: high
date: 2026-10-31
---

# Senderbot (SENDERBOT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 68/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/senderbot-eth)

---

## Audit Summary

LaunchToken is an EIP-1167 minimal clone implementation featuring integrated holder rewards. The architecture relies on privileged roles (factory, rewardHook, rewardLocker) to manage reward distribution and transfer logic. While the code is well-structured and uses reentrancy guards, the centralization of control over transfer rules and fees presents a significant trust requirement for token holders.

> **Final Recommendation:** Token holders should monitor the activity of the factory and reward-related roles, as these addresses possess significant control over the token's transferability and fee structure. We recommend transitioning these roles to a multi-signature wallet or a decentralized governance contract to mitigate single-point-of-failure risks.

Ensure that all reward funding events are verified on-chain to confirm that the reward pool remains adequately collateralized. The current implementation is secure, but the reliance on centralized controllers necessitates high transparency regarding their operational procedures.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes standard OpenZeppelin-style patterns and EIP-1167 for deployment efficiency. 7.1 Architecture is sound for a clone, and 7.2 Code Security is bolstered by consistent use of… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance aspects are centralized within the factory and reward-specific roles. Privileged addresses have the power to modify transfer rules and fees, which directly impacts the… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades are not applicable as the contract is an EIP-1167 minimal clone, which is immutable by design. 7.8 Operations are stable due to this immutability, preventing logic changes… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `CP-05` — Centralized Control Over Transfer Functionality  *(Severity: Medium · Status: Unresolved)*

Privileged addresses (factory, rewardHook, rewardLocker) can toggle a switch that determines whether transfers are permitted. This allows these controllers to effectively freeze or unfreeze token movements at will.

**Recommendation:** Implement a timelock for any changes to transfer rules or restrict the ability to pause transfers to a decentralized governance vote.


### `CP-07` — Privileged Modification of Transfer Fees  *(Severity: Medium · Status: Unresolved)*

The fee structure applied to token transfers can be modified by privileged addresses. This grants controllers the ability to alter the economic incentives of the token without prior notice to holders.

**Recommendation:** Define hard caps for transfer fees in the contract code to prevent arbitrary increases by privileged roles.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x8984…c449 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-08` — Privileged Modification of Transaction Limits  *(Severity: Low · Status: Unresolved)*

Privileged addresses can change numeric limits such as maximum transaction sizes or wallet thresholds. This could be used to restrict the liquidity or trading behavior of specific users.

**Recommendation:** Document the intended range for these limits and ensure that any changes are communicated to the community via official channels.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 84.3% of supply. What remains: 20.3% in wallets, 64.1% in other contracts. The deployer/owner wallet itself holds 8.1%. 55 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

55 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $18K (DexScreener, all pools). 24h trading volume $49K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $18K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x639b...fbef`](https://etherscan.io/address/0x639b5cd4e7af6e09eeb4e35378633f8f1b76fbef) |
| **Network** | Ethereum |
| **Price** | $0.00002085 |
| **24h Volume** | $49.2K |
| **Liquidity** | $17.8K |
| **Volume / Liquidity** | 2.8× |
| **Token Age** | 10h |
| **Top-10 Holders** | 84.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 176 buys / 117 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x9a10739de84a5b3863e2aabf96ebbbc8f59eec41b4470dd60d9f2f603b00030c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/senderbot-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
