---
token: GULD
ticker: GULD
network: ethereum
risk_score: 37
status: medium
date: 2026-08-12
---

# GULD (GULD) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 37/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/guld-eth)

---

## Audit Summary

This report details the security audit of the Custom Token contract. The audit identified a high-severity issue related to potential integer overflow in balance updates within unchecked blocks, two medium-severity issues concerning ERC-20 non-compliance and centralized control, and other minor findings. The contract implements a basic ERC-20-like token with minting capabilities up to a maximum supply.

> **Final Recommendation:** It is strongly recommended to address the high-severity integer overflow vulnerability by removing the `unchecked` blocks around `balanceOf` additions. The ERC-20 non-compliance for `totalSupply` should also be corrected to ensure broad compatibility. For the centralized roles, implement robust operational security measures like multi-signature wallets. Thoroughly test all fixes in a staging environment before deployment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract exhibits a clear structure and generally follows common Solidity patterns. Strengths include the use of `immutable` for critical parameters like `decimals` and `maxSupply`, and a… |
| **Governance / Economics** | 3/10 | High | The token's economic model is straightforward, with a fixed `maxSupply` and a centralized `issuer` role responsible for minting (7.4 Economic). The `owner` role holds significant power, including the… |
| **Upgrades** | 3/10 | High | This contract is not designed to be upgradeable. Its logic is immutable once deployed, which eliminates upgrade-related risks such as proxy misconfigurations or malicious upgrade implementations (7.7… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — ERC-20 Non-Compliance for `totalSupply`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract declares `totalSupply` as a public state variable (`uint256 public totalSupply;`) instead of implementing it as a public view function (`function totalSupply() external view returns (uint)`), as required by the ERC-20 standard. This deviation can cause compatibility issues with wallets, exchanges, and other DeFi protocols that expect the `totalSupply()` function to exist.

**Recommendation:** Change `uint256 public totalSupply;` to `uint256 internal _totalSupply;` and implement the `totalSupply()` function as `function totalSupply() external view override returns (uint) { return _totalSupply; }`. Update all internal references to `totalSupply` to `_totalSupply`.


### `M-02` — Centralized Control Over Token Supply and Ownership  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract design grants significant power to the `owner` and `issuer` roles. The `owner` can transfer ownership (via a two-step process) and change the `issuer`. The `issuer` has the sole ability to `mint` new tokens up to the `maxSupply`. This centralization introduces a single point of failure and trust, as a compromised `owner` or `issuer` account could lead to unauthorized minting or control transfer.

**Recommendation:** Acknowledge this centralization as part of the token's design. If decentralization is desired in the future, consider implementing a multi-signature wallet for the `owner` and `issuer` roles, or integrating a governance mechanism to manage these critical functions.


### `M-03` — Potential Integer Overflow in `balanceOf` Addition (unchecked block)  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `mint` and `_updateBalance` functions use `unchecked` blocks for `balanceOf[to] += value;`. While `totalSupply` is capped by `maxSupply`, individual `balanceOf` values are not explicitly checked against `type(uint256).max` before addition within these `unchecked` blocks. If `maxSupply` is sufficiently large (e.g., close to `type(uint256).max`) and a large `value` is minted or transferred to an address already holding a large balance, the `balanceOf[to]` could wrap around, leading to an incorrect, lower balance for the recipient.

**Recommendation:** Remove the `unchecked` block around `balanceOf[to] += value;` in both `mint` and `_updateBalance` functions. Solidity 0.8+ provides default overflow/underflow checks, which should be leveraged here to ensure `balanceOf` values do not wrap around.


### `L-01` — Standard `approve` Function Front-Running Vulnerability  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `approve` function, as implemented in the ERC-20 standard, is susceptible to a known front-running attack. If a user approves an amount `X` for a spender, and then decides to change the approved amount to `Y` (where `Y < X`), a malicious front-runner could observe the transaction to change the allowance, quickly execute the original allowance `X`, and then the user's transaction would set the allowance to `Y`, effectively allowing the front-runner to spend `X + Y`.

**Recommendation:** Advise users to always set the allowance to zero before setting a new non-zero allowance, i.e., call `approve(spender, 0)` then `approve(spender, newAmount)`. Alternatively, consider implementing an `increaseAllowance` and `decreaseAllowance` pattern to mitigate this user-side risk.


### `I-01` — Lack of Token Burn Mechanism  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract does not include a function to burn tokens, which means tokens can only be transferred or minted (up to `maxSupply`). There is no mechanism to permanently remove tokens from circulation, which might be desired for certain economic models or to recover tokens sent to unrecoverable addresses.

**Recommendation:** If a token burn mechanism is desired, consider adding a `burn` function that allows token holders to destroy their own tokens, or an `ownerBurn` function for administrative burning, ensuring appropriate access controls are in place.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x14d6...47a1`](https://etherscan.io/address/0x14d6c649292c5c9790c5196d1a9ea039307947a1) |
| **Network** | Ethereum |
| **Price** | $0.02188 |
| **24h Volume** | $306.3K |
| **Liquidity** | $2.13M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 40.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 86 buys / 101 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xf63fb2907e8f1067caad3dbf158bcd71b9937a054e601a7a4f8cda55e2417ce8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/guld-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-12*
