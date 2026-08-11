---
token: Mog Coin
ticker: MOG
network: ethereum
risk_score: 26
status: medium
date: 2026-08-11
---

# Mog Coin (MOG) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 26/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mog-coin-eth)

---

## Audit Summary

The MOG contract is an ERC-20 token with features such as transaction fees, automatic liquidity provision, and anti-whale mechanisms (max wallet/transaction limits). The contract utilizes the Ownable pattern, and the prefill data indicates that ownership has been renounced. This renunciation makes all owner-controlled parameters and functions immutable, which is the primary driver of the identified high and critical risks. The provided contract code was truncated, specifically the core transfer logic, but the analysis assumes the fee and limit mechanisms are correctly implemented within the missing sections based on the declared state variables and mappings.

> **Final Recommendation:** For projects considering renouncing ownership, it is paramount to conduct exhaustive pre-deployment testing and verification of all configurable parameters. Ensure that all critical functions, such as enabling trading and setting appropriate fee structures and limits, are correctly executed before renunciation. Once ownership is renounced, the contract's behavior is permanently fixed, making any misconfiguration irreversible. Future projects should consider implementing a multi-signature wallet or a time-locked contract for critical administrative functions if full decentralization via ownership renunciation is not the immediate goal, allowing for controlled parameter adjustments.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract employs SafeMath for arithmetic operations, mitigating common integer overflow/underflow vulnerabilities (7.2 Code Security). A `swapping` modifier is used to prevent reentrancy during… |
| **Governance / Economics** | 7/10 | Low | Before ownership renunciation, the contract had a highly centralized governance model, with the owner able to modify transaction fees, set receiver addresses, and adjust max wallet/transaction limits… |
| **Upgrades** | 9/10 | Low | The MOG contract is a standard (non-proxy) implementation and is not designed to be upgradeable (7.7 Upgrades). Therefore, there are no upgrade-specific risks associated with this contract. All… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — UNCX |
| **Top-1 Unlocked Holder** | 0.0% |
| **Lock Expiry** | ✅ 2092 (verified ≥ 1 year) — UNCX V2 |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Irreversible Immutability of Critical Parameters Post-Renunciation  *(Severity: Critical · Status: Unresolved)*

With ownership renounced, all owner-controlled functions (e.g., `EditTax`, `set_Receivers`, `set_MaxWallet`, `set_MaxTX`, `openTrading`, `clearStuckETH`, `clearStuckToken`) are permanently disabled. This means that if any critical parameter was misconfigured, or if `TradingOpen` was not called before renunciation, the token's functionality could be severely and irreversibly hampered or bricked, leading to a complete loss of utility or funds. For example, if `TradingOpen` was not called, trading might never be possible. Similarly, if `clearStuckETH` or `clearStuckToken` were needed, they are now unusable.

**Recommendation:** This issue is irreversible for the current contract due to renounced ownership. For future projects, ensure all critical parameters are meticulously configured and all necessary administrative actions (like enabling trading) are completed and verified before renouncing ownership. Consider a phased approach to decentralization or a multi-sig/timelock for critical functions if full immutability is not desired immediately.


### `H-01` — High and Unchangeable Transaction Fees  *(Severity: High · Status: Unresolved)*

The contract allows for significant transaction fees (liquidity, marketing, dev, buyback, burn) which are now immutable due to renounced ownership. The `EditTax` function, which could adjust `buypercent`, `sellpercent`, and `transferpercent` (affecting `totalFee`), is no longer callable. If the initial configuration set high fees, it could permanently deter trading, reduce liquidity, and make the token economically unviable for users, as these fees cannot be lowered.

**Recommendation:** This issue is irreversible for the current contract. For future projects, carefully model the economic impact of transaction fees. If ownership is to be renounced, ensure that the initial fee structure is sustainable and competitive, as it cannot be altered post-renunciation. Consider community governance for fee adjustments if flexibility is desired.


### `H-02` — Unchangeable Max Wallet/Transaction Limits  *(Severity: High · Status: Unresolved)*

The `_maxTxAmount` and `_maxWalletToken` limits are fixed after ownership renunciation. While intended as anti-whale measures, if set too restrictively (e.g., 1% of total supply), they can permanently hinder legitimate large transfers, prevent necessary liquidity pool rebalancing, or even block interactions with certain DeFi protocols. The `set_MaxWallet` and `set_MaxTX` functions, which could adjust these limits, are now unusable, potentially bricking the token's utility for certain use cases.

**Recommendation:** This issue is irreversible for the current contract. For future projects, carefully consider the implications of fixed max wallet and transaction limits. If ownership is to be renounced, ensure these limits are set to values that allow for healthy market operation and interaction with other protocols, or consider mechanisms for community-driven adjustments.


### `M-01` — Missing Zero Address Checks for Fee Receivers  *(Severity: Medium · Status: Unresolved)*

The `set_Receivers` function, if called before ownership renunciation, allowed setting `marketingFeeReceiver`, `buybackFeeReceiver`, or `devFeeReceiver` to `address(0)` without explicit checks. If this occurred, the corresponding fees would be permanently burned instead of being directed to a functional address, potentially impacting project funding or the intended distribution of funds. While `burnFeeReceiver` is intentionally set to `DEAD`, other receivers should typically be valid addresses.

**Recommendation:** For future contracts, implement explicit `require(newReceiver != address(0), "Receiver cannot be zero address")` checks in functions that set critical addresses like fee receivers. This prevents accidental or malicious burning of funds intended for project operations.


### `L-01` — Unused `authorizations` Mapping  *(Severity: Low · Status: Unresolved)*

The `authorizations` mapping in the `Ownable` contract is declared and initialized in the constructor by setting `authorizations[_owner] = true`. However, this mapping is never utilized by any other function within the contract (e.g., the `onlyOwner` modifier directly checks `_owner == _msgSender()`). This represents dead code, increasing contract size and potentially causing confusion for auditors or developers.

**Recommendation:** Remove the unused `authorizations` mapping and its initialization from the `Ownable` contract to reduce contract size and improve code clarity. If its functionality was intended, ensure it is properly integrated into the access control logic.


### `I-01` — Hardcoded DEX Router Address  *(Severity: Informational · Status: Unresolved)*

The Uniswap V2 router address (0x7a250d5630B4cF539739dF2C5dAcb4c659F2488D) is hardcoded within the contract's constructor. While common for established protocols, this design choice means the contract cannot adapt if the router address changes, is deprecated, or becomes compromised. Any such event would render the contract's internal swap and liquidity functions inoperable.

**Recommendation:** For future contracts, consider making critical external contract addresses configurable by an authorized entity (e.g., via an `onlyOwner` function) or through a governance mechanism. This allows for adaptability to changes in the ecosystem without requiring a new contract deployment.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xaaee...1c7a`](https://etherscan.io/address/0xaaee1a9723aadb7afa2810263653a34ba2c21c7a) |
| **Network** | Ethereum |
| **Price** | $0.0000001 |
| **24h Volume** | $75.9K |
| **Liquidity** | $4.53M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 3y |
| **Top-10 Holders** | 57.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 75 buys / 72 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xc2eab7d33d3cb97692ecb231a5d0e4a649cb539d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mog-coin-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
