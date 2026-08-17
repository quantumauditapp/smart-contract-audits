---
token: Rekt
ticker: REKT
network: ethereum
risk_score: 13
status: low
date: 2026-08-17
---

# Rekt (REKT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 13/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/rekt-eth)

---

## Audit Summary

The Rekt token is a standard ERC-20 token utilizing audited OpenZeppelin libraries. It features burnable, pausable, and permit functionalities. A significant portion of the token supply was minted to a single address during deployment, leading to high centralization. The contract is not upgradeable, and ownership has been renounced, making the token unpausable.

> **Final Recommendation:** Given the high centralization of token supply, it is crucial to transparently communicate the distribution strategy and the role of the address holding the majority of tokens. For long-term project health, consider a more decentralized distribution mechanism if future iterations are planned. The renouncement of ownership makes the token unpausable; ensure this is an intentional design choice, as it removes an emergency stop mechanism.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The Rekt token contract (7.1 Architecture, 7.2 Code Security) is built upon well-audited OpenZeppelin ERC20, Ownable, Burnable, Pausable, and Permit libraries, significantly reducing the likelihood… |
| **Governance / Economics** | 6/10 | Medium | The economic model (7.4 Economic) presents a high centralization risk due to the initial minting of 420,690,000,000,000 tokens (420.69 quadrillion) to a single address… |
| **Upgrades** | 9/10 | Low | The Rekt token contract is not designed with upgradeability features (7.7 Upgrades). This means its logic is immutable post-deployment, preventing any future modifications or bug fixes. While this… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Token Supply  *(Severity: High · Status: Unresolved)*

During contract deployment, a substantial amount of 420,690,000,000,000 tokens (420.69 quadrillion) was minted to a single address (0x424De83E135d0BE9a4b6b1268b04BCD4D92F7C98). This concentration of nearly the entire token supply in one address creates a single point of control, enabling potential market manipulation, rug pulls, or significant influence over any DeFi protocols integrating this token. This poses a severe economic risk to other token holders and the overall ecosystem.

**Recommendation:** For future token deployments, consider implementing a more decentralized initial distribution strategy. This could involve vesting schedules, fair launch mechanisms, or distributing tokens across multiple addresses controlled by different entities to mitigate the risk associated with a single point of failure and control.


### `M-01` — Unpausable Token After Ownership Renouncement  *(Severity: Medium · Status: Unresolved)*

The contract inherits `ERC20Pausable` and includes `pause()` and `unpause()` functions, which are restricted to the `onlyOwner` modifier. However, the provided prefill indicates that ownership has been renounced. While renouncing ownership removes the centralization risk of an owner arbitrarily pausing transfers, it also renders the token permanently unpausable. This means that in the event of a critical vulnerability in an integrated DeFi protocol or a severe market exploit, there is no mechanism to halt token transfers to prevent further damage.

**Recommendation:** Acknowledge the trade-off between decentralization (no owner to pause) and emergency response capability (no ability to pause). If an emergency pause mechanism is deemed necessary for future versions or similar projects, consider alternative decentralized governance-controlled pause mechanisms (e.g., multi-sig or DAO-controlled) rather than relying solely on `Ownable`.


### `L-01` — Immutability of Core Logic  *(Severity: Low · Status: Unresolved)*

The Rekt token contract is deployed without any upgradeability pattern (e.g., proxy contracts). This design choice makes the contract's logic immutable once deployed. While immutability provides certainty and reduces upgrade-related risks, it also means that any bugs discovered post-deployment cannot be fixed, and new features or protocol adjustments cannot be implemented without deploying an entirely new token contract.

**Recommendation:** Ensure that the current contract logic is thoroughly tested and deemed final, as no changes can be made. For projects requiring flexibility or long-term maintenance, consider implementing an upgradeable contract pattern in future iterations, along with robust upgrade safety procedures.


### `I-01` — Reliance on OpenZeppelin Libraries  *(Severity: Informational · Status: Unresolved)*

The Rekt token contract extensively utilizes well-regarded and audited OpenZeppelin contracts (ERC20, Ownable, ERC20Burnable, ERC20Pausable, ERC20Permit). This significantly enhances the baseline security of the contract by leveraging battle-tested code. However, the security of the Rekt token is inherently dependent on the continued security and correct implementation of these external libraries.

**Recommendation:** Continue to monitor OpenZeppelin's security advisories and updates. While OpenZeppelin contracts are highly secure, any newly discovered vulnerabilities in their libraries could potentially affect dependent contracts. Ensure that the specific versions used are up-to-date and free from known issues.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xdd3b...6686`](https://etherscan.io/address/0xdd3b11ef34cd511a2da159034a05fcb94d806686) |
| **Network** | Ethereum |
| **Price** | $0.0000001 |
| **24h Volume** | $71.0K |
| **Liquidity** | $937.1K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 45.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 63 buys / 70 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xf12533a96712133d9bb97c24de5bcf52f48851bd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/rekt-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-17*
