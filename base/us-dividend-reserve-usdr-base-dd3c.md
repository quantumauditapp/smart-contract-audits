---
token: US Dividend Reserve (USDR)
ticker: USDR
network: base
risk_score: 64
status: medium
date: 2026-10-24
---

# US Dividend Reserve (USDR) (USDR) — Smart Contract Security Analysis | Base

> **Risk Score: 64/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/us-dividend-reserve-usdr-base-dd3c)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with additional governance and vesting features. The architecture relies heavily on a centralized owner role, which possesses significant control over token supply and transferability. While the code follows standard OpenZeppelin patterns, the centralization of power presents a notable risk to token holders.

> **Final Recommendation:** To improve security, consider transitioning the ownership to a decentralized governance contract or a multi-signature wallet with a time-lock mechanism. This would mitigate the risk of a single compromised key unilaterally altering the token's economic parameters or liquidity status.

Additionally, implement event logging for all privileged state changes to ensure transparency for token holders. Providing a clear, public roadmap for the eventual renunciation of administrative powers would further increase trust in the protocol's long-term stability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for ERC-20, Votes, and Permitting functionality. 7.1 Architecture is modular, and 7.2 Code Security is high due to the use of standard… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance risks are elevated due to the owner's ability to mint tokens and halt transfers. The owner can unilaterally dilute holders via updateMintRate or restrict liquidity via… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not implemented as this is a non-proxy contract. 7.8 Operations are straightforward, relying on standard EOA or multisig ownership. No complex upgrade logic exists to introduce… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner can call updateMintRate and release to mint new tokens, which increases the total supply and dilutes existing holders. This function is restricted to the owner, providing them with the ability to unilaterally impact the token's value.

**Recommendation:** Implement a time-lock on minting functions or transition ownership to a DAO to ensure that supply changes are subject to community consensus.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can use lockPool and unlockPool to toggle a switch that determines whether transfers are allowed. This allows the owner to freeze the movement of tokens at their discretion.

**Recommendation:** Remove the ability to halt transfers or implement a multi-signature requirement for such drastic actions to prevent abuse by a single compromised account.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.7% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.1% in other contracts. The deployer/owner wallet itself holds 16.2%. 2,115 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,115 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $47K (DexScreener, all pools). 24h trading volume $116K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Its name presents it as a stable-value coin, yet it trades at $0.004602 — it does not hold a peg. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $47K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc999...60b7`](https://basescan.org/address/0xc999300e98ce93821dd4d53404c9ff1fe2fa60b7) |
| **Network** | Base |
| **Price** | $0.004602 |
| **24h Volume** | $115.6K |
| **Liquidity** | $46.9K |
| **Volume / Liquidity** | 2.5× |
| **Token Age** | 12h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1213 buys / 1206 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x48d730c5fc99a80ecc51747390d30a13e86d8d68302e50abc82dfae93850aad8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/us-dividend-reserve-usdr-base-dd3c)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
