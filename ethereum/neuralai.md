---
token: NeuralAI
ticker: NEURAL
network: ethereum
risk_score: 55
status: medium
date: 2026-09-13
---

# NeuralAI (NEURAL) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 55/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/neuralai-eth)

---

## Audit Summary

The NeuralAI token contract exhibits critical technical flaws, including a severe bug in `transferFrom` and a failure to mint initial supply, rendering it non-functional. Furthermore, the liquidity pool lock has expired, posing a significant rug pull risk. The contract also features high centralization of control and high transaction fees.

> **Final Recommendation:** Address the critical technical flaws by implementing the initial token supply minting in the constructor and correcting the `transferFrom` logic to adhere to the ERC20 standard. Immediately re-lock the liquidity pool for a substantial period to mitigate the rug pull risk and restore investor confidence. Re-evaluate the high transaction fees to foster a more active and attractive trading environment. For long-term project sustainability, consider decentralizing critical administrative controls through a multi-signature wallet or a time-locked governance mechanism to reduce reliance on a single entity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The contract implements the ERC20 standard with additional features like anti-whale limits and a swap-and-liquify mechanism. It uses Solidity 0.8.12, benefiting from automatic overflow/underflow… |
| **Governance / Economics** | 2/10 | High | The contract design exhibits high centralization, with the owner possessing extensive control over critical parameters such as transaction fees, maximum buy/sell/wallet amounts, and the ability to… |
| **Upgrades** | 6/10 | Medium | The contract is not designed with an upgrade proxy pattern, meaning it is not upgradeable (7.7 Upgrades). This implies that any discovered vulnerabilities or desired feature enhancements… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 99.1% — Null Address, TeamFinance |
| **Top-1 Unlocked Holder** | 0.6% |
| **Lock Expiry** | Expired 540d ago |

## Security Findings

_🔴 1 Critical · 🟠 3 High · 🟡 1 Medium · 🟢 1 Low_

### `C-01` — No Initial Supply Minted in Constructor  *(Severity: Critical · Status: Unresolved)*

The `NeuralAI` contract's constructor calls the `ERC20` constructor but does not include a call to `_createInitialSupply` or any other minting mechanism. As a result, the `_totalSupply` remains 0, and no tokens are ever created or assigned to any address. This renders the token completely non-functional from deployment.

**Recommendation:** Add a call to `_createInitialSupply(msg.sender, totalSupply)` or a similar minting function within the `NeuralAI` constructor to initialize the token supply and assign it to the deployer or a designated address.


### `H-01` — LP Lock Expired / Rug Pull Risk  *(Severity: High · Status: Unresolved)*

The provided prefill data indicates that the liquidity pool lock status is 'lock_expired' and 'lp_unlock_days_remaining' is -540. This means the liquidity provided to the `uniswapV2Pair` is no longer locked and can be withdrawn by the liquidity provider at any time. This poses a severe rug pull risk, as the project owner or initial liquidity provider could remove all liquidity, making the token untradable and worthless.

**Recommendation:** Re-lock the liquidity for a significant period (e.g., 1-5 years) using a reputable locker service. Provide verifiable proof of the new lock to the community to restore trust and mitigate the rug pull risk.


### `H-02` — Non-Standard `transferFrom` Logic  *(Severity: High · Status: Unresolved)*

The `transferFrom` function deviates from the standard ERC20 implementation. It first calls `_transfer` (which moves tokens) and *then* checks the allowance and deducts it. While the transaction will revert if the allowance is insufficient, this order of operations is non-standard and can lead to wasted gas for users attempting `transferFrom` with insufficient allowance, as the `_transfer` operation would have already consumed gas before the revert.

**Recommendation:** Refactor the `transferFrom` function to first check and deduct the allowance, and only then proceed with the `_transfer` of tokens. This aligns with the ERC20 standard and optimizes gas usage for failed transactions.


### `H-03` — High Centralization of Control  *(Severity: High · Status: Unresolved)*

The `Ownable` pattern grants the contract owner extensive power over critical contract parameters and functions. The owner can modify transaction fees, maximum buy/sell/wallet amounts, enable/disable trading, exclude addresses from fees/limits, and transfer any foreign tokens sent to the contract. This high degree of centralization introduces a single point of failure and significant trust assumptions on the owner.

**Recommendation:** Consider implementing a multi-signature wallet for ownership or transitioning to a time-locked governance mechanism for critical parameter changes. For functions like `transferForeignToken`, consider adding a delay or a community vote mechanism to enhance security and transparency.


### `M-01` — High Transaction Fees  *(Severity: Medium · Status: Unresolved)*

The initial `buyFee` and `sellFee` are set to 30 (implying 30%). Such high transaction fees can significantly deter adoption, reduce trading volume, and make the token less attractive for users and exchanges. While the owner can change these, the initial setting is very high and could negatively impact the project's ecosystem.

**Recommendation:** Re-evaluate the fee structure. Consider implementing lower, more competitive fees to encourage adoption and trading. Clearly communicate the fee mechanism and any potential changes to the community.


### `L-01` — `transferForeignToken` Function Scope  *(Severity: Low · Status: Unresolved)*

The `transferForeignToken` function allows the owner to withdraw any ERC20 token accidentally sent to the contract. While useful for recovery, it grants the owner the power to withdraw any token without specific checks or community approval, which could be misused if the owner's key is compromised or if the owner acts maliciously.

**Recommendation:** While this function is common for recovery, consider enhancing its security by adding a time-lock or requiring multi-signature approval for withdrawing significant amounts of non-native tokens. This adds a layer of protection against potential misuse.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x32b0...e6e1`](https://etherscan.io/address/0x32b053f2cba79f80ada5078cb6b305da92bde6e1) |
| **Network** | Ethereum |
| **Price** | $0.6344 |
| **24h Volume** | $63.6K |
| **Liquidity** | $538.3K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 2y |
| **Top-10 Holders** | 29.4% of supply |
| **Buy / Sell Tax** | 4.0% / 4.0% |
| **24h Transactions** | 69 buys / 48 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x1112956589a2bea1b038732db4ea6b0c416ef130)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/neuralai-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-13*
