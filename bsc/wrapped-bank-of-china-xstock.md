---
token: Wrapped Bank Of China xStock
ticker: WBANKCX
network: bsc
risk_score: 44
status: medium
date: 2026-10-22
---

# Wrapped Bank Of China xStock (WBANKCX) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 44/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wrapped-bank-of-china-xstock-bsc)

---

## Audit Summary

The WrappedBackedToken implementation utilizes a standard ERC-4626 vault architecture with administrative controls for pausing and metadata management. The protocol relies on a multisig-controlled proxy pattern, ensuring robust upgradeability and ownership management. While the architecture is sound, the presence of a centralized pause mechanism introduces a dependency on the pauser role.

> **Final Recommendation:** The protocol demonstrates a strong security posture. We recommend implementing a timelock controller for the 'setPause' and 'setPauser' functions to prevent immediate, unauthorized disruption of token transfers. Additionally, ensure that the multisig signers maintain geographically and operationally distinct keys to maximize the effectiveness of the 2-of-3 threshold.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The architecture follows industry-standard ERC-4626 and ERC-20 patterns (7.1 Architecture). Code security is high due to the use of audited OpenZeppelin libraries (7.2 Code Security). External… |
| **Governance / Economics** | 3/10 | High | Governance is managed via a 2-of-3 multisig, providing a balance between security and operational agility (7.5 Governance). Economic risks are mitigated by the vault structure, though the pause… |
| **Upgrades** | 1/10 | High | The contract uses a Transparent Proxy pattern with a dedicated ProxyAdmin (7.7 Upgrades). This setup allows for secure, controlled updates to the implementation logic. The multisig ownership of the… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 2-of-3 |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.6% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-04` — Centralized Pause Control  *(Severity: Medium · Status: Unresolved)*

The 'setPause' function allows a designated 'pauser' address to halt all token transfers globally. This creates a centralized point of failure where a single compromised or malicious address can freeze user assets.

**Recommendation:** Implement a timelock mechanism for the pause functionality or transition the 'pauser' role to a decentralized governance contract to prevent unilateral action.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 3 address(es) other than the owner/deployer. One of them — a wallet, 0x8145…0992 — holds 99.6% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 99.0% of supply. Of that, 92.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.2% in wallets, 6.3% in other contracts. 815 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

815 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $714K (DexScreener, all pools). 24h trading volume $1.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Yield vault share  *(Severity: Informational · Status: Acknowledged)*

A share in a vault (ERC-4626) that holds another token and grows with the vault's yield. Its risk is the vault's strategy and its admin. The class itself adds no points; the contract and market facts decide the score. Basis: ERC-4626 vault functions in its code. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 2-of-3 multisig. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $714K of DEX liquidity across 30 pools. Launch: under a day of market history.

**Recommendation:** Check what the vault does with deposits and who can change its strategy.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xdd51...a285`](https://bscscan.com/address/0xdd5126d49b4c1e075c5b4249e289f1a00cc0a285) |
| **Network** | BNB Chain |
| **Price** | $0.7596 |
| **24h Volume** | $1.64M |
| **Liquidity** | $709.1K |
| **Volume / Liquidity** | 2.3× |
| **Token Age** | 15h |
| **Top-10 Holders** | 99.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 10099 buys / 9924 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x176d37b3fabc1c127d6fb0443441a7d8adc7d230)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wrapped-bank-of-china-xstock-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
