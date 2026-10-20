---
token: ORBOFI
ticker: OBI
network: bsc
risk_score: 65
status: high
date: 2026-10-14
---

# ORBOFI (OBI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 65/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/orbofi-bsc)

---

## Audit Summary

The BridgeMintableTokenV2 contract is an upgradeable ERC-20 token with significant centralized control. Key functionalities such as token minting, burning, pausing transfers, and blocking individual addresses are controlled by a set of privileged addresses. This concentration of power introduces substantial technical and economic risks, as these controllers can unilaterally affect the token supply, individual balances, and overall transferability.

> **Final Recommendation:** Token holders should be aware of the high degree of centralized control over the token's core functionalities, including supply management and transfer restrictions. It is crucial to understand the governance mechanisms and security practices surrounding the privileged addresses (`chainportbridge`, `chainportcongress`, `classifiedauthority`) that control these critical operations. Consider implementing multi-signature wallets or time-locks for sensitive administrative actions to enhance security and decentralization. Additionally, a clear process for upgrading the contract should be documented and transparently communicated to the community.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The BridgeMintableTokenV2 is an upgradeable ERC-20 token (7.1 Architecture). It includes standard ERC-20 functionalities alongside several privileged operations. The contract implements pausing… |
| **Governance / Economics** | 1/10 | High | The economic stability and governance of the token are heavily dependent on the integrity of the privileged addresses. The ability to `mint` new tokens (CP-01) allows for arbitrary supply inflation… |
| **Upgrades** | 1/10 | High | The token utilizes a Transparent Upgradeable Proxy pattern, allowing the underlying implementation logic to be changed (7.1 Architecture). The `BridgeMintableTokenV2` contract is the current… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Other-Contract |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 5 Medium · ⚪ 3 Informational_

### `CP-02` — Controller Can Burn Tokens from Any Holder's Wallet  *(Severity: High · Status: Unresolved)*

The `destroyBlackFunds` function grants the `chainportcongress` controller the power to remove (burn) tokens from any address. This means the `chainportcongress` can unilaterally reduce the balance of any token holder, effectively seizing their tokens.

**Recommendation:** This function represents a significant centralization risk. Token holders must understand that their token balances are subject to direct modification by the `chainportcongress` controller. Transparency and strong governance around the use of this function are critical.


### `CP-01` — Centralized Minting Authority Can Dilute Token Supply  *(Severity: Medium · Status: Unresolved)*

The `mint` function allows specific controllers, namely `chainportbridge`, `chainportcongress`, and `classifiedauthority`, to create new tokens at any time. This means these controllers can increase the total supply of tokens, which could reduce the value of existing tokens held by others.

**Recommendation:** Token holders should be aware that the token supply is not fixed and can be increased by the designated controllers. It is important to trust these entities to manage the supply responsibly and transparently.


### `CP-04` — Controllers Can Halt All Token Transfers  *(Severity: Medium · Status: Unresolved)*

The `pause` function allows `chainportbridge`, `chainportcongress`, and `classifiedauthority` controllers to stop all token transfers on the network. If the token is paused, no one, including regular token holders, can send or receive tokens until one of the controllers uses the `unpause` function (specifically `chainportcongress`) to resume transfers.

**Recommendation:** Token holders should be aware that their ability to transfer tokens can be temporarily suspended by the designated controllers. This feature is often used in emergencies but represents a centralized point of control over liquidity.


### `CP-06` — Controllers Can Block Specific Token Holders  *(Severity: Medium · Status: Unresolved)*

The `blockAddress` function allows `chainportbridge`, `chainportcongress`, and `classifiedauthority` controllers to prevent specific addresses from transferring or receiving tokens. This means these controllers can selectively freeze individual token holders' ability to move their assets, while others can still transact. The `chainportcongress` can `unblockAddress`.

**Recommendation:** Token holders should understand that their address can be individually blocked from participating in token transfers by the designated controllers. This power could be used for regulatory compliance or to mitigate malicious activity, but it also introduces a risk of censorship.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x6d6f…1c1b — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $67K (DexScreener, all pools). 24h trading volume $1.5M (CoinGecko, all markets, daily snapshot). 24h trading volume $1.8M (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.0848 on 2023-05-29; the price is now 99.0863% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 61.4% of supply. Of that, 3.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 44.0% in wallets, 14.1% in other contracts. 8,049 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Orbofi AI (OBI), market cap $1M, rank #2846. 8,049 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $67K of DEX liquidity across 4 pools. Launch: 1233 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x69a8...d93f`](https://bscscan.com/address/0x69a87c8788d4a48c1362b3b357d0e6b59c11d93f) |
| **Network** | BNB Chain |
| **Price** | $0.00118 |
| **24h Volume** | $576.8K |
| **Liquidity** | $63.4K |
| **Volume / Liquidity** | 9.1× |
| **Token Age** | 3y |
| **Top-10 Holders** | 61.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2930 buys / 2466 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x4b85749cdb12edb26bbf8bc80016ff354fe7da74)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/orbofi-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-14*
