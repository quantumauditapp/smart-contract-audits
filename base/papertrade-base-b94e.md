---
token: Papertrade
ticker: PAPER
network: base
risk_score: 54
status: medium
date: 2026-10-21
---

# Papertrade (PAPER) — Smart Contract Security Analysis | Base

> **Risk Score: 54/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/papertrade-base-b94e)

---

## Audit Summary

The ClankerToken is an ERC-20 compliant token with cross-chain capabilities integrated via the Superchain Token Bridge. The architecture relies on the bridge contract to manage supply fluctuations. While the implementation follows standard OpenZeppelin patterns, the centralized control granted to the bridge for minting and burning poses inherent risks to token holders.

> **Final Recommendation:** Users should be aware that the token supply is dynamic and controlled by the Superchain Token Bridge. We recommend monitoring the bridge's security posture and governance parameters, as any compromise of the bridge contract directly impacts token balances and total supply.

For future iterations, consider implementing a multi-signature requirement or a timelock for administrative actions to reduce the impact of a single-point-of-failure in the bridge integration.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin libraries for ERC-20 and governance features (7.1 Architecture, 7.2 Code Security). The code is clean and follows established patterns for cross-chain… |
| **Governance / Economics** | 1/10 | High | Economic control is centralized within the bridge contract (7.4 Economic, 7.5 Governance). The ability to mint and burn tokens allows for potential supply manipulation if the bridge is compromised.… |
| **Upgrades** | 5/10 | Medium | The contract is not currently using a proxy pattern (7.7 Upgrades). Logic updates would require a full redeployment. Operational security (7.8 Operations) is dependent on the security of the bridge… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 7 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xffa3…0762 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-01` — Privileged Minting Capability  *(Severity: Informational · Status: Unresolved)*

The crosschainMint function allows the bridge contract to increase the total supply of tokens at any time, which can dilute the value of existing holdings. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Ensure that the bridge contract is secured by a multi-signature wallet or a decentralized governance mechanism to prevent unauthorized minting.


### `CP-02` — Privileged Balance Modification  *(Severity: Informational · Status: Unresolved)*

The crosschainBurn function allows the bridge contract to remove tokens from any user's balance, effectively granting the bridge controller the power to seize or destroy user assets. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Implement strict access controls and audit logs for the bridge contract to ensure that burn operations are only executed during legitimate cross-chain transfers.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 1.0% in wallets, 99.0% in other contracts. 4,408 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

4,408 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10.3M (DexScreener, all pools). 24h trading volume $57.9M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10.3M of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd081...eb07`](https://basescan.org/address/0xd0814ce4a2b66e55cdd04f8b9229a5704206eb07) |
| **Network** | Base |
| **Price** | $0.000102 |
| **24h Volume** | $57.88M |
| **Liquidity** | $10.31M |
| **Volume / Liquidity** | 5.6× |
| **Token Age** | 7h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2581 buys / 2526 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xac35de111009ed20e0cf74725f9aeb1eb7f290b3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/papertrade-base-b94e)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
