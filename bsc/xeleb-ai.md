---
token: Xeleb AI
ticker: XCX
network: bsc
risk_score: 33
status: low
date: 2026-09-28
---

# Xeleb AI (XCX) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 33/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xeleb-ai-bsc)

---

## Audit Summary

The TokenERC20 contract is a standard ERC-20 token implementation, inheriting from OpenZeppelin's battle-tested ERC20 and ERC20Burnable contracts. The code quality is high, and no critical or high-severity vulnerabilities were identified. The primary considerations are related to the initial centralized token distribution, the non-upgradeable nature of the contract, and the inherent race condition in the standard ERC-20 `approve` function.

> **Final Recommendation:** The TokenERC20 contract is a robust implementation of an ERC-20 token, benefiting greatly from OpenZeppelin's secure and audited libraries. For projects considering long-term growth or requiring flexibility, evaluate the need for an upgradeable contract architecture to allow for future enhancements or bug fixes without redeployment. Additionally, consider a more decentralized initial token distribution strategy to mitigate risks associated with single-entity control.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract leverages OpenZeppelin's well-audited ERC20 and ERC20Burnable implementations, which significantly reduces the risk of common technical vulnerabilities (7.1 Architecture, 7.2 Code… |
| **Governance / Economics** | 1/10 | High | The contract's economic model (7.4 Economic) involves an initial total supply minted entirely to the deployer, leading to a centralized distribution. While common for new tokens, this implies the… |
| **Upgrades** | 6/10 | Medium | The TokenERC20 contract is implemented as a standard, non-upgradeable contract (7.7 Upgrades). This design choice means that its logic cannot be modified post-deployment. While this eliminates… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 70.6% |
| **Top-3 Unlocked** | ⚠️ 82.7% |

## Security Findings

_🟢 1 Low · ⚪ 2 Informational_

### `L-01` — Standard ERC-20 `approve` Race Condition  *(Severity: Low · Status: Unresolved)*

The standard ERC-20 `approve` function, as implemented in OpenZeppelin's ERC20, is susceptible to a known front-running vulnerability. If a user attempts to change an existing allowance from `X` to `Y` (where `Y` is not 0), a malicious actor observing this transaction could front-run it by spending the original `X` allowance before the new `Y` allowance is set. This could lead to the malicious actor effectively spending `X + Y` tokens instead of just `Y`, if the user's intent was to replace `X` with `Y`.

**Recommendation:** Users should be advised to always set the allowance to zero (`approve(spender, 0)`) before setting a new non-zero allowance to mitigate this specific race condition. Alternatively, for more robust allowance management, consider using `increaseAllowance` and `decreaseAllowance` functions (if implemented in a custom ERC20 extension), which are designed to prevent this type of front-running attack.


### `I-01` — Centralized Initial Token Distribution  *(Severity: Informational · Status: Unresolved)*

The `TokenERC20` contract's constructor mints the entire `_totalSupply` to `msg.sender` (the deployer). This design choice results in a highly centralized initial distribution, where the deployer holds 100% of the token supply. This concentration of tokens can pose risks related to market manipulation, single points of failure, or perceived lack of decentralization.

**Recommendation:** Projects should consider a more decentralized distribution strategy for the initial token supply. This could involve mechanisms such as airdrops, liquidity pool provisioning, vesting schedules, or multi-signature controlled treasuries to distribute tokens among multiple stakeholders or the community. This is a design decision that impacts economic governance and project perception.


### `I-02` — Non-Upgradeable Contract Design  *(Severity: Informational · Status: Unresolved)*

The `TokenERC20` contract is deployed as a standard, non-upgradeable contract. This means that once deployed, its logic cannot be modified or updated. Any discovered vulnerabilities, desired feature enhancements, or changes to the token's behavior would require deploying a new contract and migrating all users and assets, which can be a complex and costly process.

**Recommendation:** For projects with long-term aspirations or those that anticipate evolving requirements, consider implementing an upgradeable proxy pattern (e.g., UUPS, Transparent) from OpenZeppelin. This would allow for future bug fixes, optimizations, or feature additions without requiring a full redeployment and migration, enhancing the project's longevity and adaptability.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe32f...8eaf`](https://bscscan.com/address/0xe32f9e8f7f7222fcd83ee0fc68baf12118448eaf) |
| **Network** | BNB Chain |
| **Price** | $0.003746 |
| **24h Volume** | $64.3K |
| **Liquidity** | $75.5K |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 1y |
| **Top-10 Holders** | 96.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 809 buys / 741 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x8c4c97d6a279c6a3eb63348c760ff0153aa779ee)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xeleb-ai-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-28*
