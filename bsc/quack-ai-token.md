---
token: Quack AI Token
ticker: Q
network: bsc
risk_score: 51
status: high
date: 2026-07-27
---

# Quack AI Token (Q) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 51/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/quack-ai-token-bsc)

---

## Audit Summary

The PeerToken contract is an ERC-20 token with burnable and permit functionalities, extending OpenZeppelin's standard implementations. It introduces a dedicated 'minter' role, separate from the 'owner', to control token supply. The contract's primary security strength lies in its use of well-audited OpenZeppelin libraries and a Timelock for the owner role. However, the centralized and unlimited minting capability by the 'minter' poses a significant economic risk, as a compromise of this role could lead to arbitrary token inflation and devaluation.

> **Final Recommendation:** It is crucial to implement stringent security measures for the `minter` address, given its ability to arbitrarily inflate the token supply. Consider using a multi-signature wallet or a more sophisticated governance mechanism for the `minter` role to distribute control and reduce the single point of failure risk. Additionally, ensure the Timelock owner's private keys are secured with the highest possible standards.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical implementation of PeerToken is robust, leveraging battle-tested OpenZeppelin contracts for ERC-20, ERC-20Permit, ERC-20Burnable, and Ownable functionalities (7.2 Code Security). Custom… |
| **Governance / Economics** | 1/10 | High | The contract implements a robust access control system with distinct `owner` and `minter` roles (7.3 Access Control). The `owner` is a Timelock with a 48-hour delay, which significantly enhances… |
| **Upgrades** | 8/10 | Low | The PeerToken contract is not designed as an upgradeable proxy (7.7 Upgrades). This eliminates upgrade-related risks such as proxy implementation mismatches or storage collisions. However, it also… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · ⚪ 1 Informational_

### `H-01` — Centralized Unlimited Minting Authority  *(Severity: High · Status: Unresolved)*

The `PeerToken` contract grants an `onlyMinter` role the ability to mint an unlimited quantity of new tokens via the `mint(address _account, uint256 _amount)` function. While the `owner` (a Timelock) can change the `minter` address, the `minter` itself has unchecked power over the token supply. A compromise of the `minter`'s private key or a malicious `minter` could lead to arbitrary token inflation, severely devaluing existing tokens and impacting the protocol's economic stability (7.4 Economic, 7.3 Access Control).

**Recommendation:** Implement a more robust control mechanism for the `minter` role. Consider: 1) Using a multi-signature wallet for the `minter` address. 2) Implementing a minting cap (e.g., a maximum total supply or a rate limit for minting). 3) Introducing a time-locked minting approval process requiring multiple parties. 4) If unlimited minting is intended, ensure the `minter`'s operational security is paramount.


### `I-01` — Non-Upgradeable Contract  *(Severity: Informational · Status: Unresolved)*

The `PeerToken` contract is deployed directly and does not utilize a proxy pattern, meaning it is not upgradeable (7.7 Upgrades). This implies that its logic cannot be modified or updated after deployment. While this eliminates upgrade-related security risks, it also means that any future bug fixes, feature enhancements, or changes to the token's economic model would require deploying an entirely new contract and migrating users/liquidity.

**Recommendation:** This is an architectural decision. If future flexibility is desired, consider implementing an upgradeable proxy pattern (e.g., UUPS or Transparent Proxy) for future contracts. If immutability is the goal, ensure the current design is thoroughly reviewed and future-proofed.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc07e...0589`](https://bscscan.com/address/0xc07e1300dc138601fa6b0b59f8d0fa477e690589) |
| **Network** | BNB Chain |
| **Price** | $0.02258 |
| **24h Volume** | $1.61M |
| **Liquidity** | $963.9K |
| **Volume / Liquidity** | 1.7× |
| **Token Age** | 11mo |
| **Top-10 Holders** | 153.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 10571 buys / 11388 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is Quack AI Token a scam?

Based on automated analysis, Quack AI Token scores 64/100 (High Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is Quack AI Token safe to buy?

Our scanner flagged a risk score of 64/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has Quack AI Token been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x8bafe0bdd3eb9ae0539f5b32e771c1a72a189b7f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/quack-ai-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-27*
