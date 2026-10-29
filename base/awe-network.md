---
token: AWE Network
ticker: AWE
network: base
risk_score: 48
status: medium
date: 2026-10-29
---

# AWE Network (AWE) — Smart Contract Security Analysis | Base

> **Risk Score: 48/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/awe-network-base)

---

## Audit Summary

The AWE token is a standard ERC-20 implementation utilizing OpenZeppelin's UUPS upgradeable pattern. The contract includes governance features such as ERC-20 Votes and Permit. Analysis confirms that the transfer logic is standard and free from backdoors or unauthorized modification capabilities. No critical vulnerabilities were identified in the provided source code.

> **Final Recommendation:** Maintain the current security posture by ensuring that the private keys associated with the administrative roles are stored in a multi-signature wallet or a hardware security module. Regularly monitor the implementation contract for any unauthorized changes to the upgrade logic.

Continue to follow OpenZeppelin's best practices for upgradeable contracts. Ensure that any future changes to the contract logic undergo a thorough peer review and testing process before deployment to the mainnet.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows industry-standard OpenZeppelin upgradeable patterns, ensuring modularity and security. 7.1 Architecture is sound, utilizing UUPS for gas-efficient upgrades. 7.2 Code Security… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance aspects are handled via standard ERC-20Votes, allowing for decentralized decision-making. The tokenomics are standard, with no hidden minting or burning mechanisms… |
| **Upgrades** | 1/10 | High | 7.7 Upgrades are managed through the UUPS pattern, which is the current industry standard for proxy security. 7.8 Operations are protected by role-based access control, ensuring that only authorized… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 56.3% |
| **Top-3 Unlocked** | ⚠️ 99.5% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 4 address(es) other than the owner/deployer. One of them — a wallet, 0x375f…9491 — holds 56.3% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 69.8% of supply. Of that, 2.9% burned — not holders that can sell, so excluded from the concentration score. What remains: 60.2% in wallets, 6.7% in other contracts. 12,662 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as AWE Network (AWE), market cap $131M, rank #230. Traded on Coinbase. 12,662 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $408K (DexScreener, all pools). 24h trading volume $4.3M (CoinGecko, all markets, daily snapshot). 24h trading volume $40K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: vote delegation in its code. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $408K of DEX liquidity across 1 pools. Launch: 526 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1b46...2778`](https://basescan.org/address/0x1b4617734c43f6159f3a70b7e06d883647512778) |
| **Network** | Base |
| **Price** | $0.06918 |
| **24h Volume** | $39.7K |
| **Liquidity** | $408.1K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 69.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 251 buys / 236 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xcb7f520d18141e36956fe0b3a6bc3d4f11245521)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/awe-network-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
