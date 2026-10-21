---
token: SKI MASK DOG
ticker: SKI
network: base
risk_score: 13
status: low
date: 2026-08-30
---

# SKI MASK DOG (SKI) — Smart Contract Security Analysis | Base

> **Risk Score: 13/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ski-mask-dog-base)

---

## Audit Summary

The SKI token contract is an ERC-20 implementation featuring dynamic taxes, anti-whale, and anti-bot mechanisms. The provided information indicates that ownership has been renounced, making the contract immutable. This immutability, combined with the default high tax rates and fixed operational parameters, introduces significant risks, including potential honeypot characteristics and a lack of adaptability. Users should exercise extreme caution.

> **Final Recommendation:** It is strongly recommended to thoroughly review the deployment state of the contract, specifically verifying if `openTrading()` and `setSwapEnabled(true)` were called *before* ownership was renounced. Given the high, fixed tax rates, potential investors should exercise extreme caution and understand the implications of these immutable parameters. For future projects, consider a phased approach to renouncing ownership, ensuring all critical operational parameters are correctly configured and tested, and potentially implementing a lower, more sustainable tax structure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes `SafeMath` for arithmetic operations, mitigating common integer overflow/underflow vulnerabilities (7.2 Code Security). A `lockTheSwap` modifier is implemented to prevent… |
| **Governance / Economics** | 7/10 | Low | The primary economic risk stems from the renounced ownership, which fixes the initial buy/sell taxes at 20% (7.4 Economic). This high, immutable tax rate creates a significant honeypot risk, as users… |
| **Upgrades** | 9/10 | Low | The contract is not designed with upgradeability in mind, as indicated by `is_proxy: false` (7.7 Upgrades). This means there are no upgrade-specific risks such as proxy misconfigurations or logic… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 2 Medium · ⚪ 1 Informational_

### `C-01` — Honeypot Risk due to High Fixed Taxes  *(Severity: Critical · Status: Unresolved)*

The contract's ownership has been renounced, making all `onlyOwner` functions inaccessible. This means the initial buy and sell taxes are permanently fixed at 20% (assuming `finaltax` was not set to `true` before renunciation). Such high, immutable taxes make it extremely difficult for users to profit, as a significant portion of their investment is lost on each transaction, creating a strong honeypot characteristic. This directly impacts the economic viability of the token (7.4 Economic).

**Recommendation:** For future projects, avoid renouncing ownership with such high, fixed tax rates. If immutability is desired, ensure tax rates are set to a sustainable level (e.g., 0-5%) before renunciation. For this deployed contract, users should be made aware of the permanent high tax rates.


### `H-01` — Immutability of Critical Operational Parameters  *(Severity: High · Status: Unresolved)*

With renounced ownership, critical operational parameters such as `_maxTxAmount`, `_maxWalletSize`, `_taxSwapThreshold`, `_maxTaxSwap`, `transferDelayEnabled`, and `_preventSwapBefore` are permanently fixed at their initial values. This removes any flexibility to adapt to changing market conditions, address unforeseen issues, or optimize tokenomics post-deployment. For example, if `_maxTxAmount` is too restrictive, it could hinder large legitimate trades (7.8 Operations, 7.5 Governance).

**Recommendation:** Before renouncing ownership, ensure all critical parameters are thoroughly tested and set to optimal, sustainable values. Consider if complete immutability is truly necessary for a token with complex dynamic features, or if a multi-sig or timelock governance could manage critical parameters.


### `H-02` — Potential for Untradable Token Post-Renunciation  *(Severity: High · Status: Unresolved)*

If the `openTrading()` function (which creates the Uniswap pair and adds initial liquidity) and `setSwapEnabled(true)` were not called by the owner *before* ownership was renounced, the token would be permanently untradable. Users would be able to buy tokens (if a pair was manually created elsewhere) but would be unable to sell them through the intended Uniswap integration, and collected taxes would not be swapped to ETH, making the token a hard honeypot (7.8 Operations, 7.4 Economic).

**Recommendation:** Verify the deployment sequence to confirm that `openTrading()` and `setSwapEnabled(true)` were successfully executed before ownership renunciation. For future deployments, ensure a robust checklist for pre-renunciation setup.


### `M-01` — `tx.origin` Usage for Transfer Delay  *(Severity: Medium · Status: Unresolved)*

The `_holderLastTransferTimestamp` mapping uses `tx.origin` to enforce a transfer delay (one purchase per block). While intended for anti-bot measures, relying on `tx.origin` can be problematic. If a user interacts with the contract through another contract that forwards `tx.origin`, it might lead to unexpected behavior or potential bypasses of the delay mechanism, as `tx.origin` always refers to the original external account (EOA) that initiated the transaction (7.2 Code Security).

**Recommendation:** Consider using `msg.sender` instead of `tx.origin` for tracking user-specific delays, as `msg.sender` reliably identifies the immediate caller, whether it's an EOA or a contract. This provides a more robust and secure approach to access control and user tracking.


### `M-02` — Lack of Emergency Stop/Pause Functionality  *(Severity: Medium · Status: Unresolved)*

With renounced ownership, there is no longer an owner or any other entity capable of pausing transfers or stopping trading in the event of a critical vulnerability, market exploit, or unforeseen operational issue. This lack of an emergency stop mechanism leaves the contract vulnerable to cascading failures without any recourse (7.8 Operations, 7.5 Governance).

**Recommendation:** For future projects, if renouncing ownership, consider implementing a decentralized emergency pause mechanism (e.g., via a timelock or community governance) or carefully weigh the risks of complete immutability against the need for emergency intervention capabilities.


### `I-01` — Centralized `_taxWallet`  *(Severity: Informational · Status: Unresolved)*

The `_taxWallet` is set to the deployer's address in the constructor and, due to renounced ownership, cannot be changed. All collected ETH from tax swaps is sent to this single, unchangeable address. This centralizes the control of collected funds to one entity without any multi-signature or timelock protection (7.4 Economic).

**Recommendation:** For future projects, consider using a multi-signature wallet or a timelock contract for the `_taxWallet` to enhance security and decentralization of collected funds, even if ownership is renounced.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x768b...0149`](https://basescan.org/address/0x768be13e1680b5ebe0024c42c896e3db59ec0149) |
| **Network** | Base |
| **Price** | $0.003934 |
| **24h Volume** | $70.5K |
| **Liquidity** | $663.5K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 2y |
| **Top-10 Holders** | 16.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 73 buys / 62 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x6d6391b9bd02eefa00fa711fb1cb828a6471d283)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ski-mask-dog-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*
