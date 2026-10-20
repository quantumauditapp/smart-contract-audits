---
token: IMO
ticker: IMO
network: base
risk_score: 51
status: medium
date: 2026-10-15
---

# IMO (IMO) — Smart Contract Security Analysis | Base

> **Risk Score: 51/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/imo-base)

---

## Audit Summary

The IMO contract is an ERC-20 token with LayerZero OFT functionality, enabling cross-chain transfers. It is owned by an EOA. The audit identified a medium-severity issue related to token minting, where privileged addresses can increase the total supply, potentially diluting existing token holders. All fields are filled based on the provided information.

> **Final Recommendation:** It is recommended to carefully manage the LayerZero `endpoint` address, as it holds the power to mint new tokens. Implement robust operational security practices for this address to prevent unauthorized token inflation. Consider implementing a multi-signature wallet for the `endpoint` or owner roles to enhance security and decentralize control over critical functions, reducing single points of failure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The IMO contract implements ERC-20 standards and integrates LayerZero OFT for cross-chain token transfers (7.1 Architecture). Core ERC-20 functions like `transfer` and `balanceOf` are present.… |
| **Governance / Economics** | 1/10 | High | The contract's ownership is retained by an External Owned Account (EOA), granting the owner significant control over administrative functions such as `setMsgInspector`, `setEnforcedOptions`, and… |
| **Upgrades** | 2/10 | High | The IMO contract is not deployed as a proxy and therefore does not support upgradeability (7.7 Upgrades). This eliminates risks associated with upgrade mechanisms, such as proxy misconfigurations or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 80.7% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `CP-01` — Privileged Address Can Mint New Tokens  *(Severity: Medium · Status: Unresolved)*

The IMO token contract allows a specific privileged address, identified as the LayerZero `endpoint`, to create new tokens. This can happen through the `send`, `lzReceiveSimulate`, and `lzReceive` functions. If this `endpoint` address is compromised or misused, it could lead to an uncontrolled increase in the total supply of IMO tokens.

**Recommendation:** Token holders should be aware that the LayerZero `endpoint` has the power to mint new tokens, which could dilute the value of their holdings. It is crucial for the project team to secure the `endpoint` address with the highest level of operational security, such as a multi-signature wallet, to prevent unauthorized minting and protect the token's economic stability.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a contract, 0xd537…9ce7 — holds 80.7% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 51.1% of supply. Of that, 14.0% locked, 4.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 33.1% in wallets, 0.0% in other contracts. 71,511 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as IMO (IMO), market cap $6M, rank #1495. 71,511 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $294K (DexScreener, all pools). 24h trading volume $103K (CoinGecko, all markets, daily snapshot). 24h trading volume $120K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $294K of DEX liquidity across 8 pools. Launch: 727 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5a7a...e1bb`](https://basescan.org/address/0x5a7a2bf9ffae199f088b25837dcd7e115cf8e1bb) |
| **Network** | Base |
| **Price** | $0.4303 |
| **24h Volume** | $117.2K |
| **Liquidity** | $293.0K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 2y |
| **Top-10 Holders** | 51.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 236 buys / 354 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xd8bca82c613026b7141bc4e5826e7c910f082f39)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/imo-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-15*
