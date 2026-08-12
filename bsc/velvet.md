---
token: Velvet
ticker: VELVET
network: bsc
risk_score: 52
status: high
date: 2026-08-12
---

# Velvet (VELVET) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 52/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/velvet-bsc)

---

## Audit Summary

The VelvetToken contract implements a BEP20 token with additional features for controlled token transfers and a whitelist. The contract exhibits a high degree of centralization, with the owner possessing significant control over token supply through minting and the ability to manipulate transfer restrictions and whitelist addresses. While the core BEP20 implementation is robust, the custom access control logic introduces notable economic and operational risks.

> **Final Recommendation:** It is strongly recommended to review and potentially decentralize the extensive owner privileges, especially regarding token minting and transfer control. Consider implementing a multi-signature wallet for critical owner functions to mitigate the single point of failure risk. For the `setTransferAllowedTimestamp` function, simplify the logic or add comprehensive documentation to ensure clarity and prevent unintended use.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract leverages standard OpenZeppelin libraries for its BEP20 implementation, contributing to a solid foundation (7.2 Code Security). The custom `_beforeTokenTransfer` hook is correctly… |
| **Governance / Economics** | 5/10 | Medium | The contract grants the owner extensive centralized control, posing significant economic risks (7.4 Economic). The owner can mint up to 1 billion tokens, leading to potential inflation and dilution… |
| **Upgrades** | 5/10 | Medium | The VelvetToken contract is not designed with upgradeability features (7.7 Upgrades). It is deployed as a standard, non-proxy contract, meaning its logic cannot be modified post-deployment. This… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 15.5% |
| **Top-3 Unlocked** | 37.3% |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 1 Medium_

### `C-01` — Centralized Minting Capability  *(Severity: Critical · Status: Unresolved)*

The `owner` address has the ability to mint an arbitrary amount of tokens up to the predefined `_cap` (1 billion tokens) via the `mintTo` and `mint` functions. This centralized control over the token supply poses a significant economic risk, as it can lead to inflation, dilution of existing token holders, and potential market manipulation if abused. (7.4 Economic, 7.3 Access Control)

**Recommendation:** Implement a mechanism to restrict or remove the owner's minting capability after an initial distribution phase, or introduce a time-locked schedule for minting. If minting is necessary, consider a multi-signature wallet for its execution or a community governance vote.


### `H-01` — Owner Can Indefinitely Delay Token Transfers  *(Severity: High · Status: Unresolved)*

The `setTransferAllowedTimestamp` function contains logic that allows the owner to indefinitely postpone the `transferAllowedTimestamp`. Specifically, if `transferAllowedTimestamp` is in the future and `ETA` is 0, the owner can set `transferAllowedTimestamp` to any new future timestamp. This enables the owner to prevent token transfers for an arbitrary duration, impacting liquidity, user access, and potentially causing significant market uncertainty. (7.4 Economic, 7.3 Access Control)

**Recommendation:** Revise the `setTransferAllowedTimestamp` logic to prevent indefinite delays. Consider a fixed maximum delay, a one-time setting, or a mechanism that requires community consensus for changes to critical timelines. Ensure that any changes to this timestamp are clearly communicated to token holders.


### `H-02` — Whitelist Bypasses Transfer Restrictions  *(Severity: High · Status: Unresolved)*

The owner can add any address to the `whitelist` mapping using `addToWhitelist`. Whitelisted addresses are exempt from the `transferAllowedTimestamp` restriction, allowing them to transfer tokens even before the general transfer period begins. This creates a mechanism for preferential treatment, potential insider trading, or selective access, undermining the fairness and transparency of the token launch and transfer restrictions. (7.4 Economic, 7.3 Access Control)

**Recommendation:** Evaluate the necessity of the whitelist mechanism. If required, implement stricter controls, such as a time-bound whitelist, a public disclosure of whitelisted addresses, or a multi-signature approval process for adding/removing addresses. Clearly define the purpose and scope of the whitelist.


### `M-01` — Single Point of Failure (Owner Key)  *(Severity: Medium · Status: Unresolved)*

The contract relies heavily on a single `owner` address for critical operations, including minting, managing the whitelist, and setting transfer timestamps. If this owner's private key is compromised, an attacker would gain full control over these sensitive functions, leading to potential financial loss, denial of service, or manipulation of the token's economy. (7.8 Operations, 7.3 Access Control)

**Recommendation:** Implement a multi-signature wallet (e.g., Gnosis Safe) for the `owner` address to distribute control and reduce the risk associated with a single point of failure. Alternatively, consider a timelock mechanism for sensitive operations to provide a window for intervention in case of a compromise.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8b19...1488`](https://bscscan.com/address/0x8b194370825e37b33373e74a41009161808c1488) |
| **Network** | BNB Chain |
| **Price** | $0.5531 |
| **24h Volume** | $1.23M |
| **Liquidity** | $2.49M |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 1y |
| **Top-10 Holders** | 91.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 33635 buys / 35423 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x5d2913a8ea284e486000177852c87ea4d64d03d6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/velvet-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-12*
