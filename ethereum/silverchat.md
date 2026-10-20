---
token: ‎ Silvercha‎t
ticker: SC
network: ethereum
risk_score: 27
status: low
date: 2026-10-02
---

# ‎ Silvercha‎t (SC) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 27/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/silverchat-eth)

---

## Audit Summary

The LaunchToken contract is a standard ERC-20 token implementation. Static analysis indicates no privileged functions or custom logic that could introduce central points of control or complex vulnerabilities. The contract adheres closely to the ERC-20 standard, suggesting a low-risk profile.

> **Final Recommendation:** Ensure the initial token supply and distribution are correctly configured during deployment, as these parameters are immutable post-deployment. Given the contract's simplicity and adherence to the ERC-20 standard, focus on external factors such as liquidity provision and user education regarding token interactions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract implements the ERC-20 standard with no additional complex logic or privileged functions, which significantly reduces the attack surface (7.2 Code Security). All standard ERC-20 functions… |
| **Governance / Economics** | 2/10 | High | The contract exhibits a highly decentralized economic model as there are no privileged functions that can alter transfer conditions or token supply beyond standard ERC-20 mechanisms (7.4 Economic).… |
| **Upgrades** | 8/10 | Low | The contract is not implemented as a proxy and therefore is not upgradeable (7.7 Upgrades). This eliminates risks associated with upgrade mechanisms, such as proxy misconfigurations or malicious… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 84.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a contract, 0xa52c…5ebb — holds 84.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 46.4% of supply. Of that, 4.3% burned — not holders that can sell, so excluded from the concentration score. What remains: 8.3% in wallets, 33.8% in other contracts. The deployer/owner wallet itself holds 5.2%. 326 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as SilverChat (SC). 326 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $95K (DexScreener, all pools). 24h trading volume $303K (CoinGecko, all markets, daily snapshot). 24h trading volume $564K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $95K of DEX liquidity across 7 pools. Launch: 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3c39...2353`](https://etherscan.io/address/0x3c3959052f60cbddc498b384958841b718112353) |
| **Network** | Ethereum |
| **Price** | $0.0003991 |
| **24h Volume** | $561.1K |
| **Liquidity** | $91.0K |
| **Volume / Liquidity** | 6.2× |
| **Token Age** | 1d |
| **Top-10 Holders** | 46.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1021 buys / 689 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x78d26149b51247240c317cb9bc2a7c786d3d6edc7f9e259aabedf6be9f081e86)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/silverchat-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-02*
