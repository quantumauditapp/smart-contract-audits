---
token: LQTY
ticker: LQTY
network: ethereum
risk_score: 49
status: high
date: 2026-07-27
---

# LQTY (LQTY) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 49/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/lqty-eth)

---

## Audit Summary

The LQTYToken contract implements an ERC-20 token with EIP-2612 (Permit) functionality. It features a fixed supply, specific initial token allocations, and time-locked restrictions on the Liquity multisig's operations for the first year post-deployment. The contract utilizes OpenZeppelin's SafeMath for arithmetic safety and includes custom checks for valid recipients and core contract callers. Overall, the contract demonstrates robust design and implementation practices, with identified risks being primarily informational or low-severity, related to inherent design choices or standard EIP behaviors.

> **Final Recommendation:** The LQTYToken contract is well-designed and implemented, adhering to established security practices. Users interacting with the EIP-2612 `permit` function should be aware of potential front-running risks and utilize appropriate `deadline` values. The multisig responsible for initial token distribution should maintain robust security practices, especially given its significant role and the lifting of restrictions after the first year. Regular security reviews of all interacting Liquity core contracts, particularly the `LockupContractFactory`, are recommended to ensure the overall ecosystem's integrity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The LQTYToken contract exhibits strong technical security. It leverages OpenZeppelin's battle-tested ERC-20 and EIP-2612 implementations, including SafeMath for robust integer arithmetic (7.2 Code… |
| **Governance / Economics** | 3/10 | High | The economic model of LQTYToken is transparent, featuring a hard-capped supply of 100 million tokens, all minted at deployment (7.4 Economic). The initial distribution to various stakeholders… |
| **Upgrades** | 7/10 | Low | The LQTYToken contract is not designed as an upgradeable proxy (7.7 Upgrades). This means that its logic cannot be altered post-deployment. While this design choice eliminates upgrade-related risks… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 54.2% |
| **Top-3 Unlocked** | ⚠️ 94.3% |

## Security Findings

_🟢 2 Low · ⚪ 3 Informational_

### `L-01` — Centralized Control via Multisig  *(Severity: Low · Status: Unresolved)*

The `multisigAddress` receives a significant portion of the initial LQTY token supply (64.66 million tokens) and, after the initial one-year restriction period, will have unrestricted control over these tokens. While the initial time-locked restrictions mitigate immediate risks, the multisig remains a central point of control. A compromise of the multisig's private keys or its governance process could lead to unauthorized token movements.

**Recommendation:** Implement robust security measures for the `multisigAddress`, including strong key management practices, multi-factor authentication, and strict operational procedures. Consider transitioning to more decentralized governance mechanisms over time if feasible.


### `L-02` — Dependency on LockupContractFactory  *(Severity: Low · Status: Unresolved)*

For the first year after deployment, the `multisigAddress` is restricted to only transferring LQTY tokens to `LockupContracts` that have been deployed via and registered in the `LockupContractFactory`. This introduces a dependency on the correct functioning and security of the `LockupContractFactory` contract. If the `LockupContractFactory` were compromised or malfunctioned, it could hinder the multisig's ability to distribute tokens as intended during the restricted period.

**Recommendation:** Ensure the `LockupContractFactory` contract is thoroughly audited and maintained with the highest security standards. Implement monitoring for the `LockupContractFactory` to detect any unusual activity or potential compromises that could impact the LQTY token distribution.


### `I-01` — Non-Upgradeability of Contract  *(Severity: Informational · Status: Unresolved)*

The LQTYToken contract is implemented as a standard, non-upgradeable contract. This design choice means that once deployed, the contract's logic cannot be modified. Consequently, any bugs discovered post-deployment cannot be patched, and new features cannot be introduced without deploying an entirely new contract and migrating assets.

**Recommendation:** Acknowledge this design choice. Ensure thorough testing and auditing pre-deployment, as the contract's immutability makes post-deployment fixes impossible. Communicate this characteristic clearly to users and stakeholders.


### `I-02` — EIP-2612 Permit Front-Running Risk  *(Severity: Informational · Status: Unresolved)*

The contract implements EIP-2612's `permit` function, which allows users to approve token transfers via a signed message instead of an on-chain transaction. While standard, this mechanism can be susceptible to front-running. A malicious actor could observe a valid `permit` signature in the mempool and submit their own transaction with a higher gas price to execute the `permit` before the legitimate user, potentially gaining the approved allowance.

**Recommendation:** Educate users about the potential for front-running with `permit` and advise them to set a strict `deadline` parameter to limit the time window for exploitation. Off-chain relayers should also implement measures to prevent front-running.


### `I-03` — Fixed Token Supply and Initial Distribution  *(Severity: Informational · Status: Unresolved)*

The LQTY token has a hard-capped total supply of 100 million tokens, all of which are minted during the contract's deployment. The initial distribution to specific addresses (bounty, community issuance, LP rewards, and multisig) is hardcoded in the constructor. This design ensures transparency and predictability of the token supply, as no further tokens can be minted or burned, and the initial distribution cannot be altered.

**Recommendation:** This is a design choice that enhances transparency and predictability. No specific recommendation is needed beyond ensuring that the initial allocation addresses are correct and secure.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6dea...c54d`](https://etherscan.io/address/0x6dea81c8171d0ba574754ef6f8b412f2ed88c54d) |
| **Network** | Ethereum |
| **Price** | $0.1968 |
| **24h Volume** | $200.4K |
| **Liquidity** | $474.7K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 5y |
| **Top-10 Holders** | 84.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 335 buys / 341 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is LQTY a scam?

Based on automated analysis, LQTY scores 61/100 (High Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is LQTY safe to buy?

Our scanner flagged a risk score of 61/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has LQTY been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xd1d5a4c0ea98971894772dcd6d2f1dc71083c44e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/lqty-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-27*
