---
token: Epic Chain
ticker: EPIC
network: ethereum
risk_score: 73
status: critical
date: 2026-07-23
---

# Epic Chain (EPIC) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 73/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/epic-chain-eth)

---

## Audit Summary

The EpicToken contract implements an ERC20 token with burnable functionality and a controlled minting mechanism. It leverages battle-tested OpenZeppelin libraries for access control (Ownable2Step) and token standards. The contract features a dual-role access control system with an owner and a governor. Key findings include a continuous inflationary minting mechanism and the immutability of the minting frequency parameter, which are significant economic design considerations.

> **Final Recommendation:** It is crucial for the project team to clearly communicate the continuous inflationary nature of the token's economic model to all stakeholders, ensuring full transparency regarding potential supply growth. Additionally, careful consideration should be given to the initial `waitPeriod` value, as its immutability means it cannot be adjusted after deployment. Thorough testing of the minting frequency and amount under various scenarios is recommended.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical implementation of the EpicToken contract is robust, utilizing well-audited OpenZeppelin libraries for ERC20, ERC20Burnable, and Ownable2Step functionalities. The access control… |
| **Governance / Economics** | 1/10 | High | The contract establishes a clear governance structure with an `owner` (expected to be a multisig) and a `governor` role for minting. The `owner` has control over setting the `governor` and recovering… |
| **Upgrades** | 4/10 | Medium | The EpicToken contract is not designed with upgradeability in mind (7.7 Upgrades). It is a standard, non-proxy implementation, meaning its logic cannot be modified post-deployment. This simplifies… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.7% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Unbounded Inflationary Mechanism  *(Severity: High · Status: Unresolved)*

The `mint` function allows the `governor` to mint up to 12% of the `initialSupply` every `waitPeriod`. This mechanism is a continuous inflationary process, not a one-time cap, meaning the total token supply can grow indefinitely over time by 12% of the initial supply per period. The comment 'up to 12% of the initial supply' could be misinterpreted as a total cap rather than a per-period limit, potentially leading to a misunderstanding of the token's long-term economic model (7.4 Economic).

**Recommendation:** Clearly document and communicate the continuous inflationary nature of the token supply. Consider adding a hard cap on the total supply or a mechanism to reduce the minting rate over time if unbounded inflation is not the desired long-term economic model. If the current design is intentional, ensure all documentation reflects this accurately.


### `M-01` — Immutability of `waitPeriod` Parameter  *(Severity: Medium · Status: Unresolved)*

The `waitPeriod` variable, which determines the minimum time between minting events, is set during the contract constructor and cannot be modified thereafter. An incorrectly configured `waitPeriod` could lead to either excessive inflation (if too short) or hinder necessary supply adjustments (if too long), without any on-chain mechanism for correction (7.4 Economic, 7.8 Operations).

**Recommendation:** Consider implementing a mechanism to allow the `owner` or `governor` to update the `waitPeriod` parameter, possibly with a time-lock or multi-signature approval, to provide flexibility for future economic adjustments. If immutability is desired, ensure the initial value is thoroughly vetted for long-term suitability.


### `L-01` — Centralization Risk with `adminTokenWithdraw`  *(Severity: Low · Status: Unresolved)*

The `adminTokenWithdraw` function allows the contract `owner` to withdraw any ERC20 tokens mistakenly sent to the contract. While a standard recovery mechanism, it grants significant power to a single address (the `owner`). A compromise of the owner's private key could lead to the loss of any such tokens held by the contract (7.3 Access Control, 7.8 Operations).

**Recommendation:** Ensure the `owner` address is secured with robust practices, such as a hardware wallet or a well-configured multi-signature wallet. Consider adding a time-lock or requiring multi-signature approval for high-value withdrawals if the contract is expected to hold significant amounts of external tokens.


### `I-01` — Constructor Requirement for Initial Owner as Contract  *(Severity: Informational · Status: Unresolved)*

The contract constructor explicitly requires the `_initialOwner` to be a contract (e.g., a multisig wallet) by using `require(_initialOwner.isContract(), "Initial owner can't be an EOA")`. While this is a good security practice to enforce robust ownership (like a multisig), it prevents a simple Externally Owned Account (EOA) from being the initial owner, which might be unexpected for some deployers (7.1 Architecture, 7.3 Access Control).

**Recommendation:** This is a design choice that enhances security by promoting multisig ownership. No change is strictly required, but ensure this requirement is clearly documented for anyone deploying the contract.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9431...fc0e`](https://etherscan.io/address/0x94314a14df63779c99c0764a30e0cd22fa78fc0e) |
| **Network** | Ethereum |
| **Price** | $0.6026 |
| **24h Volume** | $34.8K |
| **Liquidity** | $116.3K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 72.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 376 buys / 388 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xec0a57d0ad701e7c54a084f4a69ab633955b6eec9dbef9a7092d78096ff1521b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/epic-chain-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-23*
