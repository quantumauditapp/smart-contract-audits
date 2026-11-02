---
token: MOVN
ticker: MOVN
network: bsc
risk_score: 78
status: high
date: 2026-11-02
---

# MOVN (MOVN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 78/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/movn-bsc)

---

## Audit Summary

The MOVN token is a standard ERC-20 implementation with added administrative controls for pausing, blacklisting, and minting. While the code follows standard OpenZeppelin patterns, the centralized control over token supply and transferability introduces significant trust requirements for holders. 7.1 Architecture: Standard ERC-20 with administrative extensions. 7.2 Code Security: Implementation is clean and follows best practices. 7.3 Access Control: Centralized via Owner and Manager roles. 7.4 Economic: Inflationary risk exists due to minting capabilities. 7.5 Governance: Controlled by a 2/3 multisig. 7.6 External: No external dependencies. 7.7 Upgrades: Not upgradeable. 7.8 Operations: Manager role allows for emergency pausing and blacklisting.

> **Final Recommendation:** The protocol should consider implementing a timelock for sensitive administrative actions like minting to provide transparency to the community. Additionally, clear documentation regarding the criteria for blacklisting addresses should be published to maintain trust with token holders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes standard OpenZeppelin libraries for ERC-20 and Pausable functionality. The code is modular and readable, with clear separation between standard token logic and administrative… |
| **Governance / Economics** | 1/10 | High | The protocol relies on a 2/3 multisig wallet to manage sensitive functions, providing a layer of protection against single-key compromise. However, the ability to mint tokens and blacklist addresses… |
| **Upgrades** | 4/10 | Medium | The contract is not upgradeable, meaning the logic is immutable once deployed. This eliminates risks associated with proxy implementation errors or malicious logic updates. The current state is fixed… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 5 Medium · ⚪ 2 Informational_

### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 3.3% in wallets, 96.7% in other contracts. The deployer/owner wallet itself holds 96.5%. A holder that also controls the contract can sell into its own liquidity. 19,983 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The owner can call the mint function to increase the total supply of tokens, which can dilute the value of existing holdings.

**Recommendation:** Implement a timelock or a hard cap on total supply to limit the impact of potential administrative abuse.


### `CP-04` — Emergency Pause Capability  *(Severity: Medium · Status: Unresolved)*

The manager can pause all token transfers, effectively freezing the market for all users during an emergency or at their discretion.

**Recommendation:** Restrict the pause functionality to specific emergency scenarios and provide clear communication to users when active.


### `CP-06` — Address Blacklisting  *(Severity: Medium · Status: Unresolved)*

The manager can add specific addresses to a blacklist, preventing those holders from transferring or selling their tokens.

**Recommendation:** Limit the use of blacklisting to regulatory compliance requirements only and ensure the process is transparent.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x46c9…4373 — holds 99.9% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $45K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

19,983 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 2-of-3 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $9K of DEX liquidity across 2 pools. Launch: 101 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x200b...0274`](https://bscscan.com/address/0x200b63aa750c901892d4dcf82439860f9c270274) |
| **Network** | BNB Chain |
| **Price** | $0.9742 |
| **24h Volume** | $45.0K |
| **Liquidity** | $8.5K |
| **Volume / Liquidity** | 5.3× |
| **Token Age** | 3mo |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 453 buys / 79 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x9fd3e51ef5c954b5fb5bd81d71a227bcbd02a40b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/movn-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
