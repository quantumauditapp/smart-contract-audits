---
token: SOON Token
ticker: SOON
network: bsc
risk_score: 42
status: medium
date: 2026-08-20
---

# SOON Token (SOON) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 42/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/soon-token-bsc)

---

## Audit Summary

The audit of the SoonTokenV2 contract, deployed as an upgradeable proxy, identified a robust architecture leveraging OpenZeppelin and LayerZero standards. Key features include inflationary minting and an EIP-3009 authorization mechanism. The primary risks stem from the high degree of centralized control over critical functions, particularly the blacklist and inflationary parameters, which are managed by a multisig owner. While the technical implementation is sound, these centralized powers introduce significant governance and operational risks.

> **Final Recommendation:** Strengthen access control mechanisms by considering a timelock for critical owner-controlled functions, especially those related to the blacklist and inflationary parameters, to provide a delay for review and reaction. Implement robust monitoring for the owner multisig and associated addresses to detect any suspicious activity. Ensure clear communication to token holders regarding the implications of the centralized blacklist and inflationary model.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract exhibits a well-structured architecture (7.1) using established OpenZeppelin and LayerZero upgradeable patterns, including `Initializable` and `OFTUpgradeable`. Code security (7.2) is… |
| **Governance / Economics** | 3/10 | High | The economic model (7.4) includes an inflationary minting mechanism with parameters (`inflationaryRatio`, `inflationaryMinter`, `inflationaryReceiver`) controlled by the owner. While the inflation… |
| **Upgrades** | 4/10 | Medium | The contract is designed for upgradeability (7.7) using the Transparent Upgradeable Proxy pattern and OpenZeppelin's `Initializable` base. The `initialize()` and `initializeV2()` functions correctly… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 3-of-5 |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 1 Informational_

### `H-01` — Centralized Blacklist Control  *(Severity: High · Status: Unresolved)*

The contract includes a blacklist functionality (`addToBlacklist`, `removeFromBlacklist`) controlled by the `onlyOwner` modifier. The `_update` function, which is called during token transfers, checks if both the sender and receiver are blacklisted. This grants the owner (a multisig) the power to arbitrarily prevent any account from transferring tokens, effectively freezing their assets. While the owner is a multisig, this level of centralized control over user funds is a significant risk (7.3, 7.4).

**Recommendation:** Consider implementing a decentralized governance mechanism for managing the blacklist, or at minimum, introduce a timelock for blacklist operations to allow for community oversight and reaction time. Clearly communicate the existence and implications of this centralized control to all token holders.


### `M-01` — Centralized Control of Inflationary Parameters  *(Severity: Medium · Status: Unresolved)*

The `inflationaryMinter`, `inflationaryReceiver`, and `inflationaryRatio` parameters, which dictate the token's inflationary supply mechanism, are all controlled by the `onlyOwner` address. If the owner's private keys or the multisig itself were compromised, an attacker could manipulate these parameters to mint an excessive amount of tokens to an arbitrary address, leading to severe token dilution and economic instability (7.3, 7.4, 7.8).

**Recommendation:** Implement a timelock for changes to critical inflationary parameters (`inflationaryMinter`, `inflationaryReceiver`, `inflationaryRatio`) to provide a delay before changes take effect. This allows for detection and potential intervention in case of malicious or erroneous updates. Consider a more decentralized approach for these roles in the future, if applicable.


### `I-01` — Use of Non-Upgradeable ECDSA Library  *(Severity: Informational · Status: Unresolved)*

The `EIP3009Upgradeable` contract imports `ECDSA` from `@openzeppelin/contracts/utils/cryptography/ECDSA.sol` instead of the upgradeable version, `ECDSAUpgradeable`. While `ECDSA` is a stateless library and its non-upgradeable version does not introduce direct state-related vulnerabilities in an upgradeable context, using the `Upgradeable` counterpart is generally considered a best practice for consistency and to avoid potential confusion in upgradeable contract development (7.2).

**Recommendation:** For consistency and adherence to upgradeable contract best practices, consider replacing `ECDSA` with `ECDSAUpgradeable` from `@openzeppelin/contracts-upgradeable/utils/cryptography/ECDSAUpgradeable.sol`.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb9e1...a721`](https://bscscan.com/address/0xb9e1fd5a02d3a33b25a14d661414e6ed6954a721) |
| **Network** | BNB Chain |
| **Price** | $0.2014 |
| **24h Volume** | $587.4K |
| **Liquidity** | $550.8K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 93.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2978 buys / 3450 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x0b2eb4332a15e5165477aad2c79721925920a383)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/soon-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-20*
