---
token: Bitcoin Pepe
ticker: BITPEPE
network: ethereum
risk_score: 84
status: high
date: 2026-10-29
---

# Bitcoin Pepe (BITPEPE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 84/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bitcoin-pepe-eth)

---

## Audit Summary

The contract at the provided address is not verified on the Ethereum block explorer. Consequently, the source code is inaccessible for security analysis. Investors should exercise extreme caution as the lack of transparency prevents verification of ownership, tax mechanisms, or potential backdoors.

> **Final Recommendation:** Do not interact with or invest in this contract until the source code is verified on a block explorer and subjected to a professional security audit. The current state of the contract presents a high probability of malicious intent or total loss of funds.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture: Unknown due to lack of source code. 7.2 Code Security: Cannot be verified; potential for hidden minting or blacklisting functions. 7.3 Access Control: Ownership and administrative… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic: Liquidity is currently unlocked, posing a significant risk of rug-pulls. 7.5 Governance: No public documentation exists regarding tokenomics or governance rights. The lack of verified… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades: The contract is not identified as a proxy, but without source verification, the presence of hidden upgradeability or proxy-like behavior cannot be ruled out. 7.8 Operations: Operational… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 2 High · ⚪ 5 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer, preventing any security analysis or verification of contract logic.

**Recommendation:** Verify the contract source code on the block explorer to allow for public scrutiny and security auditing.


### `H-02` — Unlocked Liquidity  *(Severity: High · Status: Unresolved)*

Liquidity for this token is currently unlocked, which allows the deployer to withdraw all liquidity at any time, leading to a potential rug-pull.

**Recommendation:** Lock the liquidity in a reputable, time-locked smart contract to ensure investor protection.


### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by the token's owner/deployer (0xa0d5…3505) — they can pull that liquidity at any moment. This is the rug-pull path. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 86.0% of supply. Of that, 6.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 79.1% in wallets, 0.0% in other contracts. 203 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

203 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $53K (DexScreener, all pools). 24h trading volume $145K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (pepe). Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $53K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7fae...96a3`](https://etherscan.io/address/0x7fae52142bc5cc81c9d5c61399fe46331ec596a3) |
| **Network** | Ethereum |
| **Price** | $0.0003346 |
| **24h Volume** | $145.4K |
| **Liquidity** | $52.8K |
| **Volume / Liquidity** | 2.8× |
| **Token Age** | 5h |
| **Top-10 Holders** | 86.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 266 buys / 63 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xfc9d572b57dce19141be33ab60a7721fd320ba59)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bitcoin-pepe-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
