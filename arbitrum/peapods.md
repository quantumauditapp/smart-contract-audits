---
token: Peapods
ticker: PEAS
network: arbitrum
risk_score: 73
status: high
date: 2026-11-05
---

# Peapods (PEAS) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 73/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/peapods-arb)

---

## Audit Summary

The protocol implements a standard ERC-20 token with bridging capabilities and a centralized minting mechanism. The codebase follows established OpenZeppelin patterns, ensuring robust standard compliance. The primary risk is the centralized control over token supply, which is managed by a multisig wallet.

> **Final Recommendation:** The protocol should implement a timelock contract for the minter role to provide transparency and a delay period for any supply changes. Additionally, consider documenting the off-chain criteria used by the multisig signers to authorize minting events to increase community trust.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture utilizes standard OpenZeppelin libraries for ERC-20 and EIP-712 compliance, ensuring 7.1 Architecture and 7.2 Code Security standards are met. 7.3 Access Control is implemented via… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance risks are centered on the minting authority. While the multisig requirement (2/6) provides a layer of protection, the ability to mint tokens creates potential for… |
| **Upgrades** | 3/10 | High | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are handled via standard ownership transfers. The lack of upgradeability ensures immutability but prevents rapid patching… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.6% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 4 Informational_

### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 99.6% is held, unlocked, by the token's owner/deployer (0xc64b…362b) — they can pull that liquidity at any moment. This is the rug-pull path. 0.4% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The mint(address,uint256) function allows a privileged minter address to create new tokens at will. This increases the total supply and dilutes the value held by existing token holders.

**Recommendation:** Implement a timelock on the minter role or require a multi-step governance process before new tokens can be minted to prevent unauthorized or sudden supply inflation.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 70.3% of supply. Of that, 15.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 39.5% in wallets, 14.9% in other contracts. The deployer/owner wallet itself holds 3.6%. 1,066 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Peapods Finance (PEAS), market cap $18M, rank #904. 1,066 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $146K (DexScreener, all pools). 24h trading volume $104K (CoinGecko, all markets, daily snapshot). 24h trading volume $59K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 2-of-6 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $146K of DEX liquidity across 7 pools. Launch: 964 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x02f9...f875`](https://arbiscan.io/address/0x02f92800f57bcd74066f5709f1daa1a4302df875) |
| **Network** | Arbitrum |
| **Price** | $1.1100 |
| **24h Volume** | $59.0K |
| **Liquidity** | $140.7K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 2y |
| **Top-10 Holders** | 70.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 159 buys / 95 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0x23d17764f41aea93fdbb5beffa83571f0bf3f8b2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/peapods-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
