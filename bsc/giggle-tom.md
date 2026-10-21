---
token: Giggle Tom
ticker: TOM
network: bsc
risk_score: 81
status: high
date: 2026-09-03
---

# Giggle Tom (TOM) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 81/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/giggle-tom-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with a complex state-based tax mechanism and an integrated tax liquidation process. The audit identified critical vulnerabilities, including reentrancy and denial-of-service risks stemming from external calls within the transfer function. High-severity issues relate to the immutability of critical parameters and significant centralization risks. Medium-severity findings include the lack of an emergency pause and potential MEV exposure during tax processing. The contract utilizes OpenZeppelin's upgradeable patterns, which is a positive aspect, but the identified critical flaws require immediate attention.

> **Final Recommendation:** Address the critical reentrancy and denial-of-service vulnerabilities immediately by implementing reentrancy guards and robust error handling for external calls. Enhance the contract's flexibility by introducing owner-controlled functions to update critical parameters, ideally with time-locks or multi-signature approvals. Implement an emergency pause mechanism to mitigate risks during unforeseen events. Consider strategies to reduce MEV impact on tax processing and add a function for recovering accidentally sent tokens.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 3/10 | High | The contract leverages OpenZeppelin's upgradeable ERC20 standard and implements a detailed state machine for managing token taxes and migrations (7.1 Architecture). Code quality is generally good… |
| **Governance / Economics** | 3/10 | High | The contract's economic model relies on a state-based tax mechanism and a liquidation process that distributes collected taxes (7.4 Economic). The owner has control over state transitions (7.5… |
| **Upgrades** | 3/10 | High | The contract correctly implements the OpenZeppelin upgradeable pattern, including `Initializable` and `_disableInitializers()` in the constructor (7.7 Upgrades). This allows for future logic updates.… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 2 Critical · 🟠 2 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Reentrancy Vulnerability in `_liquidateTax`  *(Severity: Critical · Status: Unresolved)*

The `_liquidateTax` function, which is called during every `_transfer`, makes external calls to `ITaxProcessor(taxProcessor).processTax` and `IDividend(dividendContract).distribute`. These calls occur before the contract's internal state (e.g., `balanceOf(address(this))`) is fully updated or protected by a reentrancy guard. A malicious `taxProcessor` or `dividendContract` could reenter the `_transfer` or `_liquidateTax` function, potentially leading to double-spending of collected tax funds or manipulation of the contract's state.

**Recommendation:** Implement a reentrancy guard (e.g., OpenZeppelin's `ReentrancyGuard`) on the `_liquidateTax` function. Alternatively, ensure that all state changes related to tax collection and liquidation are completed following the 'checks-effects-interactions' pattern before any external calls are made.


### `C-02` — Denial of Service via External Call Reverts  *(Severity: Critical · Status: Unresolved)*

The `_liquidateTax` function, which is an integral part of the `_transfer` flow, makes external calls to `taxProcessor` and `dividendContract`. If either of these external contracts reverts (e.g., due to an error, intentional malicious behavior, or being paused), all token transfers (`_transfer`) will consequently revert. This effectively halts the entire token's functionality, leading to a complete denial of service for all users.

**Recommendation:** Implement robust error handling for external calls. Consider using a pull-based mechanism for tax distribution where external parties claim funds, rather than pushing funds directly within the critical transfer path. Alternatively, allow the owner to remove or replace a problematic `taxProcessor` or `dividendContract` to prevent a full DoS, possibly by wrapping external calls in `try/catch` blocks if partial failure is acceptable.


### `H-01` — Rigid Critical Parameters  *(Severity: High · Status: Unresolved)*

Numerous critical operational parameters, including `taxProcessor`, `dividendContract`, `v2Router`, `quoteToken`, `liqExpectedOutputAmount`, `antiFarmerDuration`, `buyTaxRate`, `sellTaxRate`, `taxDuration`, and the `pools` mapping, are set exclusively during the `initialize` function and are immutable thereafter. This rigidity prevents the contract from adapting to changing market conditions, security threats, or evolving protocol needs without a full contract upgrade, increasing operational risk.

**Recommendation:** Implement owner-controlled functions to update critical parameters (e.g., `setTaxProcessor`, `setDividendContract`, `setBuyTaxRate`, `setSellTaxRate`, `addPool`, `removePool`). These functions should include appropriate access controls (e.g., `onlyOwner`) and potentially time-locks or multi-signature approvals for sensitive changes to enhance security and flexibility.


### `H-02` — Centralization Risk and Single Point of Failure  *(Severity: High · Status: Unresolved)*

The contract relies heavily on the `owner` for critical state transitions (`startMigration`, `finalizeMigration`). Furthermore, the `taxProcessor` and `dividendContract` are fixed external dependencies. If the owner's private key is compromised, or if the `taxProcessor` or `dividendContract` are malicious or exploited, the system faces a single point of failure that could lead to fund loss, manipulation, or a complete halt of operations.

**Recommendation:** Consider implementing a multi-signature wallet for ownership to reduce the risk of a single point of compromise. For external dependencies, explore mechanisms for owner-controlled updates (as in H-01) and potentially a circuit breaker or emergency pause to mitigate risks from compromised external contracts.


### `M-01` — Lack of Emergency Pause Mechanism  *(Severity: Medium · Status: Unresolved)*

The contract lacks an emergency pause mechanism. In the event of a critical vulnerability, exploit, or unforeseen issue, there is no way for the owner or a governance body to temporarily halt transfers or other critical operations to prevent further damage or allow for a fix.

**Recommendation:** Integrate an emergency pause mechanism (e.g., OpenZeppelin's `PausableUpgradeable` contract). This would allow the owner to pause critical functions like `_transfer` in an emergency, providing time to address issues or prepare for an upgrade.


### `M-02` — MEV Risk in Tax Processing  *(Severity: Medium · Status: Unresolved)*

The `_liquidateTax` function calls `ITaxProcessor(taxProcessor).processTax(taxAmount, liqExpectedOutputAmount, quoteToken, v2Router)`. This likely involves a swap operation on a DEX. Such operations are susceptible to Miner Extractable Value (MEV) attacks, specifically sandwich attacks, where malicious actors can front-run and back-run the transaction to profit at the expense of the protocol, potentially reducing the effective value of the collected tax.

**Recommendation:** While completely eliminating MEV is challenging, consider strategies to mitigate its impact. This could include using a decentralized exchange aggregator that routes through multiple liquidity sources, implementing a minimum output amount check with slippage control, or exploring private transaction relays for sensitive operations.


### `L-01` — Reliance on `block.timestamp` for Critical Logic  *(Severity: Low · Status: Unresolved)*

The `_liquidateTax` function uses `block.timestamp` to determine state transitions (e.g., `taxExpirationTime`, `antiFarmerExpirationTime`). While common, `block.timestamp` can be manipulated by miners within a small window (up to 900 seconds on Ethereum, similar on BSC). This could allow a miner to slightly accelerate or delay a state change to their advantage, though the impact might be limited for expiration times.

**Recommendation:** Be aware of the limitations of `block.timestamp`. For critical, time-sensitive operations where precise timing is crucial and manipulation could lead to significant gains, consider using alternative time sources or mechanisms that are less susceptible to miner manipulation, such as a time oracle or a commit-reveal scheme. For expiration times, the risk is generally lower.


### `I-01` — No Token Recovery Mechanism  *(Severity: Informational · Status: Unresolved)*

The contract does not include a function to recover accidentally sent ERC20 tokens (other than its own token) that might be mistakenly transferred to the contract address. Such tokens would become permanently locked and inaccessible.

**Recommendation:** Implement an `onlyOwner` function to allow the recovery of arbitrary ERC20 tokens sent to the contract address. This function should explicitly exclude the contract's own token to prevent accidental draining.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7b87...7777`](https://bscscan.com/address/0x7b87829a47b835f7be99a74b62d6c04d57847777) |
| **Network** | BNB Chain |
| **Price** | $0.0000218 |
| **24h Volume** | $53.3K |
| **Liquidity** | $14.4K |
| **Volume / Liquidity** | 3.7× |
| **Token Age** | 10h |
| **Top-10 Holders** | 54.6% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 1372 buys / 1013 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xb33db4fd4563ab0573b2bdcf2d8eec9d57fc40d5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/giggle-tom-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-03*
