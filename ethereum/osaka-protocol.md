---
token: Osaka Protocol
ticker: OSAK
network: ethereum
risk_score: 35
status: medium
date: 2026-10-09
---

# Osaka Protocol (OSAK) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 35/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/osaka-protocol-eth)

---

## Audit Summary

The audit of the TokenMintERC20Token contract found it to be a standard ERC-20 implementation without any identified critical, high, or medium severity vulnerabilities. The contract lacks privileged functions, indicating no central control over token operations beyond standard ERC-20 mechanics. All standard ERC-20 functionalities are present and appear to be implemented correctly.

> **Final Recommendation:** Given the contract's non-upgradeable nature and lack of privileged functions, its security posture is largely determined by the robustness of the underlying ERC-20 standard implementation. Token holders should be aware that the contract's logic is fixed and cannot be changed post-deployment.
For future deployments, consider using the latest stable Solidity compiler versions and battle-tested libraries like OpenZeppelin for standard implementations. Ensure thorough testing of any custom logic, even in seemingly simple token contracts, to prevent unexpected behavior.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The TokenMintERC20Token contract implements the ERC-20 standard, providing essential token functionalities such as `transfer` and `balanceOf`. The code analysis (7.2 Code Security) reveals no custom… |
| **Governance / Economics** | 5/10 | Medium | The contract exhibits a decentralized economic model (7.4 Economic) as it lacks any privileged functions for minting, burning, pausing, or blacklisting. This means no single entity can unilaterally… |
| **Upgrades** | 8/10 | Low | The TokenMintERC20Token contract is not designed as a proxy (7.7 Upgrades) and is therefore not upgradeable. This immutability provides a high degree of certainty regarding its long-term behavior, as… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.5% |
| **Top-3 Unlocked** | ⚠️ 99.9% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0xb8f2…fa08 — holds 99.5% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 78% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 80.3% of supply. Of that, 23.9% burned, 1.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 52.4% in wallets, 2.1% in other contracts. 12,762 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Osaka Protocol (OSAK), market cap $17M, rank #945. 12,762 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $794K (DexScreener, all pools). 24h trading volume $138K (CoinGecko, all markets, daily snapshot). 24h trading volume $34K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $4.38e-07 on 2024-03-06; the price is now 94.8774% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $794K of DEX liquidity across 5 pools. Launch: 1264 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa21a...6b5c`](https://etherscan.io/address/0xa21af1050f7b26e0cff45ee51548254c41ed6b5c) |
| **Network** | Ethereum |
| **Price** | $0.00000002 |
| **24h Volume** | $34.2K |
| **Liquidity** | $620.9K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 3y |
| **Top-10 Holders** | 80.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 75 buys / 28 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x05c024b441d2c288c2729b484bd4bcef3596aa51)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/osaka-protocol-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-09*
