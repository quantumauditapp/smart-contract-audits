---
token: trUSD
ticker: TRUSD
network: ethereum
risk_score: 12
status: low
date: 2026-08-12
---

# trUSD (TRUSD) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 12/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/trusd-eth)

---

## Audit Summary

The TrUSD contract implements an upgradeable ERC-20 token with a two-tiered access control system. While leveraging battle-tested OpenZeppelin libraries and a multisig for the primary admin role, a significant risk arises from the immediate execution capabilities of the TIMELOCK_ADMIN_ROLE for critical functions like token minting and contract upgrades, lacking the timelock present for the DEFAULT_ADMIN_ROLE. This centralization of immediate power, if compromised, could lead to severe economic or operational consequences.

> **Final Recommendation:** To enhance the security posture of the TrUSD contract, it is strongly recommended to implement a timelock mechanism for all critical actions performed by the TIMELOCK_ADMIN_ROLE, particularly for `setMinter` and `_authorizeUpgrade`. This would introduce a necessary delay, allowing for scrutiny and intervention in case of a compromise or error. Additionally, ensure the TIMELOCK_ADMIN_ROLE is controlled by a robust, high-threshold multi-signature wallet, and consider adding a timelock or additional approval steps for the `setTimelockAdmin` function to prevent immediate role transfers.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract demonstrates good technical architecture (7.1) by utilizing OpenZeppelin's upgradeable ERC-20 and AccessControlDefaultAdminRules libraries, ensuring a solid foundation for code security… |
| **Governance / Economics** | 9/10 | Low | The governance and economic model (7.5, 7.4) benefits from a two-tiered access control structure, where the DEFAULT_ADMIN_ROLE (assumed multisig with a 1-day timelock) controls the… |
| **Upgrades** | 5/10 | Medium | The contract correctly implements the UUPS upgradeability pattern (7.7) using OpenZeppelin's `UUPSUpgradeable` module, overriding `_authorizeUpgrade` to restrict upgrade authorization to the… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_⚪ 9 Informational_

### `I-01` — Immediate and Centralized Control over Critical Functions (Minting & Upgrades)  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `TIMELOCK_ADMIN_ROLE` has immediate and centralized control over critical functions: `setMinter` (allowing unlimited token minting) and `_authorizeUpgrade` (allowing instant contract upgrades). Unlike the `DEFAULT_ADMIN_ROLE`, which has a 1-day timelock, actions by the `TIMELOCK_ADMIN_ROLE` can be executed instantly. This concentration of power, coupled with the lack of a timelock for these actions, presents a significant risk of immediate economic manipulation or malicious contract changes if the `TIMELOCK_ADMIN_ROLE` is compromised or misused. (7.3 Access Control, 7.4 Economic, 7.7 Upgrades)

**Recommendation:** Implement a timelock mechanism for all critical actions performed by the `TIMELOCK_ADMIN_ROLE`, specifically for `setMinter` and `_authorizeUpgrade`. This would introduce a delay, allowing for community review and intervention. Additionally, ensure the `TIMELOCK_ADMIN_ROLE` itself is controlled by a robust, multi-signature wallet with a high threshold to mitigate the centralization risk.


### `I-02` — TIMELOCK_ADMIN_ROLE Transfer Mechanism Vulnerability  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `setTimelockAdmin` function allows the current `TIMELOCK_ADMIN_ROLE` to transfer its role to a new address. If the `TIMELOCK_ADMIN_ROLE` is controlled by a single EOA or a low-threshold multisig, a compromise of this entity could lead to an unauthorized transfer of the role, potentially bypassing the `DEFAULT_ADMIN_ROLE`'s timelock for subsequent actions. (7.3 Access Control, 7.8 Operations)

**Recommendation:** Ensure the `TIMELOCK_ADMIN_ROLE` is managed by a highly secure, multi-signature wallet. Consider adding a timelock to the `setTimelockAdmin` function itself, or requiring approval from the `DEFAULT_ADMIN_ROLE` for such a critical transfer.


### `I-03` — One-Time `initializeTimelockAdmin` Call Risk  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initializeTimelockAdmin` function can only be called once by the `DEFAULT_ADMIN_ROLE` to set the initial `TIMELOCK_ADMIN_ROLE`. If an incorrect or compromised address is set during this initial call, it would require the `DEFAULT_ADMIN_ROLE` to manually revoke and regrant the role, which is possible but adds operational complexity and potential for error. (7.8 Operations)

**Recommendation:** Exercise extreme caution and verify the `timelockAdmin` address thoroughly before calling `initializeTimelockAdmin`. Implement robust pre-deployment checks and consider a multi-step initialization process or a mechanism for the `DEFAULT_ADMIN_ROLE` to correct the initial assignment more smoothly if needed.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 99.7% of supply. What remains: 2.8% in wallets, 97.0% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Tori trUSD (TRUSD), market cap $72M, rank #340. Its owner (0x0c6b…8316) controls 2 issuer-backed coins CoinGecko lists on ethereum, $136M together, among them Tori Staked trUSD: one issuer's programme, read on-chain. Verified by: CoinGecko, issuer programme.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $5.2M (DexScreener, all pools). 24h trading volume $900K (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — a 3-of-5 multisig — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Stablecoin — synthetic  *(Severity: Informational · Status: Acknowledged)*

A token designed to hold a fixed value (usually $1). Its safety rests on what backs it and on who can mint, freeze or pause it. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Stablecoins. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: a 3-of-5 multisig. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $5.2M of DEX liquidity across 1 pools. Launch: 26 days of market history.

**Recommendation:** Check what backs the peg and who controls supply: reserve attestations for an issuer-backed coin, collateral and governance for a protocol coin.


### `QA-RECENT` — Recently launched — 26 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 26 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd058...1697`](https://etherscan.io/address/0xd0580192e98ea6ceb9c7b6191ed2e27560911697) |
| **Network** | Ethereum |
| **Price** | $1.0000 |
| **24h Volume** | $900.3K |
| **Liquidity** | $5.16M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 26d |
| **Top-10 Holders** | 99.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 121 buys / 46 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xb723a224c9acf3891b20437b4d55dd45600f5fa3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/trusd-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-12*
