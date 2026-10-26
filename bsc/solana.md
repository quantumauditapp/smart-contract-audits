---
token: SOLANA
ticker: SOL
network: bsc
risk_score: 8
status: low
date: 2026-08-11
---

# SOLANA (SOL) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 8/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/solana-bsc)

---

## Audit Summary

This audit covers a BEP20 token implementation designed for an upgradeable proxy. The contract utilizes standard OpenZeppelin patterns for upgradeability, safe math, and access control. Key findings include centralized control by an EOA owner, a known ERC-20 allowance race condition, and informational observations regarding event emissions and incomplete source code.

> **Final Recommendation:** It is recommended to consider implementing a multi-signature wallet for the owner and proxy admin roles to mitigate the risks associated with centralized control and single points of failure. Additionally, review the implications of the ERC-20 allowance race condition and ensure users are aware of best practices when interacting with the `approve` function. For future development, ensure all critical state changes and initializations emit corresponding events for enhanced transparency and off-chain monitoring.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The technical architecture (7.1 Architecture) is a standard BEP20 token implementation designed for upgradeability using the Initializable pattern. Code security (7.2 Code Security) is enhanced by… |
| **Governance / Economics** | 9/10 | Low | The economic model (7.4 Economic) allows for optional minting, controlled by a single owner EOA, which introduces significant centralization risk if the `_mintable` flag is true. This centralized… |
| **Upgrades** | 2/10 | High | The contract is designed for upgradeability (7.7 Upgrades) using the `Initializable` pattern, correctly preventing re-initialization. The proxy admin, a single EOA, controls the upgrade process… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | ⚠️ EOA (single key controls upgrades) |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.7% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 8 Informational_

### `M-01` — ERC-20 Allowance Race Condition  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The standard `approve` function is susceptible to a known ERC-20 allowance race condition. If a user approves an amount, and then attempts to change that allowance to a different value, a malicious spender could front-run the second transaction. This allows the spender to spend the original allowance, and then also spend the new allowance, effectively doubling the amount they can spend. While `increaseAllowance` and `decreaseAllowance` mitigate this for changes, the initial `approve` is still vulnerable.

**Recommendation:** Educate users about the risks of the `approve` function and recommend using `increaseAllowance` and `decreaseAllowance` when modifying existing allowances. For initial approvals, users should be cautious and verify transactions. While this is a standard ERC-20 behavior, awareness is key.


### `I-01` — Missing Event for `initialize` Parameters  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initialize` function sets critical parameters such as `name`, `symbol`, `decimals`, `initial amount`, `mintable` status, and `owner`. However, it does not emit an event to log these initial configurations on-chain. This makes it harder for off-chain systems, block explorers, and monitoring tools to reliably track the token's initial setup and verify its properties without parsing transaction input data.

**Recommendation:** Emit an event within the `initialize` function that logs all the significant parameters set during the contract's initial setup. For example, `event Initialized(string name, string symbol, uint8 decimals, uint256 initialSupply, bool mintable, address owner);`


### `I-02` — Incomplete `_burnFrom` Function in Provided Source  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The provided source code for the internal `_burnFrom` function is truncated, ending with `_allowances[account][_msgSender()].sub(am...`. This prevents a full security review of its logic. While it is an internal function, its complete implementation is necessary to ensure no vulnerabilities exist within its scope, especially concerning allowance management.

**Recommendation:** Ensure that the complete and verified source code for all functions, including internal ones, is available for a comprehensive security audit. This allows for a thorough review of all code paths and logic.


### `I-03` — Centralized Control by EOA Owner  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract's `_owner` is a single External Owned Account (EOA) that has significant control over the token. This includes the ability to mint new tokens (if `_mintable` is true), transfer ownership, and renounce ownership. Furthermore, the proxy's admin, also an EOA, controls contract upgrades. This centralization introduces a single point of failure, where compromise of this EOA could lead to unauthorized minting, malicious upgrades, or loss of control over the token.

**Recommendation:** Consider migrating the `_owner` and proxy admin roles to a multi-signature wallet (e.g., Gnosis Safe) to distribute control and reduce the risk associated with a single point of compromise. This enhances security by requiring multiple approvals for critical operations.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 62.6% of supply. What remains: 61.6% in wallets, 1.1% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Binance-Peg SOL (SOL), market cap $112M. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $3.6M (DexScreener, all pools). 24h trading volume $1.7M (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Binance-Peg Tokens. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $3.6M of DEX liquidity across 30 pools. Launch: 974 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x570a...43df`](https://bscscan.com/address/0x570a5d26f7765ecb712c0924e4de545b89fd43df) |
| **Network** | BNB Chain |
| **Price** | $103.9000 |
| **24h Volume** | $1.69M |
| **Liquidity** | $1.30M |
| **Volume / Liquidity** | 1.3× |
| **Token Age** | 2y |
| **Top-10 Holders** | 62.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1147 buys / 1275 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xbffec96e8f3b5058b1817c14e4380758fada01ef)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/solana-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
