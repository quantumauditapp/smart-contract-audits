---
token: Decentrawood
ticker: DEOD
network: bsc
risk_score: 42
status: medium
date: 2026-08-08
---

# Decentrawood (DEOD) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 42/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/decentrawood-bsc)

---

## Audit Summary

The Decentrawood contract implements a standard ERC-20 token with burnable functionality, leveraging well-audited OpenZeppelin Contracts v5.5.0. The contract is simple, with a fixed total supply minted to a specified recipient during deployment. No complex logic, governance mechanisms, or upgradeability features are present, contributing to a low overall risk profile. Key operational considerations include the immutability of token parameters and the critical importance of the initial recipient address.

> **Final Recommendation:** It is recommended to thoroughly verify the deployment parameters, especially the `recipient` address in the constructor, to prevent the loss of the initial token supply. Given the contract's immutability, ensure that the fixed token supply and lack of administrative control align with the long-term vision for the Decentrawood project. Consider a multi-signature wallet for the initial recipient if the tokens are intended for a community or treasury, to enhance security and decentralization of control over the initial supply.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical architecture (7.1) is straightforward, implementing a standard ERC-20 token. Code security (7.2) is robust due to the exclusive reliance on OpenZeppelin Contracts v5.5.0, which are… |
| **Governance / Economics** | 3/10 | High | The economic model (7.4) for the Decentrawood token is simple: a fixed supply is minted at deployment, and the token is burnable. There are no complex tokenomics, staking, or lending mechanisms… |
| **Upgrades** | 5/10 | Medium | The Decentrawood contract is not designed to be upgradeable (7.7). It is deployed as an immutable contract, meaning its logic cannot be changed after deployment. This eliminates risks associated with… |

## Security Findings

_🟢 1 Low · ⚪ 3 Informational_

### `L-01` — Critical Constructor Parameter for Initial Supply  *(Severity: Low · Status: Unresolved)*

The entire initial token supply (2 billion DEOD tokens) is minted to a single `recipient` address specified in the constructor. If this address is incorrectly provided during deployment (e.g., a typo, an unowned address, or a blackholed address), the entire token supply could become permanently inaccessible or lost. This represents a critical operational risk during deployment (7.8 Operations).

**Recommendation:** Ensure rigorous verification of the `recipient` address before deployment. Consider using a multi-signature wallet as the recipient to enhance security and decentralization of control over the initial token supply, mitigating the risk of a single point of failure.


### `I-01` — Reliance on Standard OpenZeppelin Libraries  *(Severity: Informational · Status: Unresolved)*

The `Decentrawood` contract extensively utilizes well-audited and battle-tested OpenZeppelin Contracts (ERC20 and ERC20Burnable, v5.5.0). This significantly reduces the likelihood of common vulnerabilities associated with custom token implementations, such as reentrancy, integer overflows/underflows, or incorrect ERC-20 standard adherence. This approach enhances the overall security posture of the contract (7.2 Code Security).

**Recommendation:** No action required. This is a strength of the implementation. Continue to monitor OpenZeppelin updates and security advisories for any potential upstream issues.


### `I-02` — Fixed Token Supply and Immutability of Parameters  *(Severity: Informational · Status: Unresolved)*

The `Decentrawood` token has a fixed total supply of 2 billion tokens, minted exclusively during contract deployment. The token's name ("Decentrawood") and symbol ("Deod") are also set immutably in the constructor. There are no functions to mint additional tokens, modify the total supply (beyond user-initiated burning), or change the token's metadata post-deployment. This design choice ensures predictable tokenomics (7.4 Economic) but limits future flexibility.

**Recommendation:** Ensure that the project's long-term vision and tokenomics model are fully compatible with an immutable, fixed-supply token. If future adjustments to supply or metadata are ever anticipated, a different contract design or upgradeability pattern would be required.


### `I-03` — Absence of Administrative Roles and Access Control  *(Severity: Informational · Status: Unresolved)*

The `Decentrawood` contract does not implement any administrative roles, such as `Ownable` or `AccessControl` (7.3 Access Control). This means there is no single entity or group with special permissions to pause transfers, blacklist addresses, upgrade the contract, or modify any operational parameters post-deployment. This design aligns with a fully decentralized and immutable token, but it also means no emergency intervention capabilities are available.

**Recommendation:** Confirm that the absence of administrative control aligns with the project's decentralization goals and risk tolerance. If any form of administrative control (e.g., pausing in emergencies, future feature additions) is desired, it would require a re-design of the contract to include appropriate access control mechanisms.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3510...683e`](https://bscscan.com/address/0x3510fbbc13090f991ffa523527113a166161683e) |
| **Network** | BNB Chain |
| **Price** | $0.0228 |
| **24h Volume** | $55.7K |
| **Liquidity** | $71.5K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 6mo |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 533 buys / 174 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x185d73ec966d464a40372cd7e737bb68b0b95f1f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/decentrawood-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-08*
