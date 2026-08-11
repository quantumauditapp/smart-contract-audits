---
token: Orochi Network Token
ticker: ON
network: bsc
risk_score: 13
status: low
date: 2026-08-11
---

# Orochi Network Token (ON) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 13/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/orochi-network-token-bsc)

---

## Audit Summary

The BNBOrochiNetworkToken contract is an ERC-20 token built upon OpenZeppelin's battle-tested implementations for ERC20 and Ownable. The core token functionalities are robust. Key findings include a design limitation regarding the single-shot minting mechanism and the inherent centralization risk associated with the Ownable pattern. No critical technical vulnerabilities were identified.

> **Final Recommendation:** It is recommended to carefully plan the initial token supply due to the single-shot minting mechanism. Consider transferring ownership to a multi-signature wallet for enhanced security and shared control over the initial mint and other administrative functions. After all necessary administrative tasks are completed, evaluate the option of renouncing ownership to further decentralize control and reduce the single point of failure risk.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract leverages battle-tested OpenZeppelin ERC20 and Ownable implementations, ensuring robust core token functionalities and secure access control (7.2 Code Security). Standard ERC20… |
| **Governance / Economics** | 6/10 | Medium | The token's economic model features a single-shot minting mechanism controlled by the owner (7.4 Economic). Once a non-zero supply is minted, no further tokens can be created, which defines a fixed… |
| **Upgrades** | 9/10 | Low | The contract is not designed to be upgradeable (7.7 Upgrades), meaning its logic is immutable once deployed. This eliminates risks associated with proxy patterns, such as storage collisions or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Single-Shot Minting Design Limitation  *(Severity: Medium · Status: Unresolved)*

The `mint()` function includes a check `if (totalSupply() > 0) { revert AlreadyMinted(totalSupply()); }`, which prevents subsequent minting calls if any tokens have already been minted (i.e., `totalSupply` is non-zero). If the owner initially mints 0 tokens, they can still mint a non-zero amount later. However, if they mint any non-zero amount, they cannot mint additional tokens in the future. This design choice creates an immutable total supply after the first non-zero mint, which might be a desired feature but limits flexibility for future token supply management.

**Recommendation:** Confirm that a fixed, non-expandable token supply after the initial mint is the intended tokenomic model. If future flexibility for supply adjustments (e.g., for ecosystem growth, liquidity incentives) is ever desired, this design would require a new contract deployment. Ensure the initial mint quantity is carefully planned to meet all long-term requirements.


### `L-01` — Centralized Ownership Risk  *(Severity: Low · Status: Unresolved)*

The contract utilizes the `Ownable` pattern, granting a single external address (the `owner`) exclusive control over critical administrative functions, specifically the `mint()` function and the ability to `transferOwnership()`. This introduces a single point of failure (7.3 Access Control). If the owner's private key is compromised, a malicious actor could potentially perform an unauthorized initial mint or transfer ownership to themselves, leading to a loss of control or unexpected token distribution.

**Recommendation:** To mitigate the risk associated with a single point of failure, consider transferring ownership to a multi-signature wallet (e.g., Gnosis Safe) after deployment. This distributes control among multiple trusted parties, requiring multiple approvals for critical operations. Alternatively, if the token supply is fixed and no further administrative actions are anticipated, the owner could renounce ownership to fully decentralize control.


### `I-01` — Immutability of Token Decimals  *(Severity: Informational · Status: Unresolved)*

The `decimals()` function is hardcoded to return `18`. While 18 is the most common and widely accepted standard for ERC-20 token decimals, this value is immutable once the contract is deployed. Any future requirement to change the token's decimal precision would necessitate deploying an entirely new token contract.

**Recommendation:** Confirm that 18 decimals is the permanent and desired configuration for the token. This is generally a safe and standard practice, but it's important to acknowledge its immutability in the context of long-term project planning.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0e4f...1d48`](https://bscscan.com/address/0x0e4f6209ed984b21edea43ace6e09559ed051d48) |
| **Network** | BNB Chain |
| **Price** | $0.3905 |
| **24h Volume** | $8.99M |
| **Liquidity** | $1.54M |
| **Volume / Liquidity** | 5.8× |
| **Token Age** | 9mo |
| **Top-10 Holders** | 53.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 21219 buys / 22450 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x4620f5c127a6055fbebb1f71327d60ff079c9060)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/orochi-network-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
