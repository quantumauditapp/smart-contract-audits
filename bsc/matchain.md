---
token: Matchain
ticker: MAT
network: bsc
risk_score: 68
status: high
date: 2026-10-15
---

# Matchain (MAT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 68/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/matchain-bsc)

---

## Audit Summary

This audit covers the HypERC20 token contract, an ERC-20 compliant token with cross-chain routing capabilities, deployed behind a TransparentUpgradeableProxy. The contract exhibits standard ERC-20 functionality and integrates with a mailbox system for interchain communication. Key findings include a medium-severity issue allowing a privileged 'mailbox' address to mint tokens, and two high-severity technical issues related to handling `msg.value` in a non-payable function and a state shadowing vulnerability. The contract owner is a multisig, enhancing control over administrative functions and upgrades.

> **Final Recommendation:** Prioritize resolving the high-severity technical issues, specifically the `msg.value` in non-payable function `_dispatch` and the state shadowing concern. Implement robust access controls and monitoring for the `mailbox` role, given its ability to mint new tokens, to prevent unauthorized supply inflation. Ensure all future upgrade proposals undergo thorough security audits before deployment to mitigate risks associated with upgradeability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The contract implements standard ERC-20 functionality and integrates cross-chain messaging via `TokenRouter` and `MailboxClient` (7.1 Architecture). However, two high-severity technical issues were… |
| **Governance / Economics** | 4/10 | Medium | The contract utilizes `OwnableUpgradeable` for administrative functions, with ownership held by a multisig (3/5 threshold), enhancing security for critical operations like `setDestinationGas` and… |
| **Upgrades** | 1/10 | High | The contract is deployed behind a `TransparentUpgradeableProxy`, allowing for future upgrades to fix bugs or add features without redeploying the entire system (7.7 Upgrades). The upgrade mechanism… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 3-of-5 |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 42.1% |
| **Top-3 Unlocked** | 61.7% |

## Security Findings

_🟠 2 High · 🟡 2 Medium · ⚪ 4 Informational_

### `CD-01` — Funds sent with cross-chain transfers might be lost due to a technical error.  *(Severity: High · Status: Unresolved)*

When you initiate a cross-chain transfer using functions like `transferRemote(uint32,bytes32,uint256)` or `transferRemote(uint32,bytes32,uint256,bytes,address)`, you might send Ether (ETH) along with your token transfer to cover gas or other costs. However, the internal `_dispatch` function, which processes these transfers, is not designed to receive Ether. This means any Ether sent with these transactions could be stuck in the contract and become inaccessible, effectively leading to a loss of funds.

**Recommendation:** The project team must immediately fix the `_dispatch` function to correctly handle or reject Ether sent with cross-chain transfers. Token holders should exercise caution when sending Ether with `transferRemote` functions until this issue is confirmed to be resolved.


### `CD-02` — A technical flaw could lead to unexpected behavior or vulnerabilities.  *(Severity: High · Status: Unresolved)*

The contract has a technical issue where a variable or function in a derived contract has the same name as one in a base contract, but they refer to different underlying storage or logic. This 'shadowing' can cause confusion, lead to unintended behavior, or even introduce security vulnerabilities if the contract's logic relies on the shadowed state in an unexpected way. This could potentially affect how the contract manages its internal state and operations.

**Recommendation:** The project team should address this state shadowing issue to ensure the contract's logic is clear, predictable, and secure. This typically involves renaming variables or functions to avoid conflicts and ensure that the correct state is always being accessed and modified.


### `CP-01` — The `mailbox` controller can create new tokens, potentially diluting your holdings.  *(Severity: Medium · Status: Unresolved)*

The contract allows a specific controller, referred to as the `mailbox`, to create new tokens out of thin air. Functions like `transferRemote(uint32,bytes32,uint256)`, `transferRemote(uint32,bytes32,uint256,bytes,address)`, and `handle(uint32,bytes32,bytes)` can increase the total supply of tokens. If this `mailbox` controller is compromised or misused, it could lead to an unlimited creation of tokens, reducing the value of every token you hold.

**Recommendation:** Token holders should be aware that the `mailbox` controller has significant power over the token supply. The project team should implement strict governance and security measures around the `mailbox` controller's private keys or access, potentially using a multi-signature wallet or a time-locked contract for these operations to add an extra layer of security.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 85.5% is held, unlocked, by 10 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 78% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 90.3% of supply. Of that, 0.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 19.2% in wallets, 70.4% in other contracts. 4,760 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Matchain (MAT), rank #3734. 4,760 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $132K (DexScreener, all pools). 24h trading volume $795K (CoinGecko, all markets, daily snapshot). 24h trading volume $550K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $3.27 on 2025-06-19; the price is now 98.0167% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Governance. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 3-of-5 multisig. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $132K of DEX liquidity across 5 pools. Launch: 484 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfe2d...bab0`](https://bscscan.com/address/0xfe2dd2d57a05f89438f3aec94eafa4070396bab0) |
| **Network** | BNB Chain |
| **Price** | $0.07235 |
| **24h Volume** | $435.3K |
| **Liquidity** | $102.5K |
| **Volume / Liquidity** | 4.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 90.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3113 buys / 3576 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x5eb4a369e7a446f6f24e8f3e8f27eec35197618f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/matchain-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-15*
