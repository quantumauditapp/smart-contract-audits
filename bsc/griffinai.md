---
token: GriffinAI
ticker: GAIN
network: bsc
risk_score: 61
status: medium
date: 2026-10-13
---

# GriffinAI (GAIN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 61/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/griffinai-bsc)

---

## Audit Summary

The GainOFT contract is an ERC-20 token with Omnichain Fungible Token (OFT) capabilities, enabling cross-chain transfers via LayerZero. While it implements standard token functionality and robust ownership management, a key finding identifies that specific functions allow for the minting of new tokens by a privileged 'endpoint' address, which could dilute existing token holders.

> **Final Recommendation:** It is crucial to thoroughly understand and secure the `endpoint` address that controls the token minting functions, as its compromise could lead to unauthorized token inflation. Implement robust monitoring for `send`, `lzReceiveSimulate`, and `lzReceive` calls to detect any unusual minting activity. Additionally, ensure that the multisig controlling the contract owner is highly secure and follows best practices for key management and operational security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements the ERC-20 standard and integrates LayerZero's OFT functionality, enabling cross-chain token transfers. Ownership is managed via `Ownable2Step`, enhancing access control for… |
| **Governance / Economics** | 1/10 | High | The contract's ownership is retained and secured by a 3/6 multisig, which is a robust access control mechanism for administrative functions (7.3 Access Control). The owner can configure critical… |
| **Upgrades** | 3/10 | High | The contract is not designed as a proxy and does not include explicit upgradeability mechanisms (7.7 Upgrades). This means the contract's logic is immutable once deployed, providing certainty… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `CP-01` — Privileged Address Can Mint New Tokens  *(Severity: Medium · Status: Unresolved)*

The `send`, `lzReceiveSimulate`, and `lzReceive` functions allow a specific address, referred to as the `endpoint`, to create new tokens. This means that the total supply of GainOFT tokens can be increased by the `endpoint` without explicit approval from token holders. If this `endpoint` is compromised or misused, it could lead to an uncontrolled increase in token supply, diluting the value of existing tokens held by users.

**Recommendation:** Token holders should be aware that the `endpoint` address has the power to mint new tokens. It is critical to understand who controls this `endpoint` and what safeguards are in place to prevent its misuse. The project team should provide clear documentation on the `endpoint`'s role, its security measures, and the circumstances under which new tokens might be minted.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xdf8a…5978 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 93% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 91.9% of supply. Of that, 1.9% burned, 3.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 32.4% in wallets, 54.6% in other contracts. The deployer/owner wallet itself holds 3.0%. 4,997 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Griffin AI (GAIN). 4,997 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $85K (DexScreener, all pools). 24h trading volume $798K (CoinGecko, all markets, daily snapshot). 24h trading volume $364K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.0277 on 2025-10-09; the price is now 90.5357% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 3-of-6 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $85K of DEX liquidity across 3 pools. Launch: 371 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa890...a96f`](https://bscscan.com/address/0xa890f8ba60051ec8a5b528f056da362ba208a96f) |
| **Network** | BNB Chain |
| **Price** | $0.002427 |
| **24h Volume** | $346.6K |
| **Liquidity** | $79.8K |
| **Volume / Liquidity** | 4.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 91.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2523 buys / 2048 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xa39c258cbc35cb243a18ecba38bfb024aeb3c709)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/griffinai-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-13*
