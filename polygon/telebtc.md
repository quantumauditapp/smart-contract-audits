---
token: teleBTC
ticker: TELEBTC
network: polygon
risk_score: 84
status: high
date: 2026-10-20
---

# teleBTC (TELEBTC) — Smart Contract Security Analysis | Polygon

> **Risk Score: 84/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/telebtc-poly)

---

## Audit Summary

The TeleBTC contract is a centralized token implementation utilizing a Transparent Proxy pattern. The architecture relies heavily on a single owner address with extensive administrative privileges, including the ability to burn user tokens and blacklist addresses. While the code follows standard OpenZeppelin patterns, the centralization of power presents a significant trust requirement for token holders.

> **Final Recommendation:** It is strongly recommended to transition the ownership and proxy administration from an EOA to a multi-signature wallet (e.g., Gnosis Safe) to mitigate the risk of a single compromised key. Additionally, implementing a timelock for sensitive administrative functions would provide transparency and allow users to react to significant changes in protocol rules.

For long-term security, consider decentralizing the minter and burner roles to a governance contract. This would reduce the trust burden on the current owner and align the protocol with industry standards for decentralized assets.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes standard, well-audited libraries like ReentrancyGuard and Ownable. 7.1 Architecture follows the EIP-1967 standard for proxies, ensuring clear separation between logic and… |
| **Governance / Economics** | 1/10 | High | The protocol exhibits high centralization risks regarding 7.3 Access Control and 7.5 Governance. The owner holds absolute authority to modify balances and restrict transfers, which is a significant… |
| **Upgrades** | 1/10 | High | The contract uses a Transparent Proxy pattern, which is a standard and safe approach for 7.7 Upgrades. However, the proxy admin is an EOA, which is a single point of failure for the entire upgrade… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | ⚠️ EOA (single key controls upgrades) |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 4 Informational_

### `CP-02` — Privileged Token Burning  *(Severity: High · Status: Unresolved)*

The ownerBurn function allows the contract owner to directly reduce the balance of any user's wallet. This grants the owner the power to unilaterally seize or destroy tokens held by any participant in the ecosystem.

**Recommendation:** Restrict the use of this function to specific, transparent scenarios or remove it entirely in favor of a user-initiated burn mechanism. If required for regulatory compliance, implement a multi-signature requirement for its execution.


### `CP-06` — Centralized Blacklisting Capability  *(Severity: Medium · Status: Unresolved)*

The owner can add addresses to a blacklist, which prevents those addresses from transferring tokens. This mechanism is controlled entirely by the owner, allowing them to freeze any user's assets at will.

**Recommendation:** Implement a decentralized process for blacklisting, such as a community vote or a multi-signature approval, to prevent the abuse of this power by a single entity.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x1da9…89b0 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 99.7% of supply. What remains: 3.6% in wallets, 96.1% in other contracts. 222 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as teleBTC (TELEBTC). 222 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $199K (DexScreener, all pools). 24h trading volume $1.1M (CoinGecko, all markets, daily snapshot). 24h trading volume $298K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a single wallet (EOA). Code: upgradeable proxy. Fees: no buy or sell tax. Market: $199K of DEX liquidity across 1 pools. Launch: 711 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3bf6...c685`](https://polygonscan.com/address/0x3bf668fe1ec79a84ca8481cead5dbb30d61cc685) |
| **Network** | Polygon |
| **Price** | $81,183.0560 |
| **24h Volume** | $298.2K |
| **Liquidity** | $198.7K |
| **Volume / Liquidity** | 1.5× |
| **Token Age** | 1y |
| **Top-10 Holders** | 99.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 132 buys / 353 sells |

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

- [View on DexScreener](https://dexscreener.com/polygon/0x461751642208dbc4878091e1d94071f0fde7b35e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/telebtc-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
