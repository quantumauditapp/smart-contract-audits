---
token: Arbitrum Dog
ticker: MILES
network: arbitrum
risk_score: 36
status: medium
date: 2026-09-02
---

# Arbitrum Dog (MILES) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 36/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/arbitrum-dog-arb)

---

## Audit Summary

The OdysToken contract implements an ERC-20-like token with custom anti-whale and anti-bot mechanisms during a restricted launch period. The contract utilizes immutable variables for critical parameters and employs a factory pattern for initial setup and access control. While the core ERC-20 functionality is standard, the anti-bot/anti-whale logic contains significant bypasses for the liquidity pool and an initial buy recipient, which could undermine the intended launch strategy. Additionally, an unchecked arithmetic operation for balance increments poses a minor risk.

> **Final Recommendation:** It is crucial to address the identified bypasses in the anti-bot/anti-whale mechanisms to ensure the intended launch strategy and fair distribution are maintained. Specifically, re-evaluate the exemption logic for the `liquidityPool` and `initialBuyRecipient` to prevent unintended circumvention of transaction and wallet size limits. Additionally, remove the `unchecked` block for balance increments to enhance safety against potential, albeit unlikely, overflows. Thorough testing of the revised restriction logic is recommended before deployment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates good adherence to ERC-20 standards for basic token operations (7.2 Code Security). Key parameters like `factory`, `launchTime`, and restriction settings are correctly set as… |
| **Governance / Economics** | 2/10 | High | The contract incorporates anti-whale and anti-bot mechanisms (`maxWalletBps`, `restrictionSeconds`) designed to control token distribution during the initial launch phase (7.4 Economic). These… |
| **Upgrades** | 6/10 | Medium | The OdysToken contract is not designed with upgradeability features, meaning its logic cannot be modified after deployment (7.7 Upgrades). This eliminates risks associated with proxy patterns, such… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Initial Buy Recipient Bypasses All Restrictions  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initialBuyRecipient` address is included in the `_exempt` list, which means it is not subject to `MaxWalletExceeded` or `MaxTxExceeded` checks during the restricted period. This allows the designated recipient to accumulate an unlimited amount of tokens and transfer any amount in a single transaction, potentially enabling a large holder to bypass anti-whale measures or distribute tokens without limits, which could be exploited for market manipulation or an unfair advantage.

**Recommendation:** Clarify the intended role and necessity of `initialBuyRecipient` being fully exempt from all restrictions. If its purpose is for initial distribution, consider if it truly needs to bypass *all* restrictions. If not, remove it from the `_exempt` list or implement specific, limited exemptions that align with its intended function without compromising the anti-whale mechanism.


### `M-02` — Liquidity Pool Bypass of Max Transaction Limit  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_move` function's anti-bot/anti-whale logic exempts the `liquidityPool` from the `MaxTxExceeded` check when it is the `from` address. This means that during the restricted period, any amount of tokens can be transferred from the liquidity pool to a non-exempt address in a single transaction. This directly bypasses the intended `maxTx` limit, allowing bots or large buyers to acquire an unlimited amount of tokens from the pool in one go.

**Recommendation:** Re-evaluate the exemption logic for `liquidityPool` when it acts as the sender. Consider applying `MaxTxExceeded` checks for transfers *from* the liquidity pool *to* non-exempt addresses. This may require a more granular exemption mechanism or a specific handler for liquidity pool interactions to ensure the anti-bot measures are effective.


### `L-01` — Unchecked Arithmetic for Balance Increment  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `balanceOf[to] += value;` operation within the `_move` function is placed inside an `unchecked` block. While an overflow of `uint256` is highly unlikely in practical scenarios for token balances, if `balanceOf[to]` were to be near `type(uint256).max`, adding `value` could cause a wraparound, resulting in an incorrect and significantly lower balance for the recipient.

**Recommendation:** Remove the `unchecked` block around `balanceOf[to] += value;`. Solidity 0.8+ provides default checked arithmetic, which would cause a revert on overflow, preventing incorrect state and ensuring balance integrity. The performance gain from `unchecked` in this context is negligible compared to the potential risk.


### `I-01` — Precision Loss in BPS Calculations  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `maxWallet()` and `maxTx()` functions use integer division for calculations involving `BPS` (basis points), specifically `(totalSupply * maxWalletBps) / BPS`. Integer division truncates any fractional remainders, which can lead to minor precision loss in the calculated maximum wallet and transaction sizes.

**Recommendation:** This is a common and generally accepted pattern for basis point calculations in Solidity. No direct action is required unless exact fractional precision is a critical requirement for the token's economic model, in which case a fixed-point math library would be necessary (which adds complexity). Document this behavior if not already clear to stakeholders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6bea...2ca7`](https://arbiscan.io/address/0x6beadfcc25f6bc71c158a4bff85bf2f1746d2ca7) |
| **Network** | Arbitrum |
| **Price** | $0.00006464 |
| **24h Volume** | $23.3K |
| **Liquidity** | $29.9K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 13d |
| **Top-10 Holders** | 47.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 204 buys / 205 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0x06f2d9e061dfc85561595e79022531ce099d1501)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/arbitrum-dog-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-02*
