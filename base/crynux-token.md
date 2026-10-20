---
token: Crynux Token
ticker: CNX
network: base
risk_score: 87
status: critical
date: 2026-10-01
---

# Crynux Token (CNX) — Smart Contract Security Analysis | Base

> **Risk Score: 87/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/crynux-token-base)

---

## Audit Summary

The OptimismMintableERC20 contract functions as a standard ERC-20 token with a specific minting capability. A key finding is that a designated 'bridge' address has the power to mint new tokens, which can increase the total supply and dilute existing token holders. This introduces a centralized point of control over the token's supply, which is a common pattern for cross-chain tokens but requires careful consideration of the bridge's security.

> **Final Recommendation:** Token holders should be aware that the 'bridge' address has the ability to mint new tokens, which can increase the total supply and potentially dilute the value of existing holdings. It is crucial to understand the operational security and governance mechanisms surrounding the 'bridge' controller. Ensure transparency and robust security practices are in place for the entity controlling the bridge to mitigate risks associated with this centralized minting power.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The OptimismMintableERC20 contract implements the ERC-20 standard, providing core functionalities like `transfer`, `balanceOf`, and `approve` (7.1 Architecture). The contract includes a `mint`… |
| **Governance / Economics** | 1/10 | High | The economic model of this token is directly impacted by the `mint` function, which allows the 'bridge' to increase the total supply (7.4 Economic). This capability, while potentially necessary for… |
| **Upgrades** | 2/10 | High | The contract is not designed as an upgradeable proxy (7.7 Upgrades), meaning its logic cannot be modified after deployment. This reduces the risk of future logic changes introducing new… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 63.6% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 3 Informational_

### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 91.3% of supply. What remains: 20.6% in wallets, 70.7% in other contracts. The deployer/owner wallet itself holds 23.0%. A holder that also controls the contract can sell into its own liquidity. 486 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `CP-01` — A privileged address can mint new tokens  *(Severity: Medium · Status: Unresolved)*

A privileged function increases the total supply, diluting every holder. Functions: mint(address,uint256). Restricted to: bridge.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 34.9% is held, unlocked, by the token's owner/deployer (0x1b4f…bd89) — they can pull that liquidity at any moment. This is the rug-pull path. 65.1% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a contract, 0x3b46…0361 — holds 63.6% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

486 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $89K (DexScreener, all pools). 24h trading volume $31K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $89K of DEX liquidity across 3 pools. Launch: 98 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9557...9396`](https://basescan.org/address/0x9557dd9e241bc9636732623b672b4090af519396) |
| **Network** | Base |
| **Price** | $0.002528 |
| **24h Volume** | $31.4K |
| **Liquidity** | $88.8K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 3mo |
| **Top-10 Holders** | 91.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 71 buys / 73 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x2b1e35f39734e895a40a355862ebeb4af161dce321f15a4c22e632f848f8cf72)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/crynux-token-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-01*
