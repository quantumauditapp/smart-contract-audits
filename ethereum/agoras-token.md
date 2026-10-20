---
token: Agoras Token
ticker: AGRS
network: ethereum
risk_score: 72
status: high
date: 2026-10-01
---

# Agoras Token (AGRS) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 72/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/agoras-token-eth)

---

## Audit Summary

The AgorasToken contract is a standard ERC-20 token with additional administrative functionalities. The audit identified two medium-severity issues related to centralized control: the owner can mint new tokens, potentially diluting existing holders, and can pause all token transfers, affecting liquidity and user access. These findings highlight significant control held by the contract owner.

> **Final Recommendation:** It is strongly recommended to review the extent of centralized control within the AgorasToken contract. Consider implementing a multi-signature wallet for the `owner` role to mitigate the risk of a single point of compromise. For critical functions like `mint` and `pause`, explore the possibility of introducing time-locks or community governance mechanisms to provide transparency and allow token holders to react to proposed changes. This would enhance the security and decentralization of the token.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The AgorasToken contract implements standard ERC-20 functionalities (7.1 Architecture) and includes basic access control for administrative functions (7.3 Access Control). The `transfer` and… |
| **Governance / Economics** | 1/10 | High | The contract exhibits a highly centralized governance and economic model (7.5 Governance, 7.4 Economic). The `owner` address holds exclusive power to `mint(uint256)` new tokens, which can dilute the… |
| **Upgrades** | 3/10 | High | The AgorasToken contract is not designed with upgradeability in mind (7.7 Upgrades). This means its logic is immutable once deployed, providing certainty that the contract's behavior will not change… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 31.1% |
| **Top-3 Unlocked** | 70.0% |

## Security Findings

_🟠 1 High · 🟡 3 Medium · ⚪ 3 Informational_

### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 51.8% of supply. What remains: 50.3% in wallets, 1.5% in other contracts. The deployer/owner wallet itself holds 31.4%. A holder that also controls the contract can sell into its own liquidity. 5,499 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `CP-01` — A privileged address can mint new tokens  *(Severity: Medium · Status: Unresolved)*

A privileged function increases the total supply, diluting every holder. Functions: mint(uint256). Restricted to: owner.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `CP-04` — A privileged address can pause transfers  *(Severity: Medium · Status: Unresolved)*

A privileged switch checked on every transfer can stop all transfers. Functions: pause, unpause. Restricted to: owner.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 7 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 88% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Agoras: Tau Net (AGRS), market cap $31M, rank #701. 5,499 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $434K (DexScreener, all pools). 24h trading volume $174K (CoinGecko, all markets, daily snapshot). 24h trading volume $173K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $38.86 on 2020-05-12; the price is now 98.1194% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $434K of DEX liquidity across 3 pools. Launch: 1342 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7388...bdda`](https://etherscan.io/address/0x738865301a9b7dd80dc3666dd48cf034ec42bdda) |
| **Network** | Ethereum |
| **Price** | $0.7574 |
| **24h Volume** | $150.5K |
| **Liquidity** | $380.3K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 3y |
| **Top-10 Holders** | 51.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 127 buys / 93 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xaddd24a001243e6d446ed8d088c82aeff84073a3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/agoras-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-01*
