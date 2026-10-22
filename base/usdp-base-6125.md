---
token: USDP
ticker: USDP
network: base
risk_score: 75
status: high
date: 2026-10-22
---

# USDP (USDP) — Smart Contract Security Analysis | Base

> **Risk Score: 75/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/usdp-base-6125)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with additional governance, voting, and vesting capabilities. The protocol relies on a centralized owner to manage inflation rates and pool access. While the code follows established OpenZeppelin standards, the high degree of administrative control over token supply and transferability presents a significant centralization risk to token holders.

> **Final Recommendation:** To improve security, the project should transition administrative functions to a multi-signature wallet or a decentralized governance contract. Implementing a timelock on sensitive functions like updateMintRate would provide transparency and allow the community to react to supply changes.

Furthermore, consider documenting the specific conditions under which the pool is locked or unlocked. Providing clear, on-chain or off-chain transparency regarding the owner's intent for these functions will help build trust with token holders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract utilizes standard OpenZeppelin libraries for ERC-20, EIP-712, and Votes, ensuring 7.1 Architecture and 7.2 Code Security compliance. 7.3 Access Control is implemented via Ownable, though… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized under the contract owner. The owner has the ability to mint tokens and halt pool transfers, which directly impacts 7.4 Economic… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are straightforward, relying on the owner to trigger minting and vesting releases. No complex upgrade paths exist to… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner can call updateMintRate and release to mint new tokens, which increases the total supply and dilutes the value of existing holdings. This allows the owner to unilaterally change the tokenomics of the protocol.

**Recommendation:** Implement a timelock for supply-changing functions or transition ownership to a DAO-governed contract to prevent arbitrary inflation.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can use lockPool and unlockPool to toggle a switch that determines whether transfers are permitted. This gives the owner the power to freeze user assets or restrict liquidity at will.

**Recommendation:** Remove the ability to arbitrarily lock transfers or restrict this functionality to a decentralized governance vote with a mandatory notice period.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 2,064 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,064 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $190K (DexScreener, all pools). 24h trading volume $296K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Its name presents it as a stable-value coin, yet it trades at $0.3867 — it does not hold a peg. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $190K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9c1e...3c7e`](https://basescan.org/address/0x9c1e03eeda5782e49c75140fd5d8e322ae683c7e) |
| **Network** | Base |
| **Price** | $0.3867 |
| **24h Volume** | $296.2K |
| **Liquidity** | $190.4K |
| **Volume / Liquidity** | 1.6× |
| **Token Age** | 14h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1478 buys / 1410 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xb486b098f578696538fefdecab4766b463a25ffc64165a34cddff87704f56756)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/usdp-base-6125)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
