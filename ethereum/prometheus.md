---
token: Prometheus
ticker: PROMETHEUS
network: ethereum
risk_score: 40
status: medium
date: 2026-08-12
---

# Prometheus (PROMETHEUS) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 40/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/prometheus-eth)

---

## Audit Summary

The Prometheus token contract implements custom tax mechanisms, anti-bot/anti-whale features, and automated liquidity management. While it uses SafeMath for arithmetic safety, the audit reveals critical economic risks, primarily due to an unlocked liquidity pool and highly centralized control. The contract's high and dynamic tax rates also pose significant concerns for users.

> **Final Recommendation:** It is strongly recommended that users exercise extreme caution when interacting with this contract due to the critical risk of a rug pull from the unlocked liquidity pool. The project should immediately lock its liquidity to protect investor funds. Furthermore, the excessively high and dynamic tax rates, coupled with the extensive owner control, create an unfavorable and potentially exploitative economic environment. The project should consider significantly reducing tax rates, implementing a more transparent and immutable tax structure, and decentralizing control over critical parameters to build trust and foster a sustainable ecosystem.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes `SafeMath` for arithmetic operations, mitigating common integer overflow/underflow vulnerabilities. Standard ERC-20 functionality is implemented correctly. However, the… |
| **Governance / Economics** | 5/10 | Medium | The economic model presents significant risks, primarily due to an **unlocked liquidity pool** (7.4 Economic), which enables a rug pull by the deployer. The contract exhibits **high centralization**… |
| **Upgrades** | 8/10 | Low | The contract is not designed with upgradeability mechanisms (7.7 Upgrades), meaning its logic cannot be modified post-deployment. This eliminates risks associated with proxy patterns or upgrade… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 98.9% (≈ permanent lock) |
| **LP Locked** | 98.9% — Null Address |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 2 Medium · ⚪ 1 Informational_

### `C-01` — Unlocked Liquidity Pool (Rug Pull Risk)  *(Severity: Critical · Status: Unresolved)*

The provided information indicates that the liquidity pool for the Prometheus token is 'unlocked'. This means the deployer or owner of the liquidity pool tokens can remove the entire liquidity at any time, effectively draining the trading pair and rendering the token worthless. This is a classic 'rug pull' vector, posing an immediate and severe threat to investor funds (7.4 Economic).

**Recommendation:** Immediately lock the liquidity pool tokens using a reputable locker service or by transferring them to a burn address. Provide verifiable proof of liquidity locking to the community to build trust and mitigate this critical risk.


### `H-01` — Excessive Owner Privileges and Centralization  *(Severity: High · Status: Unresolved)*

The contract grants extensive control to the `owner()`, allowing manipulation of critical parameters. The owner can set various tax rates, transaction limits (`_maxTxAmount`, `_maxWalletSize`), swap parameters, and manage a `bots` mapping to exclude addresses from fees and limits. This high degree of centralization (7.3 Access Control) enables the owner to significantly impact the token's economy, potentially leading to unfair advantages, market manipulation, or malicious actions (7.4 Economic).

**Recommendation:** Consider implementing a multi-signature wallet or a time-locked governance mechanism for sensitive functions. For parameters that must remain adjustable, implement reasonable bounds and transparent update procedures. Clearly communicate the extent of owner control to the community.


### `H-02` — Extremely High and Punitive Transaction Taxes  *(Severity: High · Status: Unresolved)*

The contract implements initial buy/sell taxes of 25% and a transfer tax of 70% for regular transfers between non-owner addresses after the first buy. These excessively high tax rates (7.4 Economic) are highly punitive, making the token unattractive for holding or transferring and strongly indicating a 'honeypot' characteristic. The owner's ability to dynamically modify these taxes at will further exacerbates the risk of exploitation.

**Recommendation:** Significantly reduce all transaction taxes to foster a healthy and sustainable token economy. Consider implementing a fixed, transparent, and immutable tax structure to build trust and prevent potential abuse by the owner. Clearly document the tax mechanics and their purpose.


### `M-01` — Potential DoS for Sellers via `_taxWallet` Revert  *(Severity: Medium · Status: Unresolved)*

The `_transfer` function, specifically during sell operations to `uniswapV2Pair`, calls `sendETHToFee` to forward collected ETH to `_taxWallet`. If `_taxWallet` is a contract that is unable to receive ETH (e.g., due to a missing `receive()`/`fallback()` function or intentional revert logic), the `sendETHToFee` call will revert. This would cause the entire `_transfer` transaction to fail, effectively denying service for all sell transactions (7.2 Code Security, 7.8 Operations).

**Recommendation:** Ensure the `_taxWallet` is either an Externally Owned Account (EOA) or a robust contract designed to safely receive ETH. Implement a `try/catch` block around the `sendETHToFee` call to handle potential reverts gracefully, preventing the entire transaction from failing. Consider adding a mechanism to change the `_taxWallet` in case of issues.


### `M-02` — Anti-Bot/Anti-Whale Mechanisms Can Be Abused  *(Severity: Medium · Status: Unresolved)*

The contract includes `_maxTxAmount`, `_maxWalletSize`, and a `bots` mapping to prevent manipulation. However, these mechanisms are controlled by the owner, who can add or remove addresses from the `bots` list, effectively exempting them from taxes and limits (7.3 Access Control). This could be used to grant preferential treatment or manipulate the market. Additionally, the `sellCount` limit of 3 sells per block, while intended to prevent rapid dumping, can lead to legitimate users being unable to sell, causing frustration and potential DoS for sellers (7.4 Economic).

**Recommendation:** Implement transparent criteria and a decentralized process for managing bot lists or consider removing the ability to exempt specific addresses. Re-evaluate the sell limit per block to ensure it does not unduly restrict legitimate trading activity. Clearly document the purpose and impact of these mechanisms.


### `I-01` — Incomplete Code Snippet / Missing `sendETHToFee` Implementation  *(Severity: Informational · Status: Unresolved)*

The provided contract snippet is incomplete, specifically lacking the implementation of the `sendETHToFee` function and the contract's `receive()` or `fallback()` payable function. While the contract's balance suggests a `receive()`/`fallback()` exists, the absence of these critical components in the audit scope prevents a full security assessment of their logic and potential vulnerabilities (7.1 Architecture, 7.2 Code Security).

**Recommendation:** Provide the complete and final source code for all relevant functions and contracts to enable a comprehensive security audit. Ensure all external calls and ETH handling logic are explicitly defined and reviewed.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3cdb...04f1`](https://etherscan.io/address/0x3cdb41027d61c413e064e84d9c21812b6ef004f1) |
| **Network** | Ethereum |
| **Price** | $0.003439 |
| **24h Volume** | $214.7K |
| **Liquidity** | $34.3K |
| **Volume / Liquidity** | 6.3× |
| **Token Age** | 2d |
| **Top-10 Holders** | 24.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 590 buys / 399 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x70f4e3ed1ee30494c29150558a0b738af3e1b318)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/prometheus-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-12*
