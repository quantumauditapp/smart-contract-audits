---
token: Roll
ticker: ROLL
network: base
risk_score: 38
status: medium
date: 2026-09-04
---

# Roll (ROLL) — Smart Contract Security Analysis | Base

> **Risk Score: 38/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/roll-base)

---

## Audit Summary

The RollToken contract is a standard ERC20 token with `permit` functionality, inheriting from OpenZeppelin's battle-tested libraries. The primary risk identified is the complete centralization of the token's initial supply to a single treasury address, posing a significant single point of failure. The technical implementation is robust due to the use of audited libraries.

> **Final Recommendation:** It is strongly recommended to implement robust security measures for the `treasury` address, such as a multi-signature wallet (e.g., Gnosis Safe) with a diverse set of signers, to mitigate the high centralization risk associated with holding the entire token supply. Consider the long-term implications of a fixed supply and the absence of a pause mechanism for future operational flexibility.
For `permit` functionality, educate users on best practices to avoid front-running, such as using private transaction relays.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The RollToken contract is a straightforward ERC20 implementation, leveraging OpenZeppelin's robust `ERC20` and `ERC20Permit` libraries (7.1 Architecture). This approach significantly reduces the… |
| **Governance / Economics** | 1/10 | High | The economic model of the RollToken involves minting the entire `MAX_SUPPLY` to a single `treasury` address during deployment (7.4 Economic). This design choice centralizes control over the token's… |
| **Upgrades** | 6/10 | Medium | The RollToken contract is implemented as a standard, non-upgradeable ERC20 token. This design choice eliminates the complexities and potential risks associated with upgrade mechanisms, such as proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 93.8% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Centralized Control of Total Supply  *(Severity: High · Status: Unresolved)*

The `RollToken` contract's constructor mints the entire `MAX_SUPPLY` (1 billion tokens) to a single `treasury` address. This design centralizes control over the entire token supply to one entity (7.3 Access Control, 7.4 Economic). If the `treasury` address is compromised, the entire token supply is at risk of theft or misuse, leading to a complete loss of value for the token holders.

**Recommendation:** Implement robust security measures for the `treasury` address. A multi-signature wallet (e.g., Gnosis Safe) with a diverse set of trusted signers is highly recommended to distribute control and reduce the single point of failure risk. Consider a phased distribution or vesting schedule for the tokens to further decentralize control over time.


### `L-01` — Lack of Emergency Pause Mechanism  *(Severity: Low · Status: Unresolved)*

The `RollToken` contract does not include any mechanism to pause token transfers or other critical functions (7.8 Operations). While a simple ERC20 token may not always require this, in the event of a critical vulnerability discovered in the token itself or a dependent protocol, the inability to pause operations could prevent mitigation of further damage or loss of funds.

**Recommendation:** Consider implementing a pausable mechanism (e.g., inheriting from OpenZeppelin's `Pausable` contract) controlled by a trusted entity (like the multi-sig treasury). This would provide an emergency stop-gap in unforeseen circumstances, allowing time to address critical issues. Clearly define the conditions under which the pause can be activated and deactivated.


### `I-01` — Permit Function Front-Running Risk  *(Severity: Informational · Status: Unresolved)*

The `ERC20Permit` functionality allows for gasless approvals via signed messages. However, if a user's signed `permit` message is broadcast publicly (e.g., on a public mempool), a malicious actor could front-run the legitimate transaction by submitting their own transaction with the same signed message, potentially approving themselves as the `spender` before the intended `spender` (7.2 Code Security, 7.6 External). This is an inherent characteristic of the `permit` design and not a flaw in the implementation.

**Recommendation:** Educate users on the risks associated with public `permit` message broadcasting. Recommend using private transaction relays or services that offer front-running protection when interacting with `permit` functions. Users should be cautious about sharing signed messages in public channels.


### `I-02` — Fixed Token Supply  *(Severity: Informational · Status: Unresolved)*

The `RollToken` contract has a `MAX_SUPPLY` that is entirely minted during deployment, and no further minting or burning capabilities are exposed (7.4 Economic). This results in a fixed and immutable total supply. While this provides predictability, it limits the protocol's flexibility for future economic models, such as introducing inflation/deflation mechanisms, ecosystem incentives, or adjusting supply based on demand.

**Recommendation:** This is a design choice. If future flexibility is desired, consider adding controlled minting/burning functionalities, possibly governed by a multi-signature wallet or a decentralized autonomous organization (DAO). If a fixed supply is the intended design, ensure this is clearly communicated to the community.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xab63...d021`](https://basescan.org/address/0xab6363da0c80cef3ae105bd6241e30872355d021) |
| **Network** | Base |
| **Price** | $0.1292 |
| **24h Volume** | $246.5K |
| **Liquidity** | $1.63M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 7mo |
| **Top-10 Holders** | 95.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4393 buys / 5080 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x0a04e1c94584a6f91228da6c0dba6bf0fbe5c9fa20ec6df57490494994489333)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/roll-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-04*
