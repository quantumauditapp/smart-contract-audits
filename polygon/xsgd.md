---
token: XSGD
ticker: XSGD
network: polygon
risk_score: 66
status: high
date: 2026-10-29
---

# XSGD (XSGD) — Smart Contract Security Analysis | Polygon

> **Risk Score: 66/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xsgd-poly)

---

## Audit Summary

The protocol implements a centralized stablecoin architecture with extensive administrative controls. While the code follows standard patterns for regulated assets, it grants significant power to privileged roles, including the ability to freeze accounts, burn balances, and mint supply. The system relies on a multisig owner, which mitigates single-point-of-failure risks for administrative actions.

> **Final Recommendation:** Users should be aware that this token is highly centralized; administrative roles possess the technical capability to freeze assets or modify balances. It is recommended that the protocol maintain high-security standards for the multisig signers and provide transparent documentation regarding the criteria for invoking blacklisting or wiping functions.

Ensure that all administrative keys are stored in hardware security modules (HSMs) or cold storage. Regularly audit the list of addresses assigned to privileged roles to ensure they remain authorized and active.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The codebase utilizes established OpenZeppelin-style patterns for Pausable and Ownable functionality. 7.1 Architecture is modular, separating core logic from administrative controls. 7.2 Code… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance risks are elevated due to the centralized control model. Privileged roles can unilaterally alter supply and restrict user access. 7.6 External dependencies are… |
| **Upgrades** | 1/10 | High | 7.7 Upgrades are managed via a proxy pattern, allowing for logic updates. 7.8 Operations are supported by a 3-of-5 multisig, providing a layer of protection against unauthorized administrative… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Zeppelin Os Legacy |
| **Admin** | Other-Contract |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 60.7% |
| **Top-3 Unlocked** | ⚠️ 86.0% |

## Security Findings

_🟠 1 High · 🟡 4 Medium · ⚪ 4 Informational_

### `CP-02` — Administrative Balance Manipulation  *(Severity: High · Status: Unresolved)*

The lawEnforcementWipingBurn(address) function allows the blacklister role to burn the entire balance of any blacklisted address, effectively seizing user funds.

**Recommendation:** Restrict the use of this function to strictly defined legal or regulatory scenarios and ensure that the process is governed by a transparent, multi-party consensus.


### `CP-01` — Centralized Minting Capability  *(Severity: Medium · Status: Unresolved)*

The mint(address,uint256) function allows authorized minters to increase the total supply of the token, which can dilute the value of existing holdings.

**Recommendation:** Implement a time-lock or multi-signature requirement for minting operations to ensure transparency and prevent unauthorized supply expansion.


### `CP-04` — Global Transfer Pause  *(Severity: Medium · Status: Unresolved)*

The pause and unpause functions allow the pauser role to halt all token transfers, preventing users from moving their assets during an emergency or administrative action.

**Recommendation:** Limit the scope of the pause functionality if possible, or ensure that the pause trigger is subject to strict governance oversight.


### `CP-06` — Individual Account Blacklisting  *(Severity: Medium · Status: Unresolved)*

The blacklist and unBlacklist functions allow the blacklister role to prevent specific addresses from transferring or receiving tokens, effectively freezing user assets.

**Recommendation:** Establish clear, public criteria for when an address may be blacklisted to protect users from arbitrary or malicious account freezing.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 97.4% is held, unlocked, by 10 address(es) other than the owner/deployer. One of them — a contract, 0xa6e6…c479 — holds 60.7% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 67% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 70.8% of supply. Of that, 2.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 58.6% in wallets, 9.6% in other contracts. 4,925 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as XSGD (XSGD), market cap $13M, rank #1118. 4,925 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $254K (DexScreener, all pools). 24h trading volume $543K (CoinGecko, all markets, daily snapshot). 24h trading volume $177.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Stablecoin — issuer-backed (fiat reserves)  *(Severity: Informational · Status: Acknowledged)*

A token designed to hold a fixed value (usually $1). Its safety rests on what backs it and on who can mint, freeze or pause it. Its identity is not independently verified, so it gets none of the allowances an established stablecoin gets: every power its owner holds over supply and transfers is scored in full, because a peg is only as good as whoever can mint. Basis: CoinGecko category: Fiat-backed Stablecoin. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 3-of-5 multisig. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $254K of DEX liquidity across 12 pools. Launch: 1497 days of market history.

**Recommendation:** Check what backs the peg and who controls supply: reserve attestations for an issuer-backed coin, collateral and governance for a protocol coin.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xdc33...1995`](https://polygonscan.com/address/0xdc3326e71d45186f113a2f448984ca0e8d201995) |
| **Network** | Polygon |
| **Price** | $0.7812 |
| **24h Volume** | $393.3K |
| **Liquidity** | $169.5K |
| **Volume / Liquidity** | 2.3× |
| **Token Age** | 4y |
| **Top-10 Holders** | 70.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 33 buys / 110 sells |

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

- [View on DexScreener](https://dexscreener.com/polygon/0x1f6082db7c8f4b199e17090cd5c8831a1dad1997)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xsgd-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
