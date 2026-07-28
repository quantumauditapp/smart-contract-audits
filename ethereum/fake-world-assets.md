---
token: Fake World Assets
ticker: FWA
network: ethereum
risk_score: 72
status: critical
date: 2026-07-28
---

# Fake World Assets (FWA) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 72/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fake-world-assets-eth)

---

## Audit Summary

The FWAToken contract implements a fixed-supply ERC20 token with custom transfer restrictions and a Uniswap v4 integrated buyback mechanism. While leveraging battle-tested libraries like Solady and incorporating reentrancy protection, a critical vulnerability was identified in the Uniswap v4 callback logic. This flaw, involving an integer underflow during an allowance grant, could lead to the unauthorized draining of the contract's FWAToken balance. Additionally, the contract exhibits centralized owner privileges and a minor denial-of-service vector for its buyback function.

> **Final Recommendation:** Address the critical integer underflow vulnerability in the `uniswapV4UnlockCallback` immediately to prevent potential draining of FWAToken. Thoroughly review all interactions with external Uniswap v4 components, especially regarding token transfers and allowances, to ensure they align with the intended security model. Consider implementing a multi-signature wallet for the owner address to mitigate risks associated with centralized control over critical parameters and explore progressive decentralization of governance for key economic settings as the protocol matures.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract demonstrates good architectural practices (7.1) by using immutable variables for critical external dependencies and inheriting `ReentrancyGuard` for code security (7.2). Custom error… |
| **Governance / Economics** | 1/10 | High | The tokenomics (7.4) feature a fixed supply and a buyback mechanism designed to accrue value and distribute tokens, with configurable routing splits and a price limit to protect against extreme… |
| **Upgrades** | 4/10 | Medium | The FWAToken contract is not designed as an upgradeable proxy (7.7). Therefore, there are no direct upgrade safety concerns. Any changes to the contract logic would require a new deployment and… |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · 🟢 1 Low_

### `C-01` — Uniswap V4 Callback Integer Underflow Leads to Infinite Allowance  *(Severity: Critical · Status: Unresolved)*

The `uniswapV4UnlockCallback` function, invoked by the Uniswap v4 PoolManager during a swap, attempts to set an allowance for the `poolManager` to pull FWAToken from the contract. Specifically, `_approve(address(this), address(poolManager), uint256(delta.amount0))` is called. In the `buyback()` scenario, the contract is buying FWAToken (currency0) and selling ETH (currency1). This implies `delta.amount0` (the net change in FWAToken balance for the pool) will be a negative `int256` value, as the pool sends FWAToken to the contract. Casting a negative `int256` value to `uint256` results in an integer underflow, yielding a very large (effectively infinite) `uint256` value. This grants the `poo…

**Recommendation:** The `uniswapV4UnlockCallback` function's logic for setting allowances must be critically reviewed and corrected. For a buyback where FWAToken is received by the contract, no allowance should be granted to the `poolManager` for FWAToken. If an allowance is needed for other swap directions, ensure `delta.amount0` is correctly handled (e.g., only if positive and representing an outgoing token transfer) and that appropriate access control (`onlyHook`) is maintained. Consider removing the `_approve`…


### `M-01` — Extensive Centralized Owner Privileges  *(Severity: Medium · Status: Unresolved)*

The `Ownable` contract grants significant control to the owner address. The owner can: set `isDistributor` for any address, bypassing transfer restrictions; set the `pool` (IBuybackRouter) address, which receives a portion of bought FWAToken; set the `routeSplit` for depositors, purchasers, and burn, potentially manipulating token distribution; set `buybackSqrtPriceLimitX96`, influencing the buyback price; and approve any `spender` to transfer tokens from the contract using `_approve(address spender, uint256 amount)`. While common in early-stage projects, this centralization introduces a single point of failure and trust, where a compromised owner key could lead to significant financial los…

**Recommendation:** Consider implementing a multi-signature wallet (e.g., Gnosis Safe) for the owner address to reduce the risk of a single point of compromise. As the protocol matures, explore decentralizing control through a time-locked governance mechanism for critical parameters like the `pool` address and `routeSplit` to enhance trust and resilience.


### `L-01` — Buyback Function Susceptible to Minor Denial of Service  *(Severity: Low · Status: Unresolved)*

The `buyback()` function includes a rate-limiting mechanism (`block.number >= lastBuybackBlock + BUYBACK_DELAY_BLOCKS`). A malicious actor could repeatedly call `buyback()` with the minimum required ETH (`BUYBACK_INCREMENT` is 1 ETH) just after the `BUYBACK_DELAY_BLOCKS` period. This action would effectively reset `lastBuybackBlock`, preventing other users from executing larger or more impactful buybacks for the duration of the delay. While the cost of 1 ETH per call acts as a deterrent, it could still be used to disrupt buyback operations or create an unfavorable user experience.

**Recommendation:** Evaluate if the `BUYBACK_DELAY_BLOCKS` and `BUYBACK_INCREMENT` are appropriately balanced for the intended operational frequency and cost. Consider increasing the `BUYBACK_INCREMENT` or implementing a dynamic delay based on recent buyback activity or a minimum ETH amount for the caller to prevent trivial denial-of-service attempts.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa0df...c845`](https://etherscan.io/address/0xa0df17b5ac76ababa36e1450e2cbcd18a620c845) |
| **Network** | Ethereum |
| **Price** | $0.01385 |
| **24h Volume** | $2.16M |
| **Liquidity** | $785.1K |
| **Volume / Liquidity** | 2.8× |
| **Token Age** | 11d |
| **Top-10 Holders** | 55.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6081 buys / 6931 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x230ecd3c25b44af30db59c15f70df7794eb13f67a200f230b7400daa96fe804d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fake-world-assets-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-28*
