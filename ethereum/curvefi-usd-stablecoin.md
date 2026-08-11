---
token: Curve.Fi USD Stablecoin
ticker: CRVUSD
network: ethereum
risk_score: 41
status: medium
date: 2026-08-11
---

# Curve.Fi USD Stablecoin (CRVUSD) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 41/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/curvefi-usd-stablecoin-eth)

---

## Audit Summary

The crvUSD Stablecoin contract is a Vyper-based ERC-20 token implementation, including EIP-2612 permit functionality and a centralized minter role. The code demonstrates high quality, robust handling of integer arithmetic, and adherence to ERC standards. Key security features like replay protection for EIP-2612 and explicit overflow/underflow checks are correctly implemented. The primary risk identified is the centralized control over token minting, which is a design decision inherent to many stablecoins but represents a single point of failure.

> **Final Recommendation:** Ensure the private key controlling the `minter` address is secured with the highest possible standards, ideally using a multi-signature wallet or a hardware security module. Implement robust operational procedures (7.8 Operations) for managing this key and any `set_minter` operations. While the contract is technically sound, continuous monitoring of the `minter` address for unusual activity is recommended. Consider transparent reporting on minting activities to enhance trust and accountability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract exhibits strong technical security (7.2 Code Security). It correctly implements ERC-20 and EIP-2612 standards, including robust replay protection for permits and ERC-1271 support for… |
| **Governance / Economics** | 2/10 | High | The economic model (7.4 Economic) centers around a stablecoin with a centralized `minter` role. This `minter` has the sole authority to mint new tokens and transfer the minter privilege (7.5… |
| **Upgrades** | 3/10 | High | This contract is not designed with an upgrade mechanism (7.7 Upgrades). It is deployed as a standalone, immutable contract. Therefore, there are no upgrade-related risks to assess. Any future changes… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 2 Informational_

### `M-01` — Centralized Minter Role  *(Severity: Medium · Status: Unresolved)*

The `minter` address holds exclusive control over the `mint` function, allowing it to create an arbitrary amount of new tokens. Additionally, the `minter` can transfer this privilege to any other address via `set_minter`. While this is a common design for centralized stablecoins, it introduces a significant single point of failure. A compromise of the `minter`'s private key would allow an attacker to inflate the token supply, leading to a loss of peg and severe economic consequences for the protocol and its users.

**Recommendation:** Implement robust security measures for the `minter` address, such as a multi-signature wallet with a high threshold for transactions, or a time-locked governance mechanism. Establish clear operational procedures for managing the `minter` key and any changes to the `minter` address. Consider a mechanism for emergency pausing or rate-limiting minting if feasible within the protocol's design.


### `I-01` — Standard ERC-20 `approve` Race Condition  *(Severity: Informational · Status: Unresolved)*

The `approve` function, as per the ERC-20 standard, is susceptible to a known front-running or race condition attack. If a user increases an allowance from `X` to `Y` and a malicious spender observes this transaction, they can front-run it by spending the original `X` allowance, then allowing the user's `approve(Y)` transaction to confirm, and finally spending `Y` tokens. This results in the spender taking `X + Y` tokens instead of just `Y` (or `X` if the user intended to decrease). The contract's docstring for `approve` acknowledges this and recommends `increaseAllowance` and `decreaseAllowance` as safer alternatives.

**Recommendation:** Educate users to primarily use `increaseAllowance` and `decreaseAllowance` instead of directly calling `approve` when changing an existing allowance. If `approve` must be used to change an allowance, it is best practice to first set the allowance to zero before setting it to a new non-zero value.


### `I-02` — Immutability of EIP-712 `salt` from `block.prevhash`  *(Severity: Informational · Status: Unresolved)*

The EIP-712 domain separator `salt` is initialized in the constructor using `block.prevhash` and then made `immutable`. While `block.prevhash` provides a unique value for the deployment, ensuring domain separation, it is not a cryptographically strong source of randomness. For the specific purpose of an EIP-712 `salt`, which primarily needs to be unique per deployment and consistent, this approach is generally acceptable and does not pose a direct security vulnerability. The contract also correctly recalculates the domain separator if `chain.id` changes, enhancing fork safety.

**Recommendation:** No direct action is required as the current implementation is acceptable for its intended purpose. For future contracts requiring stronger randomness or unpredictability for initialization parameters, consider using a Verifiable Random Function (VRF) or a more robust source of entropy if available and appropriate for the use case.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf939...1b4e`](https://etherscan.io/address/0xf939e0a03fb07f59a73314e73794be0e57ac1b4e) |
| **Network** | Ethereum |
| **Price** | $1.0001 |
| **24h Volume** | $4.93M |
| **Liquidity** | $46.39M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 3y |
| **Top-10 Holders** | 79.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 207 buys / 381 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x390f3595bca2df7d23783dfd126427cceb997bf4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/curvefi-usd-stablecoin-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
