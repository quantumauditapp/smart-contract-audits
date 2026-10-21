---
token: Pangea Cat
ticker: PCAT
network: ethereum
risk_score: 58
status: medium
date: 2026-10-21
---

# Pangea Cat (PCAT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 58/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pangea-cat-eth)

---

## Audit Summary

The PangeaOFT contract implements an Omnichain Fungible Token (OFT) standard. The architecture relies on LayerZero for cross-chain messaging and includes specific roles for metadata management and supply reporting. While the code follows standard patterns, the ability for privileged roles to influence token supply introduces centralization risks that users should be aware of.

> **Final Recommendation:** The protocol should consider transitioning the supplyReporter and metadataAuthority roles to a multi-signature wallet or a decentralized DAO to mitigate centralization risks. Additionally, implementing a time-lock on sensitive administrative functions would provide transparency and allow the community to react to significant changes in token supply or metadata.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes a robust LayerZero OFT implementation, ensuring standard ERC-20 compatibility and cross-chain interoperability. 7.1 Architecture and 7.2 Code Security are well-structured… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are centralized, as the supplyReporter and metadataAuthority roles hold significant power. While these roles are necessary for the OFT mechanism, they… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not applicable as the contract is not a proxy. 7.8 Operations are handled through clearly defined administrative functions. The lack of upgradeability ensures immutability but limits… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The supplyReporter role has the authority to mint new tokens and adjust the reported supply via the reportSupply function. This allows the controller to dilute the value of existing tokens held by users.

**Recommendation:** Restrict the supplyReporter role to a multi-signature wallet or a time-locked contract to prevent unilateral supply inflation. Ensure that any minting activity is transparently communicated to the community.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x450b…1969 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 75.2% of supply. What remains: 15.3% in wallets, 59.9% in other contracts. 41 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

41 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $12K (DexScreener, all pools). 24h trading volume $67K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (cat). Tokenomics — Supply: mintable with no on-chain cap found. Control: a contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $12K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd102...b6ea`](https://etherscan.io/address/0xd102b5a086687e27e8f5fa0951eda6a7775bb6ea) |
| **Network** | Ethereum |
| **Price** | $0.0000177 |
| **24h Volume** | $67.0K |
| **Liquidity** | $11.6K |
| **Volume / Liquidity** | 5.8× |
| **Token Age** | 6h |
| **Top-10 Holders** | 75.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 308 buys / 238 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x7653a7d45cee016d8e338584488c3290641c848c526e64c4f116008259d8904a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pangea-cat-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
