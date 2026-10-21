---
token: SpaceX Inu
ticker: SI
network: bsc
risk_score: 19
status: low
date: 2026-10-21
---

# SpaceX Inu (SI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 19/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/spacex-inu-bsc)

---

## Audit Summary

SpaceXInu is a standard ERC-20 token with additional fee and swap mechanics. The contract ownership has been renounced, effectively locking the administrative functions that previously allowed for the modification of fee exemptions and swap thresholds. However, a specific marketing address retains the ability to withdraw stuck BNB and rescue tokens from the contract, which represents a centralized point of control.

> **Final Recommendation:** The protocol is currently in a stable, immutable state regarding its core tokenomics due to the renouncement of ownership. Users should be aware that the marketing address still holds the power to withdraw any BNB or foreign tokens sent to the contract address.

No further action is required for the core token logic. Future interactions should focus on monitoring the marketing address for any unexpected movement of funds, as this remains the only active privileged role.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract implements standard ERC-20 functionality with 7.1 Architecture following common token patterns. 7.2 Code Security is maintained through the use of OpenZeppelin-like patterns and standard… |
| **Governance / Economics** | 2/10 | High | 7.5 Governance is non-existent as ownership is renounced, preventing any future parameter updates. 7.4 Economic risk is minimized because the swap thresholds are now immutable. The marketing address… |
| **Upgrades** | 8/10 | Low | The contract is not upgradeable (7.7 Upgrades). There are no proxy patterns or delegatecall mechanisms present. The logic is fixed at deployment. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x1e78…7140 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-08` — Immutable Transfer and Fee Configuration  *(Severity: Informational · Status: Unresolved)*

The functions updateSwapTokensAmt, setExemptFromFee, and others allowed the owner to modify tokenomics. Because ownership has been renounced, these functions are now permanently disabled and cannot be called by anyone.

**Recommendation:** No action required as the renouncement is a security feature that prevents future unauthorized changes to the token's economic rules.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 20.8% of supply. Of that, 1.2% burned, 12.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 5.8% in wallets, 1.1% in other contracts. 761 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

761 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $77K (DexScreener, all pools). 24h trading volume $508K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (inu). Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3% on buy, 3% on sell. Market: $77K of DEX liquidity across 1 pools. Launch: 3 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x725c...6666`](https://bscscan.com/address/0x725ccc7b5ceacb0324b64ccb7da3eca2cd3a6666) |
| **Network** | BNB Chain |
| **Price** | $0. |
| **24h Volume** | $508.0K |
| **Liquidity** | $77.0K |
| **Volume / Liquidity** | 6.6× |
| **Token Age** | 3d |
| **Top-10 Holders** | 20.8% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 2103 buys / 807 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x5a606e1533fb11870f3b6c2f98a7edda699b94bf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/spacex-inu-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
