---
token: Disney (Ondo Tokenized)
ticker: DISON
network: bsc
risk_score: 76
status: high
date: 2026-10-02
---

# Disney (Ondo Tokenized) (DISON) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 76/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/disney-ondo-tokenized-bsc)

---

## Audit Summary

This audit covers the GMToken contract, an ERC-20 token implemented as an upgradeable BeaconProxy on the BSC network. The contract incorporates role-based access control for critical functions such as minting and managing external compliance and pause mechanisms. Two findings were identified, highlighting significant control held by privileged roles over token supply and transfer logic.

> **Final Recommendation:** It is critical to implement robust security measures for all privileged roles, especially the `MINTER_ROLE` and `CONFIGURER_ROLE`. These roles should ideally be controlled by multi-signature wallets with high thresholds or decentralized autonomous organizations (DAOs) to prevent single points of failure and unauthorized actions.

Additionally, establish clear, transparent, and publicly verifiable processes for any changes to critical external contract addresses (`tokenPauseManager`, `compliance`) and for any token minting operations. Regular security reviews and monitoring of these privileged actions are essential to safeguard the integrity and economic stability of the GMToken.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The GMToken contract is built upon established OpenZeppelin upgradeable standards, providing a robust foundation for an ERC-20 token (7.1 Architecture). It includes standard ERC-20 functionalities… |
| **Governance / Economics** | 1/10 | High | The contract employs a role-based access control system, allowing for granular permission management over sensitive operations. This structure provides a clear framework for governance (7.5… |
| **Upgrades** | 1/10 | High | The GMToken contract utilizes the BeaconProxy pattern, enabling future upgrades to its logic without changing the token's address (7.7 Upgrades). This pattern, based on OpenZeppelin's `Initializable`… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 96.9% |
| **Top-3 Unlocked** | ⚠️ 98.9% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 4 Informational_

### `CP-03` — A privileged address can replace a contract every transfer depends on  *(Severity: High · Status: Unresolved)*

Transfers call an external contract whose address a privileged function can change. Whoever controls that setting controls what a transfer does. Functions: setTokenPauseManager, setCompliance. Restricted to: role.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `CP-01` — A privileged address can mint new tokens  *(Severity: Medium · Status: Unresolved)*

A privileged function increases the total supply, diluting every holder. Functions: mint(address,uint256). Restricted to: role.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 99.8% is held, unlocked, by 8 address(es) other than the owner/deployer. One of them — a wallet, 0x8145…0992 — holds 96.9% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 75% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 78.3% of supply. Of that, 19.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 35.9% in wallets, 23.1% in other contracts. 1,294 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Disney (Ondo Tokenized Stock) (DISON), market cap $1M, rank #3041. 1,294 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $67K (DexScreener, all pools). 24h trading volume $211K (CoinGecko, all markets, daily snapshot). 24h trading volume $228K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Tokenized Stocks. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $67K of DEX liquidity across 30 pools. Launch: 60 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xeee9...acfa`](https://bscscan.com/address/0xeee9eee593cb8f7946260b4066cba7907f40acfa) |
| **Network** | BNB Chain |
| **Price** | $102.2000 |
| **24h Volume** | $227.9K |
| **Liquidity** | $50.9K |
| **Volume / Liquidity** | 4.5× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 78.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2013 buys / 2270 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x167c88898537ea7dc756d9b0bf7489a068f0b497)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/disney-ondo-tokenized-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-02*
