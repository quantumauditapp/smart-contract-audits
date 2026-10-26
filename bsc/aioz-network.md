---
token: AIOZ Network
ticker: AIOZ
network: bsc
risk_score: 57
status: medium
date: 2026-09-22
---

# AIOZ Network (AIOZ) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/aioz-network-bsc)

---

## Audit Summary

The AIOZToken contract implements a standard ERC-20 token with owner-controlled minting and burning capabilities, and a fixed maximum total supply. Initial token distribution includes vesting via a TimelockFactory. A critical vulnerability was identified in the custom ERC20 implementation's `transferFrom` function, which can lead to tokens being transferred without sufficient allowance. Additionally, significant centralization risks exist due to owner-controlled supply management and an EOA owner.

> **Final Recommendation:** It is strongly recommended to address the critical bug in the `transferFrom` function immediately. This requires a redeployment of the token contract. For future deployments, consider using battle-tested and audited ERC-20 implementations from reputable libraries like OpenZeppelin to minimize the risk of fundamental token logic errors. Additionally, enhance access control by transferring ownership of critical functions (mint, burn) to a multi-signature wallet or a robust governance mechanism to mitigate the single point of failure risk associated with an EOA owner.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical architecture is a custom ERC-20 token with `Ownable` access control and a hard-capped total supply (7.1 Architecture). The contract uses Solidity 0.8.0+, mitigating common integer… |
| **Governance / Economics** | 2/10 | High | The token's economic model includes a fixed maximum total supply, which is a positive aspect for predictability (7.4 Economic). However, the `mint` and `burn` functions are `onlyOwner`, granting a… |
| **Upgrades** | 3/10 | High | The AIOZToken contract is not designed as an upgradeable proxy (7.7 Upgrades). This means that once deployed, its logic cannot be modified. While this eliminates upgrade-specific risks, it also means… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.8% |
| **Top-3 Unlocked** | ⚠️ 99.9% |

## Security Findings

_🟡 4 Medium · 🟢 1 Low_

### `M-01` — Owner is an Externally Owned Account (EOA)  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract owner, which controls critical functions like `mint`, `burn`, and `transferOwnership`, is an Externally Owned Account (EOA). EOAs are single points of failure; if the private key associated with this EOA is compromised, an attacker would gain full control over the token's supply management, posing a significant security risk.

**Recommendation:** It is highly recommended to transfer ownership to a multi-signature wallet (e.g., Gnosis Safe) to distribute control and reduce the risk associated with a single point of failure. This adds an extra layer of security by requiring multiple approvals for sensitive operations.


### `M-02` — Reliance on Custom ERC20 Implementation  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `ERC20` contract is a custom implementation rather than importing a battle-tested and audited library like OpenZeppelin Contracts. While the code largely mirrors standard ERC20 functionality, custom implementations are more susceptible to subtle bugs or deviations from the standard that may not be immediately apparent, as demonstrated by the critical `transferFrom` issue.

**Recommendation:** For future token deployments, strongly consider using well-established and audited ERC20 implementations from reputable libraries (e.g., OpenZeppelin). These libraries undergo extensive security audits and community review, significantly reducing the risk of fundamental vulnerabilities.


### `M-03` — Incorrect `transferFrom` Logic in Custom ERC20 Implementation  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `transferFrom` function in the custom `ERC20` contract first executes the `_transfer` of tokens and then performs the allowance check (`require(currentAllowance >= amount, "ERC20: transfer amount exceeds allowance")`) and allowance reduction. If `_transfer` succeeds but the subsequent allowance check fails, the transaction will revert, but the tokens will have already been moved. This breaks the fundamental ERC20 invariant that `transferFrom` should only succeed if the allowance is sufficient *before* the transfer, leading to an inconsistent state where tokens are transferred without proper authorization and the al

**Recommendation:** The allowance check and reduction must occur *before* the `_transfer` call within the `transferFrom` function. The correct order of operations should be: 1) Check allowance, 2) Reduce allowance, 3) Perform transfer. This issue requires a contract redeployment.


### `M-04` — Centralized Control of Token Supply  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `mint` and `burn` functions are protected by the `onlyOwner` modifier, granting a single address (the contract owner) exclusive control over increasing or decreasing the total supply of AIOZ tokens. This centralization introduces a significant risk, as a compromised owner key or malicious owner could manipulate the token supply, leading to severe economic consequences for token holders, such as inflation or deflation.

**Recommendation:** Consider implementing a more decentralized approach for supply management. This could involve a time-locked multi-signature wallet for minting/burning operations, or a community governance mechanism. If centralization is intended, ensure the owner's private key is secured with the highest possible standards.


### `L-01` — Unused `TimelockFactory` Instance in Constructor  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). In the `AIOZToken` constructor, a `TimelockFactory` instance is created (`TimelockFactory timelockFactory = new TimelockFactory();`) and used to create initial timelock contracts. However, the `timelockFactory` variable is local to the constructor and its address is not stored in a state variable. This means the `AIOZToken` contract itself cannot interact with or manage the deployed `TimelockFactory` after its construction, limiting potential future operational flexibility if dynamic timelock creation by the token contract was ever envisioned.

**Recommendation:** If there is no intention for the `AIOZToken` contract to interact with the `TimelockFactory` post-deployment, this is an informational observation. If future dynamic creation of timelocks by the token contract is a possibility, consider storing the `TimelockFactory` address in a state variable for later use.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x33d0...741d`](https://bscscan.com/address/0x33d08d8c7a168333a85285a68c0042b39fc3741d) |
| **Network** | BNB Chain |
| **Price** | $0.1365 |
| **24h Volume** | $1.96M |
| **Liquidity** | $1.67M |
| **Volume / Liquidity** | 1.2× |
| **Token Age** | 2y |
| **Top-10 Holders** | 64.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4758 buys / 5101 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x80968a476e0235a026fd1f33aaac5a3b7b76110f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/aioz-network-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-22*
