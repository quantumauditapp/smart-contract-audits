---
token: Naoris Protocol
ticker: NAORIS
network: ethereum
risk_score: 60
status: medium
date: 2026-10-18
---

# Naoris Protocol (NAORIS) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 60/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/naoris-protocol-eth)

---

## Audit Summary

This audit covers the NaorisTokenV3 contract, an ERC-20 token implementation utilizing OpenZeppelin's upgradeable standards, including UUPS proxy, AccessControl, and Pausable features. The contract allows for token transfers, and its operations can be paused by a designated role. No specific vulnerabilities were identified within the provided code map and key function sources.

> **Final Recommendation:** To mitigate the risks associated with centralized control, it is strongly recommended to secure the `DEFAULT_ADMIN_ROLE` and `PAUSER_ROLE` with a robust multi-signature wallet. This ensures that critical operations, such as pausing transfers or initiating upgrades, require consensus from multiple trusted parties, significantly reducing the risk of a single point of failure or malicious action. Additionally, all proposed upgrades should undergo thorough testing and independent security audits before deployment to production.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The NaorisTokenV3 contract is an ERC-20 token built upon well-audited OpenZeppelin upgradeable libraries, ensuring a robust foundation (7.1 Architecture). Key functions like `transfer` and… |
| **Governance / Economics** | 1/10 | High | The contract incorporates `AccessControlUpgradeable` and `PausableUpgradeable`, centralizing significant control (7.3 Access Control). A `PAUSER_ROLE` can halt all token transfers via `pause()` and… |
| **Upgrades** | 1/10 | High | NaorisTokenV3 is implemented as an upgradeable UUPS proxy, allowing the contract logic to be modified in the future (7.7 Upgrades). The `upgradeToAndCall` function, restricted to a specific… |

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

_🟠 1 High · 🟡 1 Medium · ⚪ 5 Informational_

### `QA-POWERS` — What the token's controller can do  *(Severity: High · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — pause all transfers. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x3ba5…1274 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 98.7% of supply. What remains: 5.0% in wallets, 93.7% in other contracts. 2,100 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as NaoX Protocol (NAORIS), market cap $18M, rank #877. 2,100 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $136K (DexScreener, all pools). 24h trading volume $841K (CoinGecko, all markets, daily snapshot). 24h trading volume $37K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $136K of DEX liquidity across 1 pools. Launch: 443 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1b37...80cc`](https://etherscan.io/address/0x1b379a79c91a540b2bcd612b4d713f31de1b80cc) |
| **Network** | Ethereum |
| **Price** | $0.03016 |
| **24h Volume** | $37.5K |
| **Liquidity** | $135.6K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 98.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 94 buys / 99 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xc85aa0aeb2458f9f35f0224f773cd90a96ce813c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/naoris-protocol-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-18*
