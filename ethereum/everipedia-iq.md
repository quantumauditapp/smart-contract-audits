---
token: Everipedia IQ
ticker: IQ
network: ethereum
risk_score: 71
status: high
date: 2026-09-01
---

# Everipedia IQ (IQ) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 71/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/everipedia-iq-eth)

---

## Audit Summary

The IQERC20 token contract implements a standard ERC20 token with added minting and burning capabilities. The contract leverages OpenZeppelin's battle-tested libraries for core ERC20 functionality and access control. A critical economic risk is identified due to the centralized control over token supply through minting and burning functions, which are accessible by the contract owner and a designated minter. While the owner is a multisig, the power to inflate the supply remains a significant concern.

> **Final Recommendation:** It is strongly recommended to implement robust off-chain governance or multi-signature controls for the `_minter` role to mitigate the risk of unauthorized token inflation. Consider implementing a maximum supply limit or a rate-limiting mechanism for minting to provide greater economic stability. Ensure the operational security of both the owner multisig and the designated minter address is paramount to prevent compromise.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The contract utilizes OpenZeppelin's robust ERC20, Ownable, and SafeMath libraries, which significantly enhance code security and mitigate common vulnerabilities like integer overflows (7.2 Code… |
| **Governance / Economics** | 1/10 | High | The contract design introduces a critical centralization risk due to the `owner` and `_minter` roles having unlimited minting and burning capabilities (7.4 Economic). This power allows for arbitrary… |
| **Upgrades** | 4/10 | Medium | The IQERC20 contract is not designed as an upgradeable proxy (7.7 Upgrades). Therefore, no upgrade-specific vulnerabilities or risks are present. Any changes to the contract logic would require… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · ⚪ 1 Informational_

### `C-01` — Centralized Minting/Burning Authority  *(Severity: Critical · Status: Unresolved)*

The `IQERC20` contract grants the `owner` and a designated `_minter` the ability to mint and burn an unlimited amount of tokens via the `mint` and `burn` functions. This centralized control over the token supply introduces a critical economic risk, as it allows for arbitrary inflation or deflation of the token, potentially devaluing existing token holders' assets. While the owner is a multisig, the power itself is highly centralized.

**Recommendation:** Implement a robust governance mechanism (e.g., a DAO or a more complex multi-signature scheme) to control minting and burning. Consider introducing a maximum total supply limit (`cap`) for the token or a rate-limiting mechanism for minting operations. If unlimited minting is an intentional design, ensure this is clearly communicated to token holders and that the `_minter` address is secured with the highest possible operational security standards.


### `H-01` — Minter Role Security  *(Severity: High · Status: Unresolved)*

The `_minter` address, once set by the `owner`, gains the power to mint and burn tokens. If this `_minter` address is a single Externally Owned Account (EOA) and its private key is compromised, an attacker could gain full control over the token supply, leading to severe economic damage. The `setMinter` function is `onlyOwner`, but the security of the `_minter` itself is critical.

**Recommendation:** Ensure that the `_minter` address is controlled by a highly secure entity, such as a hardware wallet, a multi-signature wallet, or a well-audited smart contract with robust access controls. Implement strict operational procedures around the `_minter`'s private key management or contract interaction. Regularly review the `_minter` address and its associated security practices.


### `I-01` — Standard ERC20 Approval Race Condition  *(Severity: Informational · Status: Unresolved)*

The `approve` function in ERC20 contracts is susceptible to a known front-running vulnerability. If a user approves an allowance for a spender and then attempts to change that allowance, a malicious actor could front-run the second transaction, spending the original allowance before the new one is set, and then spending the new allowance as well. This can lead to the spender spending more than intended.

**Recommendation:** While this is an inherent characteristic of the ERC20 standard, users should be advised to use the `increaseAllowance` and `decreaseAllowance` functions (which are implemented in this contract) instead of directly calling `approve` when modifying an existing allowance. These functions mitigate the race condition by atomically adding or subtracting from the current allowance.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x579c...b0c9`](https://etherscan.io/address/0x579cea1889991f68acc35ff5c3dd0621ff29b0c9) |
| **Network** | Ethereum |
| **Price** | $0.0007101 |
| **24h Volume** | $25.2K |
| **Liquidity** | $1.63M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 4y |
| **Top-10 Holders** | 92.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 130 buys / 58 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x07af6bb51d6ad0cf126e3ed2dee6eac34bf094f8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/everipedia-iq-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-01*
