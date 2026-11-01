---
token: Dimo
ticker: DIMO
network: polygon
risk_score: 72
status: high
date: 2026-11-01
---

# Dimo (DIMO) — Smart Contract Security Analysis | Polygon

> **Risk Score: 72/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dimo-poly)

---

## Audit Summary

The Dimo token is an upgradeable ERC-20 implementation utilizing the UUPS proxy pattern. While the contract leverages standard OpenZeppelin libraries for security, it contains a critical vulnerability regarding the initialization of the implementation contract and significant centralization risks via privileged roles. 7.1 Architecture: UUPS Proxy. 7.2 Code Security: Critical initialization flaw. 7.3 Access Control: High centralization. 7.4 Economic: Minting capabilities. 7.5 Governance: Voting enabled. 7.6 External: Standard ERC-20. 7.7 Upgrades: UUPS enabled. 7.8 Operations: Pausable.

> **Final Recommendation:** Immediately initialize the implementation contract to prevent unauthorized takeover. Transition privileged roles (MINTER, PAUSER) to a multi-signature wallet or a decentralized governance contract to mitigate centralization risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The codebase utilizes well-vetted OpenZeppelin libraries for core functionality. The implementation of UUPS proxy patterns is standard, though the lack of initialization protection on the… |
| **Governance / Economics** | 1/10 | High | The token economy is heavily centralized, with privileged roles capable of minting tokens and pausing transfers. These roles allow for arbitrary supply inflation and total liquidity freezing.… |
| **Upgrades** | 1/10 | High | The contract uses the UUPS upgradeable pattern, which is generally safer than Transparent proxies. However, the implementation contract is not initialized, allowing an attacker to potentially take… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 46.4% |
| **Top-3 Unlocked** | 76.1% |

## Security Findings

_🔴 1 Critical · 🟡 3 Medium · ⚪ 4 Informational_

### `CD-01` — Unprotected Implementation Initialization  *(Severity: Critical · Status: Unresolved)*

The implementation contract lacks an initialization guard, allowing any user to call the initialize function and potentially take control of the logic contract.

**Recommendation:** Add a constructor that calls _disableInitializers() to prevent the implementation contract from being initialized.


### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

Privileged addresses with the MINTER_ROLE or DEPOSITOR_ROLE can mint an unlimited number of tokens, which can dilute the value of existing holdings.

**Recommendation:** Restrict minting capabilities to a time-locked governance contract or a multi-sig wallet.


### `CP-04` — Centralized Pause Control  *(Severity: Medium · Status: Unresolved)*

Addresses with the PAUSER_ROLE can pause all token transfers, effectively freezing user liquidity at will.

**Recommendation:** Implement a multi-sig requirement for pausing or remove the pause functionality if not strictly required for emergency response.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 96.0% is held, unlocked, by 10 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 90% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 55.0% of supply. What remains: 0.0% in wallets, 55.0% in other contracts. 80,213 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as DIMO (DIMO), market cap $10M, rank #1225. 80,213 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $35K (DexScreener, all pools). 24h trading volume $1.7M (CoinGecko, all markets, daily snapshot). 24h trading volume $39K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.786 on 2023-12-18; the price is now 96.9463% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: vote delegation in its code. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $35K of DEX liquidity across 27 pools. Launch: 1419 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe261...61db`](https://polygonscan.com/address/0xe261d618a959afffd53168cd07d12e37b26761db) |
| **Network** | Polygon |
| **Price** | $0.02232 |
| **24h Volume** | $38.3K |
| **Liquidity** | $31.8K |
| **Volume / Liquidity** | 1.2× |
| **Token Age** | 3y |
| **Top-10 Holders** | 55.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 697 buys / 743 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/polygon/0x41e64a5bc929fa8e6a9c8d7e3b81a13b21ff3045)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dimo-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-01*
