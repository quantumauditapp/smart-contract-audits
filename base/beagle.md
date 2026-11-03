---
token: Beagle
ticker: BGLE
network: base
risk_score: 78
status: high
date: 2026-11-03
---

# Beagle (BGLE) — Smart Contract Security Analysis | Base

> **Risk Score: 78/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/beagle-base)

---

## Audit Summary

The DopplerERC20V1 contract is a standard ERC-20 token with governance voting capabilities, deployed as an EIP-1167 minimal clone. The architecture is immutable, preventing logic upgrades. While the core token functionality is standard, the contract includes centralized administrative controls that allow the owner or controller to restrict token transfers and manage balance limits. Two primary issues were identified: the presence of centralized transfer-blocking mechanisms and the inability to recover accidentally sent ETH.

> **Final Recommendation:** The protocol should implement a 'withdrawETH' function restricted to the owner to allow for the recovery of accidentally sent funds. Additionally, the team should provide clear documentation or a public-facing policy regarding the use of the 'lockPool' and 'disableBalanceLimit' functions to maintain transparency with token holders, as these functions directly impact the ability to trade the token.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes standard OpenZeppelin libraries for ERC-20 and governance features, ensuring robust base logic. 7.1 Architecture: EIP-1167 clone pattern is correctly implemented for gas… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic: The token includes balance limits and pool locking mechanisms that directly impact liquidity and transferability. 7.5 Governance: The owner holds significant power to modify transfer… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades: The contract is an EIP-1167 minimal clone, which is inherently immutable. The implementation address is fixed at deployment, preventing any future logic changes. This eliminates the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · ⚪ 5 Informational_

### `CD-01` — Inability to Withdraw ETH  *(Severity: Medium · Status: Unresolved)*

The contract accepts ETH but lacks any function to withdraw or transfer it out. Any ETH sent to the contract address will be permanently locked and inaccessible to the protocol or its users.

**Recommendation:** Add a function restricted to the owner that allows for the withdrawal of any ETH held by the contract.


### `CP-05` — Centralized Control Over Token Transfers  *(Severity: Medium · Status: Unresolved)*

The owner and controller have the ability to lock pools and disable balance limits, which effectively allows them to halt or restrict token transfers for users. This creates a centralized point of failure where the protocol's utility can be unilaterally suspended.

**Recommendation:** Implement a timelock for all administrative actions that affect transferability to provide users with notice, or transition these controls to a decentralized governance contract.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x0dad…d24e — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 91.9% of supply. What remains: 7.2% in wallets, 84.7% in other contracts. 79 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

79 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $29K (DexScreener, all pools). 24h trading volume $87K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: vote delegation in its code. Tokenomics — Supply: fixed — the contract has no mint function. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $29K of DEX liquidity across 4 pools. Launch: under a day of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb8a4...dba3`](https://basescan.org/address/0xb8a49d0e436512b462365496974f5e3dafaddba3) |
| **Network** | Base |
| **Price** | $0.0000003 |
| **24h Volume** | $87.0K |
| **Liquidity** | $29.0K |
| **Volume / Liquidity** | 3.0× |
| **Token Age** | 3h |
| **Top-10 Holders** | 91.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 859 buys / 1287 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x2fb04054960e0b7afc14497352aaac4a227e6d1c952f728f46bde68018b56836)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/beagle-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
