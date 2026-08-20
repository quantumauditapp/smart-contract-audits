---
token: PancakeSwap
ticker: CAKE
network: ethereum
risk_score: 89
status: critical
date: 2026-08-20
---

# PancakeSwap (CAKE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 89/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pancakeswap-eth)

---

## Audit Summary

The CakeOFT contract implements an Omnichain Fungible Token (OFT) with LayerZero integration, featuring daily transfer caps and a whitelist mechanism. The audit identified a critical inconsistency in token decimals, which could lead to severe miscalculations or loss of funds. Additionally, centralized control and the lack of a general emergency withdrawal function for accidentally sent ERC-20 tokens were noted.

> **Final Recommendation:** Immediately address the critical inconsistency in token decimals to prevent potential miscalculations and loss of funds. Review the access control strategy for the `onlyOwner` role, especially concerning the whitelist, and ensure robust security measures are in place for the owner's private keys or multisig setup. Consider implementing a general emergency withdrawal function for accidentally sent ERC-20 tokens to enhance operational safety.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract leverages LayerZero for omnichain functionality and OpenZeppelin's Pausable for operational control (7.1 Architecture, 7.2 Code Security). It implements daily inbound and outbound… |
| **Governance / Economics** | 1/10 | High | The contract's economic model incorporates daily transfer caps to mitigate risks associated with cross-chain token movements (7.4 Economic). Control over these caps, as well as pausing and whitelist… |
| **Upgrades** | 3/10 | High | The provided contract is not designed as an upgradeable proxy (7.7 Upgrades). Therefore, there are no specific upgrade-related risks inherent to this contract's architecture. Any future changes would… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.1% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium_

### `C-01` — Inconsistent Token Decimals  *(Severity: Critical · Status: Unresolved)*

The `CakeOFT` contract's `decimals()` function explicitly overrides the inherited `ERC20.decimals()` to return `18`. However, in its constructor, it initializes the `OFTWithFee` (which inherits from `ERC20`) with `8` decimals: `OFTWithFee("PancakeSwap Token", "Cake", 8, _lzEndpoint)`. This creates a severe inconsistency where the token internally operates with 8 decimals (e.g., for LayerZero `_amountLD` calculations) but externally reports 18 decimals. This discrepancy can lead to incorrect token amounts being transferred, displayed, or accounted for in external systems, potentially resulting in significant financial loss or protocol malfunction.

**Recommendation:** Ensure consistency in token decimals. Either initialize `OFTWithFee` with 18 decimals in the constructor and remove the `decimals()` override, or ensure all internal and external interactions correctly handle the 8-decimal representation. The most straightforward solution is to align the constructor parameter with the overridden `decimals()` function.


### `H-01` — Centralized Control and Whitelist Bypass Risk  *(Severity: High · Status: Unresolved)*

The `onlyOwner` role holds significant power, including the ability to pause/unpause the contract, set inbound/outbound transfer caps, and manage the whitelist. The whitelist allows designated addresses to bypass the daily transfer caps, which are a critical security feature designed to limit potential losses during bridge exploits. If the `onlyOwner` key (or multisig) is compromised, or if a whitelisted address is compromised, an attacker could bypass the caps and drain funds or cause significant disruption.

**Recommendation:** Implement robust security measures for the `onlyOwner` role, such as a strong multisig with a high threshold. Regularly review and audit whitelisted addresses. Consider implementing time-locks or multi-signature approvals for critical administrative actions like setting caps to zero or adding/removing addresses from the whitelist, to introduce a delay and allow for community oversight or emergency intervention.


### `M-01` — Lack of General Emergency Withdrawal for ERC-20 Tokens  *(Severity: Medium · Status: Unresolved)*

The contract is an ERC-20 token itself, but it does not include a general function to recover other ERC-20 tokens that might be accidentally sent to its address. While the contract is primarily for its native token, receiving other tokens by mistake is a common operational risk. Without a dedicated recovery mechanism, such tokens would be permanently locked in the contract.

**Recommendation:** Implement a `recoverERC20(address tokenAddress, uint256 amount)` function, restricted to the `onlyOwner` role. This function would allow the owner to retrieve any ERC-20 tokens accidentally sent to the contract, preventing their permanent loss. Ensure this function cannot be used to drain the contract's native token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1526...c898`](https://etherscan.io/address/0x152649ea73beab28c5b49b26eb48f7ead6d4c898) |
| **Network** | Ethereum |
| **Price** | $1.6300 |
| **24h Volume** | $139.9K |
| **Liquidity** | $167.5K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 3y |
| **Top-10 Holders** | 57.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 76 buys / 94 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x517f451b0a9e1b87dc0ae98a05ee033c3310f046)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pancakeswap-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-20*
