---
token: Nola
ticker: NOLA
network: arbitrum
risk_score: 60
status: medium
date: 2026-09-01
---

# Nola (NOLA) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 60/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/nola-arb)

---

## Audit Summary

The OdysToken contract implements a standard ERC-20-like token with custom transfer restrictions based on wallet and transaction limits. The contract exhibits good adherence to ERC-20 standards and includes immutable parameters for core tokenomics, enhancing predictability. However, a high-severity integer overflow vulnerability exists in the calculation of transfer limits under extreme `totalSupply` values. Centralized control by the `factory` address for critical setup functions and the lack of upgradeability or emergency pause mechanisms are also noted.

> **Final Recommendation:** It is strongly recommended to address the high-severity integer overflow vulnerability in the `maxWallet` and `maxTx` calculations to ensure the integrity of transfer restrictions. For enhanced security and operational robustness, consider implementing a multi-signature wallet for the `factory` address and adding functions for emergency pausing and recovery of accidentally sent tokens. Review the immutability of key tokenomic parameters to confirm alignment with long-term project goals regarding flexibility versus predictability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The OdysToken contract provides a basic ERC-20 implementation with additional transfer restrictions for wallet and transaction sizes (7.1 Architecture). It correctly implements standard ERC-20… |
| **Governance / Economics** | 1/10 | High | The `factory` address holds centralized control for setting the `liquidityPool` and `initialBuyRecipient` addresses (7.3 Access Control), posing a single point of failure if compromised. Key… |
| **Upgrades** | 6/10 | Medium | The OdysToken contract is not designed to be upgradeable (7.7 Upgrades), meaning its logic cannot be modified after deployment. This eliminates risks associated with proxy patterns, upgradeability… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 93.7% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 2 Low · ⚪ 2 Informational_

### `H-01` — Integer Overflow in `maxWallet` and `maxTx` Calculations  *(Severity: High · Status: Unresolved)*

The calculations for `maxWallet()` and `maxTx()` involve multiplication operations: `(totalSupply * maxWalletBps)` and `(w * 110)`. If `totalSupply` or `w` (the result of `maxWallet()`) are sufficiently large, these multiplications can exceed `type(uint256).max`, leading to an integer overflow. This would result in incorrect (smaller than intended) `maxWallet` or `maxTx` values, potentially allowing transfers that should be restricted or causing unexpected behavior in the token's economic model (7.2 Code Security).

**Recommendation:** Implement safe arithmetic for all multiplication operations, especially those involving large `uint256` values. Consider using OpenZeppelin's `SafeMath` library or explicitly checking for overflow before multiplication, for example, `require(totalSupply <= type(uint256).max / maxWalletBps, 'Overflow');`.


### `M-01` — Centralized Control by `factory` Address  *(Severity: Medium · Status: Unresolved)*

The `factory` address, set during contract deployment, holds exclusive control over critical functions such as `setPool()` and `setInitialBuyRecipient()` (7.3 Access Control). If the private key associated with this `factory` address is compromised, an attacker could maliciously set the `liquidityPool` or `initialBuyRecipient` to an arbitrary address, potentially disrupting liquidity or diverting funds. This represents a single point of failure for initial contract setup.

**Recommendation:** To mitigate the risk of a single point of failure, consider using a multi-signature wallet (e.g., Gnosis Safe) for the `factory` address. For highly critical operations, implementing a time-lock mechanism could provide a window for intervention if a malicious transaction is initiated.


### `M-02` — Immutability of Key Parameters Limits Flexibility  *(Severity: Medium · Status: Unresolved)*

The `maxWalletBps` and `restrictionSeconds` parameters are set as `immutable` in the constructor (7.4 Economic). While this provides predictability and reduces governance complexity, it also means these critical tokenomic parameters cannot be adjusted after deployment. This lack of flexibility could become a significant issue if unforeseen market conditions, community feedback, or protocol evolution necessitate changes to the token's transfer restrictions.

**Recommendation:** Evaluate whether future flexibility for these parameters is desirable. If so, consider making them configurable by a trusted entity (e.g., the `factory` address or a governance mechanism) with appropriate safeguards like time-locks or multi-signature approvals. If immutability is the intended design, ensure this decision is well-documented and understood by stakeholders.


### `L-01` — Missing `metaURI` Setter or Immutability Declaration  *(Severity: Low · Status: Unresolved)*

The `metaURI` state variable is declared as `string public` and initialized in the constructor. However, there is no setter function provided to update its value after deployment. If the intention was for `metaURI` to be mutable, this is an oversight. If it was intended to be immutable, it should be declared as `immutable` to clearly communicate its fixed nature and potentially save gas (7.1 Architecture).

**Recommendation:** Clarify the intended mutability of `metaURI`. If it should be immutable, declare it as `string public immutable metaURI;`. If it should be mutable, add a restricted setter function (e.g., callable only by the `factory` address) to allow updates.


### `L-02` — No Mechanism for Recovering Accidentally Sent Tokens  *(Severity: Low · Status: Unresolved)*

The contract lacks a function to recover accidentally sent ERC-20 tokens (other than its own `OdysToken`) or native currency (ETH/MATIC/BNB) that might be mistakenly sent to the contract address (7.8 Operations). Any such assets would become permanently locked within the contract, leading to irrecoverable loss.

**Recommendation:** Implement a restricted `recoverERC20(address tokenAddress, uint256 amount)` function and a `withdrawEther(uint256 amount)` function, callable only by the `factory` address. This would allow the recovery of assets sent to the contract by mistake.


### `I-01` — `unchecked` Block for `balanceOf[to] += value`  *(Severity: Informational · Status: Unresolved)*

The operation `balanceOf[to] += value;` is placed within an `unchecked` block. While `balanceOf[from] -= value;` is outside, ensuring `value` does not exceed `balanceOf[from]`, and `totalSupply` is fixed, it's important to confirm that `balanceOf[to]` can never exceed `type(uint256).max` under any valid scenario. Given the current design, where `value` is bounded by `balanceOf[from]` and `totalSupply` is fixed, an overflow of `balanceOf[to]` is highly unlikely, but explicit documentation of this invariant would be beneficial (7.2 Code Security).

**Recommendation:** Document the reasoning behind using `unchecked` for this specific operation, explicitly stating the invariants that prevent an overflow (e.g., `balanceOf[to]` cannot exceed `totalSupply`, and `totalSupply` is less than `type(uint256).max`).


### `I-02` — Lack of Emergency Pause Functionality  *(Severity: Informational · Status: Unresolved)*

The contract does not include a mechanism to pause transfers or other critical operations in case of an emergency, such as a discovered vulnerability, a major exploit in an integrated protocol, or severe market manipulation (7.8 Operations). Without a pause function, the protocol would be unable to react quickly to mitigate ongoing damage.

**Recommendation:** Consider adding a pause mechanism, controlled by the `factory` address (preferably a multi-signature wallet), that can temporarily halt transfers. This would provide a crucial safety switch during unforeseen events.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x768d...0c4e`](https://arbiscan.io/address/0x768d4b20869771a93946b5101a6a2e886f020c4e) |
| **Network** | Arbitrum |
| **Price** | $0.000137 |
| **24h Volume** | $29.8K |
| **Liquidity** | $44.6K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 20d |
| **Top-10 Holders** | 37.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 771 buys / 573 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0xb2d0b9fc11381130897f50656a9705bb6fdeb9d9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/nola-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-01*
