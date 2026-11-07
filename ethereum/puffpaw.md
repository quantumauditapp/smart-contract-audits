---
token: Puffpaw
ticker: VAPE
network: ethereum
risk_score: 64
status: medium
date: 2026-11-07
---

# Puffpaw (VAPE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 64/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/puffpaw-eth)

---

## Audit Summary

The contract at the provided address is not verified on Etherscan, preventing a direct security audit of the source code. The project utilizes a multisig ownership structure (2-of-3), which provides a layer of operational security but does not mitigate risks associated with hidden malicious logic or backdoors in the bytecode. Investors should exercise extreme caution as the lack of transparency prevents verification of tax mechanisms, minting capabilities, or liquidity safety.

> **Final Recommendation:** Do not interact with this contract until the source code is verified on a block explorer. Verify the contract's logic for hidden 'honeypot' features, such as transfer restrictions or excessive tax functions, before committing any capital. 

Monitor the multisig owner address for suspicious activity. If the project claims to be legitimate, demand that the developers verify the source code on Etherscan to allow for a comprehensive security review.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture and 7.2 Code Security cannot be assessed due to the lack of verified source code. 7.3 Access Control relies on a multisig, which is a positive signal compared to a single EOA.… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance parameters are entirely hidden from the user. The 2-of-3 multisig provides a basic governance framework, but the lack of public documentation on tokenomics creates… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades status is unknown as the contract is not verified. It is impossible to determine if the contract is a proxy or if it contains immutable logic. Users should assume the highest risk… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 2 Medium · ⚪ 5 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer, making it impossible to audit for malicious functions or vulnerabilities.

**Recommendation:** Verify the contract source code on Etherscan immediately.


### `H-01` — Lack of Transparency  *(Severity: High · Status: Unresolved)*

Investors cannot verify tokenomics, tax logic, or ownership privileges, leading to high risk of rug-pull or hidden backdoors.

**Recommendation:** Publish documentation and verified code to establish trust.


### `M-01` — Unverified Upgradeability  *(Severity: Medium · Status: Unresolved)*

Without source code, it is impossible to confirm if the contract is immutable or if the owner can upgrade the logic at any time.

**Recommendation:** Confirm if the contract is a proxy and disclose the implementation address.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a contract, 0x59d7…c7fb — holds 99.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 2.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 0.0% in wallets, 97.2% in other contracts. 48 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

48 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $68K (DexScreener, all pools). 24h trading volume $52K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: a 2-of-3 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $68K of DEX liquidity across 3 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3861...55ae`](https://etherscan.io/address/0x3861ad7a4fde897c0eb5f6d27d77b5a7d29c55ae) |
| **Network** | Ethereum |
| **Price** | $0.2889 |
| **24h Volume** | $51.9K |
| **Liquidity** | $68.2K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 18h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 167 buys / 38 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x8128aea429c73147d890b8cba97cd945b4327dec)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/puffpaw-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
