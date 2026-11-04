---
token: XTO
ticker: XTO
network: base
risk_score: 67
status: high
date: 2026-11-04
---

# XTO (XTO) — Smart Contract Security Analysis | Base

> **Risk Score: 67/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xto-base-652b)

---

## Audit Summary

ClankerToken is an ERC-20 compliant token on the Base network designed for cross-chain interoperability via the Superchain Token Bridge. The contract implements standard OpenZeppelin libraries for governance and security. While the architecture is robust for its intended cross-chain purpose, it grants significant control to the bridge contract, which poses inherent risks to token holders.

> **Final Recommendation:** The protocol should ensure that the Superchain Token Bridge remains the sole entity with mint/burn permissions and that its own security audits are kept up to date. Users should be aware that the token supply is dynamic and controlled by the bridge's cross-chain logic.

Regular monitoring of the bridge's administrative keys and cross-chain event logs is recommended to detect any anomalous minting or burning activities. No further code changes are required for the current implementation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract follows standard ERC-20 and ERC-7802 patterns, ensuring high compatibility with existing DeFi infrastructure. 7.1 Architecture and 7.2 Code Security are well-implemented using… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance aspects are centralized within the bridge and admin roles. The ability to mint and burn tokens is strictly gated to the bridge, which is a design requirement for… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades are not implemented via proxy patterns in this contract, reducing complexity. 7.8 Operations are straightforward, with administrative functions limited to metadata updates. The lack of… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 6 Informational_

### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 91.8% of supply. What remains: 29.8% in wallets, 62.0% in other contracts. The deployer/owner wallet itself holds 21.8%. A holder that also controls the contract can sell into its own liquidity. 1,042 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xffa3…0762 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-01` — Privileged Minting Capability  *(Severity: Informational · Status: Unresolved)*

The crosschainMint function allows the Superchain Token Bridge to increase the total supply of the token. This can lead to the dilution of existing token holders' value if the bridge is compromised or misconfigured. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Ensure that the bridge contract is secured with multi-signature requirements and that minting events are monitored by an automated alerting system.


### `CP-02` — Privileged Balance Manipulation  *(Severity: Informational · Status: Unresolved)*

The crosschainBurn function allows the Superchain Token Bridge to remove tokens from any user's balance. While intended for cross-chain transfers, this function grants the bridge the power to effectively seize or destroy user funds. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Implement strict circuit breakers or rate limits on the bridge's ability to burn tokens to prevent mass-seizure events in the event of a bridge exploit.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,042 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $385K (DexScreener, all pools). 24h trading volume $80K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $385K of DEX liquidity across 3 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe417...78ea`](https://basescan.org/address/0xe4176f02127b8c929ac0ccd66e24663a48ae78ea) |
| **Network** | Base |
| **Price** | $0.00000495 |
| **24h Volume** | $80.0K |
| **Liquidity** | $384.5K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 4h |
| **Top-10 Holders** | 91.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2854 buys / 596 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x7deeca2aff60c549a0cfb25db75ac1bc2c0853839dc8a04a178a6507eba8cc23)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xto-base-652b)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
