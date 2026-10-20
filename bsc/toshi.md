---
token: Toshi
ticker: TOSHI
network: bsc
risk_score: 58
status: medium
date: 2026-10-20
---

# Toshi (TOSHI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 58/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/toshi-bsc)

---

## Audit Summary

The HypERC20 contract is an upgradeable cross-chain token bridge implementation. It utilizes a standard proxy pattern and integrates with an external mailbox system for interchain messaging. While the architecture follows established patterns for cross-chain interoperability, the implementation contains high-severity issues regarding state management and function modifiers that require immediate remediation.

> **Final Recommendation:** Immediate remediation of the high-severity findings is required before further deployment or scaling. Specifically, ensure all functions handling native currency are marked as payable and resolve all state variable shadowing to prevent logic errors.

It is recommended to implement a circuit breaker or pause mechanism that can be triggered by the multisig in the event of a detected anomaly in the cross-chain messaging layer. Regular monitoring of the mailbox and remote router configurations is essential to ensure the integrity of the minting process.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The architecture leverages a robust modular design for cross-chain communication via the Mailbox pattern. 7.1 Architecture is well-structured for scalability, and 7.2 Code Security is generally high… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance risks are centered on the minting capabilities inherent in the bridge mechanism. The ability to mint tokens via the handle function allows for potential supply… |
| **Upgrades** | 1/10 | High | 7.7 Upgrades are managed via a Transparent Proxy pattern with a dedicated ProxyAdmin. This setup is industry-standard and allows for secure, controlled updates to the implementation logic. 7.8… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 3-of-5 |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 72.7% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟡 2 Medium · ⚪ 4 Informational_

### `CD-01` — Missing Payable Modifier  *(Severity: High · Status: Unresolved)*

The _dispatch function is marked as nonpayable but is intended to handle native currency transfers. This will cause transactions to revert if they include a msg.value.

**Recommendation:** Add the 'payable' modifier to the _dispatch function to correctly handle native currency transfers.


### `CD-02` — State Variable Shadowing  *(Severity: High · Status: Unresolved)*

The contract contains instances of state variable shadowing, where local or inherited variables hide state variables of the same name. This can lead to unexpected behavior and logic errors during execution.

**Recommendation:** Rename shadowed variables to ensure clarity and prevent accidental modification of the wrong state variables.


### `CP-01` — Privileged Minting Capability  *(Severity: Medium · Status: Unresolved)*

The functions transferRemote and handle allow for the creation of new tokens. This increases the total supply and dilutes existing holders, which is a significant economic risk if the mailbox or remote router is compromised.

**Recommendation:** Implement strict validation on the origin of minting requests and consider adding a hard cap on the total supply that can be minted via the bridge.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0xc324…5cab — holds 72.7% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 91.0% of supply. Of that, 56.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.9% in wallets, 33.3% in other contracts. 17,733 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Toshi (TOSHI), market cap $45M, rank #493. 17,733 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $399K (DexScreener, all pools). 24h trading volume $2.2M (CoinGecko, all markets, daily snapshot). 24h trading volume $180K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.00226 on 2025-01-26; the price is now 95.2816% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Base Meme. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 3-of-5 multisig. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $399K of DEX liquidity across 3 pools. Launch: 474 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6a26...db3f`](https://bscscan.com/address/0x6a2608dabe09bc1128eec7275b92dfb939d5db3f) |
| **Network** | BNB Chain |
| **Price** | $0.0001179 |
| **24h Volume** | $176.1K |
| **Liquidity** | $393.1K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 1y |
| **Top-10 Holders** | 91.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 751 buys / 731 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x27820f8b2e7c5dbe1eef6805577c222afde1a191)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/toshi-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
