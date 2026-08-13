---
token: Koma Inu
ticker: KOMA
network: bsc
risk_score: 26
status: medium
date: 2026-08-13
---

# Koma Inu (KOMA) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 26/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/koma-inu-bsc)

---

## Audit Summary

The KOMA token contract is an ERC-20 compliant token with custom fee mechanisms, anti-bot features, and an auto-liquidity/marketing function. The contract utilizes the Ownable pattern for administrative control and includes reentrancy protection for its swap operations. Key findings include a high centralization risk due to an immutable marketing receiver, potential for unrecoverable ETH if external calls fail, and significant owner privileges regarding fee exemptions. The overall risk level is assessed as Medium.

> **Final Recommendation:** It is recommended to review and mitigate the identified centralization risks, particularly concerning the `marketing_receiver` address. Consider implementing a mechanism to update this address or distribute funds to multiple, more resilient destinations. Additionally, implement a recovery mechanism for ETH that might get stuck in the contract due to failed external calls to the marketing receiver. Carefully consider the implications of broad owner privileges, such as fee exemptions, and ensure robust operational procedures are in place for their use.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract demonstrates good code quality and utilizes Solidity 0.8.18, benefiting from built-in overflow/underflow checks. Reentrancy protection is implemented for the `swapAndLiquify` function… |
| **Governance / Economics** | 5/10 | Medium | The tokenomics include dynamic buy/sell fees and an initial high tax period, designed to manage early trading behavior (7.4 Economic). A significant centralization risk arises from the hardcoded and… |
| **Upgrades** | 10/10 | Low | The KOMA token contract is not designed with an upgrade mechanism (e.g., proxy pattern). Therefore, there are no upgrade-related risks (7.7 Upgrades). Any changes to the contract logic would require… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 71.0% — OnlyMoons Lock |
| **Top-1 Unlocked Holder** | 14.6% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralization Risk with Immutable Marketing Receiver  *(Severity: High · Status: Unresolved)*

The `marketing_receiver` address is hardcoded in the constructor and cannot be changed after deployment. This address acts as a single point of failure for all collected transaction fees. If this address were to be compromised or become inaccessible, all accumulated funds would be at risk, and the protocol's ability to utilize these funds for marketing or other purposes would be severely hindered. This impacts 7.5 Governance and 7.4 Economic.

**Recommendation:** Implement a function, callable only by the owner, to update the `marketing_receiver` address. Consider using a multi-signature wallet for the `marketing_receiver` to enhance security and decentralization, or a contract that allows for recovery/redirection of funds.


### `M-01` — Unrecoverable ETH on Marketing Receiver Call Failure  *(Severity: Medium · Status: Unresolved)*

In the `swapAndLiquify` function, if the `marketing_receiver.call{value: deltaBalance}("")` operation fails (e.g., due to the receiver being a contract that reverts on receiving ETH, or gas limits), the ETH remains in the KOMA contract. There is no mechanism for the owner or any other party to recover or redirect these stuck funds, leading to potential loss of value. This impacts 7.8 Operations.

**Recommendation:** Implement a recovery mechanism for stuck ETH. This could be an `onlyOwner` function to sweep any ETH balance from the contract to a designated address, or a more sophisticated retry/fallback mechanism within `swapAndLiquify`.


### `M-02` — Owner's Broad Power to Exempt Fees  *(Severity: Medium · Status: Unresolved)*

The `setisExempt` function allows the contract owner to exempt any address from transaction fees. While intended for legitimate purposes (e.g., exempting router addresses or specific contract interactions), this power is highly centralized. It could be abused to give preferential treatment to certain parties, allowing them to bypass fees for large transfers, potentially impacting the token's economic model and fairness. This impacts 7.3 Access Control and 7.4 Economic.

**Recommendation:** Consider implementing a more granular or time-bound fee exemption mechanism. If broad exemption is necessary, ensure robust off-chain governance and transparency around its usage. Document the intended use cases for fee exemptions clearly.


### `L-01` — Hardcoded External Contract Addresses  *(Severity: Low · Status: Unresolved)*

The PancakeSwap router and factory addresses are hardcoded in the constructor (`0x10ED43C718714eb63d5aA57B78B54704E256024E` and `0xcA143Ce32Fe78f1f7019d7d551a6402fC5350c73`). While this is common for single-chain deployments, it makes the contract non-portable to other EVM chains or future versions/upgrades of the router/factory without a complete redeployment. This impacts 7.6 External.

**Recommendation:** For future deployments or multi-chain considerations, consider making these addresses configurable via an `onlyOwner` function or through a constructor parameter that can be set during deployment. For this specific deployment, this is a minor concern given the BSC context.


### `I-01` — Initial High Taxes and Short Durations  *(Severity: Informational · Status: Unresolved)*

The contract implements `INITIAL_BUY_TAX` (30%) and `INITIAL_SELL_TAX` (30%) with relatively short durations (`BUY_TAX_DURATION` 15 seconds, `SELL_TAX_DURATION` 30 minutes). While these aggressive tax structures are often intended to deter bots and early price manipulation, they can also deter legitimate early participants and lead to significant price volatility during the initial trading phase. This impacts 7.4 Economic.

**Recommendation:** This is a design choice, but it's important for the project team to be aware of the potential impact on early adoption and market dynamics. Ensure clear communication to the community regarding these initial tax mechanics.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd5ea...3c19`](https://bscscan.com/address/0xd5eaaac47bd1993d661bc087e15dfb079a7f3c19) |
| **Network** | BNB Chain |
| **Price** | $0.01342 |
| **24h Volume** | $708.7K |
| **Liquidity** | $1.89M |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 1y |
| **Top-10 Holders** | 83.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2211 buys / 2156 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x0ec12db33551afba853b691b4edf49196ea0e99a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/koma-inu-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-13*
