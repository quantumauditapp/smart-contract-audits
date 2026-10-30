---
token: Safu Inu
ticker: SI
network: bsc
risk_score: 44
status: medium
date: 2026-10-30
---

# Safu Inu (SI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 44/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/safu-inu-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is an EIP-1167 minimal clone implementation of an ERC-20 token with custom migration and tax logic. The contract utilizes standard OpenZeppelin upgradeable base contracts for initialization, though the clone pattern itself is immutable. No critical vulnerabilities were identified in the provided logic.

> **Final Recommendation:** The contract is well-structured and follows secure patterns for immutable token deployments. We recommend that the owner address be transitioned to a multi-signature wallet or a decentralized governance contract to mitigate the risks associated with centralized control over migration and tax parameters.

Ensure that all future deployments of this clone follow the same initialization procedures to prevent potential state collision or misconfiguration. No further technical changes are required at this time.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows the EIP-1167 standard, ensuring a lightweight and immutable deployment. 7.1 Architecture and 7.2 Code Security are robust, utilizing well-audited OpenZeppelin libraries for… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic and 7.5 Governance risks are centralized under the contract owner. The owner has the authority to trigger migration states, which directly impacts token transfer behavior and tax… |
| **Upgrades** | 7/10 | Low | 7.7 Upgrades are effectively disabled due to the EIP-1167 minimal clone architecture, which points to a fixed implementation address. While the contract uses Initializable base contracts, these are… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 74.3% of supply. What remains: 15.9% in wallets, 58.4% in other contracts. The deployer/owner wallet itself holds 57.9%. A holder that also controls the contract can sell into its own liquidity. 84 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

84 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $12K (DexScreener, all pools). 24h trading volume $32K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (inu). Tokenomics — Supply: fixed — the contract has no mint function. Control: a role-controlled contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $12K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9e84...7777`](https://bscscan.com/address/0x9e8452c705120488379213bfbb4fc3771e767777) |
| **Network** | BNB Chain |
| **Price** | $0.00000901 |
| **24h Volume** | $31.9K |
| **Liquidity** | $12.5K |
| **Volume / Liquidity** | 2.6× |
| **Token Age** | 7h |
| **Top-10 Holders** | 74.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 302 buys / 206 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ⚠️ Unknown |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x361d892cd684c6bfa32f36d4e1c4af4bfb300cba)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/safu-inu-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
