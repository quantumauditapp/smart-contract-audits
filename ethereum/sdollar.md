---
token: SDollar
ticker: SDLR
network: ethereum
risk_score: 56
status: medium
date: 2026-11-05
---

# SDollar (SDLR) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 56/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sdollar-eth)

---

## Audit Summary

The TokenContract is a highly centralized ERC-20 implementation featuring advanced administrative controls, including minting, burning, and blacklisting capabilities. While the architecture is robust and utilizes standard security patterns like ReentrancyGuard and AccessControl, the level of control granted to the admin role introduces significant trust requirements for token holders. The contract is not upgradeable, ensuring code immutability, but the administrative functions allow for substantial manipulation of user balances and transfer rules.

> **Final Recommendation:** Token holders should be aware that the administrative role possesses significant power to alter the token's economic properties and individual user access. It is recommended that the project transition to a multi-signature wallet or a decentralized governance model to mitigate the risks associated with a single point of failure.

Furthermore, ensure that all administrative actions are transparently communicated to the community. Consider implementing a timelock mechanism for all sensitive administrative functions to provide users with adequate notice before significant changes to the protocol are enacted.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture (7.1) follows standard OpenZeppelin patterns for access control and token management. Code security (7.2) is high, utilizing ReentrancyGuard and explicit input validation to prevent… |
| **Governance / Economics** | 1/10 | High | Economic (7.4) and Governance (7.5) risks are elevated due to the admin's ability to mint tokens and modify user balances. The protocol relies on a centralized admin for all parameter adjustments… |
| **Upgrades** | 3/10 | High | The contract does not utilize proxy patterns (7.7), ensuring that the logic is immutable once deployed. Operations (7.8) are straightforward, with no complex upgrade paths to manage. This lack of… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 4 Medium · ⚪ 4 Informational_

### `CP-02` — Administrative Control Over User Balances  *(Severity: High · Status: Unresolved)*

The burnAndRedeem function allows a privileged address to burn or move tokens from any user's balance, posing a direct risk to user funds.

**Recommendation:** Remove the ability for the admin to burn or transfer tokens on behalf of users without their explicit, time-bound authorization.


### `CP-01` — Centralized Minting Capability  *(Severity: Medium · Status: Unresolved)*

The mint function allows a privileged address to create new tokens at will, which can dilute the value of existing holdings.

**Recommendation:** Restrict the minting authority to a multi-signature wallet or a decentralized governance contract.


### `CP-06` — Arbitrary Address Blacklisting  *(Severity: Medium · Status: Unresolved)*

The admin can add any address to a blocklist, preventing them from transferring or selling their tokens.

**Recommendation:** Implement a clear, public policy for blacklisting and consider using a timelock for such actions.


### `CP-07` — Dynamic Transfer Fee Manipulation  *(Severity: Medium · Status: Unresolved)*

The admin can change the transfer tax and discount tiers at any time, which directly impacts the economic utility of the token.

**Recommendation:** Set hard caps on transfer taxes and require a governance vote for any changes to the fee structure.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x55b9…0397 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 66.4% of supply. Of that, 48.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 18.4% in wallets, 0.0% in other contracts. 6,188 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

6,188 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $243K (DexScreener, all pools). 24h trading volume $478K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $243K of DEX liquidity across 2 pools. Launch: 97 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0b57...afd6`](https://etherscan.io/address/0x0b57b7333c43fe900d17a81bddc67c88c825afd6) |
| **Network** | Ethereum |
| **Price** | $1.7800 |
| **24h Volume** | $478.1K |
| **Liquidity** | $242.8K |
| **Volume / Liquidity** | 2.0× |
| **Token Age** | 3mo |
| **Top-10 Holders** | 66.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1370 buys / 1168 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x32b16ffa899ac5fd40d798abbafb4ee59de88fb1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sdollar-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
