---
token: World of Dypians
ticker: WOD
network: bsc
risk_score: 10
status: low
date: 2026-09-03
---

# World of Dypians (WOD) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 10/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/world-of-dypians-bsc)

---

## Audit Summary

The WorldOfDypians token contract is a standard ERC-20 implementation, inheriting from well-audited OpenZeppelin contracts. It features a fixed maximum supply, with all tokens minted to a designated lock address during deployment. The contract exhibits robust code quality and adheres to common security practices, with no critical or high-severity vulnerabilities identified. Minor findings relate to design choices regarding token distribution and immutability.

> **Final Recommendation:** It is recommended to ensure robust security and operational procedures for the `tokenLockAddress`, as it holds the entire initial token supply. Implement multi-signature control and secure key management practices for this address to mitigate risks associated with centralized control. Additionally, consider documenting the intended release schedule or mechanism for tokens held at the `tokenLockAddress` to provide transparency to the community.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The technical implementation of the WorldOfDypians token is based on battle-tested OpenZeppelin ERC20 and Ownable contracts, ensuring a high standard of code security (7.2 Code Security). The use of… |
| **Governance / Economics** | 6/10 | Medium | The contract utilizes the Ownable pattern for administrative control, allowing the owner to transfer or renounce ownership (7.3 Access Control). However, the owner has no control over the token… |
| **Upgrades** | 9/10 | Low | The WorldOfDypians contract is not designed as an upgradeable proxy. It is a standard, non-upgradeable implementation, meaning its logic cannot be modified after deployment (7.7 Upgrades). Any future… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟢 1 Low · ⚪ 2 Informational_

### `L-01` — Centralized Control of Initial Supply  *(Severity: Low · Status: Unresolved)*

The entire `MAX_SUPPLY` of WorldOfDypians tokens is minted to a single `tokenLockAddress` (0x3589Fcb5bEE84DbB4DA4f987Ed84a45F012d3890) during contract deployment. This design choice centralizes control over the initial token distribution to the entity managing this specific address. Any compromise, mismanagement, or single point of failure associated with the `tokenLockAddress` could significantly impact the entire token supply and its intended distribution (7.3 Access Control, 7.4 Economic, 7.6 External).

**Recommendation:** Implement robust security measures for the `tokenLockAddress`, such as a multi-signature wallet or a time-locked contract, to distribute control and reduce the risk of a single point of failure. Clearly communicate the purpose and management of this address to stakeholders.


### `I-01` — Immutable Token Supply  *(Severity: Informational · Status: Unresolved)*

The WorldOfDypians token contract implements a fixed token supply model. After the initial minting of `MAX_SUPPLY` tokens to the `tokenLockAddress` in the constructor, there are no public or internal functions available to mint additional tokens or burn existing ones. This design makes the total token supply immutable, preventing any future inflation or deflation through contract-level operations (7.4 Economic).

**Recommendation:** No action is required if a fixed supply is the intended economic model. Ensure this design choice is clearly communicated in the project's documentation and whitepaper.


### `I-02` — Hardcoded `tokenLockAddress`  *(Severity: Informational · Status: Unresolved)*

The `tokenLockAddress` (0x3589Fcb5bEE84DbB4DA4f987Ed84a45F012d3890) is defined as a `public constant` within the contract. While this ensures the address cannot be changed after deployment, it also introduces inflexibility. If the intended recipient or the strategy for managing the initial token supply needs to change in the future, it would necessitate deploying an entirely new contract (7.1 Architecture).

**Recommendation:** No action is required if immutability of the lock address is the intended design. For future projects requiring flexibility, consider making such critical addresses configurable via constructor arguments or an owner-controlled setter function, if appropriate for the project's risk model.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb994...b0e8`](https://bscscan.com/address/0xb994882a1b9bd98a71dd6ea5f61577c42848b0e8) |
| **Network** | BNB Chain |
| **Price** | $0.003606 |
| **24h Volume** | $346.5K |
| **Liquidity** | $258.2K |
| **Volume / Liquidity** | 1.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 75.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2272 buys / 1955 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xcf39e58ed4decc9ef7bdb2f9335602dc22be99b4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/world-of-dypians-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-03*
