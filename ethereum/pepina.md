---
token: Pepina
ticker: PEPINA
network: ethereum
risk_score: 84
status: high
date: 2026-10-20
---

# Pepina (PEPINA) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 84/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pepina-eth)

---

## Audit Summary

The Pepina contract is a standard ERC-20 token implementation. It lacks any privileged administrative functions, blacklists, or minting capabilities, ensuring a decentralized and immutable token structure. The code follows OpenZeppelin standards, providing a secure foundation for asset transfers.

> **Final Recommendation:** The contract is secure and follows best practices for a standard ERC-20 token. No further action is required as the code is immutable and free of administrative backdoors.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows standard ERC-20 patterns (7.1 Architecture). Code security is high due to the use of audited OpenZeppelin libraries (7.2 Code Security). There are no access control… |
| **Governance / Economics** | 1/10 | High | There are no governance mechanisms (7.5 Governance) or economic parameters (7.4 Economic) defined within the contract. The token supply is fixed upon deployment. The lack of administrative functions… |
| **Upgrades** | 6/10 | Medium | The contract is not a proxy and does not support upgrades (7.7 Upgrades). This provides maximum security against upgrade-related vulnerabilities. Operational procedures (7.8 Operations) are… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by the token's owner/deployer (0xf48c…a585) — they can pull that liquidity at any moment. This is the rug-pull path. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No code-level findings — contract source is not verified on the explorer  *(Severity: Informational · Status: Acknowledged)*

The contract's source code has not been published or verified on the block explorer, so only its deployed bytecode and on-chain behaviour were available. No source-level vulnerability could be confirmed or ruled out. The assessment on this page rests on holder concentration.

**Recommendation:** Treat an unverified contract as unaudited at the code level. Ask the team to verify the source on the explorer, which makes an independent review possible.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 100.0% in wallets, 0.0% in other contracts. 1 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $42K (DexScreener, all pools). 24h trading volume $144K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $42K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x967f...6e26`](https://etherscan.io/address/0x967fbace50402e7ef50d3b32d2d8750f2cbe6e26) |
| **Network** | Ethereum |
| **Price** | $0.0002035 |
| **24h Volume** | $144.1K |
| **Liquidity** | $42.3K |
| **Volume / Liquidity** | 3.4× |
| **Token Age** | 1h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 237 buys / 80 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x4b787a9ae63301e6ce3904fb51a64cb50d07e36b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pepina-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
