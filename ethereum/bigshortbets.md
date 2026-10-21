---
token: BigShortBets
ticker: BIGSB
network: ethereum
risk_score: 81
status: high
date: 2026-09-03
---

# BigShortBets (BIGSB) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 81/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bigshortbets-eth)

---

## Audit Summary

The BigSB token contract implements a deflationary ERC-20 token with reflection mechanics, automated liquidity provision, and anti-whale/anti-bot features. The contract exhibits a high degree of centralized control by the owner, who can modify critical economic parameters, pause transfers, and exclude addresses from fees and rewards. While the code is generally well-structured and uses Solidity 0.8.7 for overflow protection, the extensive owner privileges introduce significant trust assumptions and potential for malicious manipulation or operational risks.

> **Final Recommendation:** To mitigate the identified risks, consider decentralizing critical control functions by implementing a multi-signature wallet or a time-locked governance mechanism for sensitive parameter changes (e.g., fees, anti-whale limits, pause functionality). Clearly document the intended use and limitations of owner-controlled functions to manage community expectations. For gas efficiency, explore alternative data structures or limits for the `_excluded` array if it is expected to grow large.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract's architecture (7.1) is a standard ERC-20 with added deflationary and reflection mechanisms. Code security (7.2) benefits from Solidity 0.8.7, mitigating common integer issues. However… |
| **Governance / Economics** | 1/10 | High | Access control (7.3) is heavily centralized, with an `Owned` contract granting the owner extensive privileges over critical economic parameters (7.4). The owner can arbitrarily set all transaction… |
| **Upgrades** | 6/10 | Medium | The BigSB contract is not designed with upgradeability in mind (7.7). It is a standard contract deployment without a proxy pattern, meaning its logic cannot be changed after deployment. This… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | 28.8% |
| **LP Locked** | 28.8% — Null Address |
| **Top-1 Unlocked Holder** | 42.1% |
| **Top-3 Unlocked** | 71.2% |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Centralized Control Over Critical Parameters and Transfers  *(Severity: Critical · Status: Unresolved)*

The `owner` of the contract possesses extensive control over critical functions and parameters. This includes the ability to set all transaction fees (reflection, burn, liquidity, wallet) to arbitrary values, enable/disable the `swapAndLiquify` mechanism, set `_maxTxAmount` and `_maxWalletAmount` to zero (effectively halting all transfers or making tokens untradable), pause all transfers via `_isPaused`, and recover any ERC20 tokens or ETH accidentally sent to the contract. This level of centralization creates a single point of failure and a significant rug-pull risk, as a malicious or compromised owner could severely impact token holders.

**Recommendation:** Implement a multi-signature wallet for ownership or transition to a decentralized governance model. For highly sensitive functions like pausing transfers or setting critical limits, consider adding a time-lock mechanism or requiring community consensus through a DAO vote. Clearly communicate the extent of owner privileges to the community.


### `H-01` — Potential for Manipulation of Anti-Whale/Anti-Bot Limits  *(Severity: High · Status: Unresolved)*

The `_maxTxAmount` and `_maxWalletAmount` variables, intended to prevent large transactions or holdings, can be modified by the owner at any time. While these features aim to protect against market manipulation, an malicious owner could set these limits to extremely low values. This could effectively prevent users from selling their tokens (if `_maxTxAmount` is too low) or holding their desired amount (if `_maxWalletAmount` is too low), leading to a denial of service for token holders or forced sell-offs at disadvantageous prices.

**Recommendation:** If these limits are deemed necessary, consider making them immutable after deployment or subject to a time-locked, multi-signature, or governance-controlled update process. Provide clear documentation on the purpose and potential impact of these limits.


### `H-02` — High and Arbitrarily Modifiable Transaction Fees  *(Severity: High · Status: Unresolved)*

The contract implements multiple transaction fees (reflection, burn, liquidity, wallet) which can sum up to a significant percentage of each transfer. The owner has the ability to modify these fees at any time through functions like `setReflectionFee`, `setBurnFee`, `setLiquidityFee`, and `setWalletFee`. This arbitrary control over fees introduces economic uncertainty for users and could be exploited by a malicious owner to extract excessive value from transactions, negatively impacting token liquidity and user trust.

**Recommendation:** Consider capping the maximum allowable fees or implementing a time-lock for fee changes to provide transparency and predictability for users. Alternatively, decentralize fee management through a governance mechanism.


### `M-01` — Gas Inefficiency in `_excluded` Array Management  *(Severity: Medium · Status: Unresolved)*

The `includeInReward` and `excludeFromReward` functions iterate through the `_excluded` array to add or remove addresses. If the number of excluded addresses grows significantly, these operations will become increasingly gas-intensive. This could lead to high transaction costs, potentially making these functions prohibitively expensive to call, effectively causing a denial of service for managing excluded addresses.

**Recommendation:** For large numbers of excluded addresses, consider alternative data structures (e.g., a mapping `isExcluded[address] => bool` without an array for iteration) or implement a mechanism to process exclusions in batches. If the array is necessary, enforce a reasonable maximum size for `_excluded` to prevent excessive gas consumption.


### `L-01` — Use of `UNLICENSE` License  *(Severity: Low · Status: Unresolved)*

The contract uses the `UNLICENSE` identifier. While legally permissible, `UNLICENSE` is less common and explicit than other open-source licenses like MIT, Apache 2.0, or GPL. Using a more widely recognized license can provide clearer terms regarding intellectual property rights, permissions, and limitations for users and developers interacting with the code.

**Recommendation:** Consider adopting a more standard and explicit open-source license (e.g., MIT License) to provide greater clarity on the terms of use and distribution of the contract code.


### `I-01` — Extensive In-Code Project Description  *(Severity: Informational · Status: Unresolved)*

The contract includes a very long, philosophical project description and marketing text as a multi-line comment at the top of the `bigsb-token.sol` file. While informative for understanding the project's vision, this extensive text adds unnecessary bytes to the deployed bytecode (if not optimized away by the compiler) and can make the source code harder to navigate and review for security-critical logic.

**Recommendation:** Relocate extensive project descriptions and marketing content to external documentation (e.g., project website, whitepaper, GitHub README). Keep in-code comments concise and focused on explaining the logic, purpose, and invariants of the code itself.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1311...b6f6`](https://etherscan.io/address/0x131157c6760f78f7ddf877c0019eba175ba4b6f6) |
| **Network** | Ethereum |
| **Price** | $0.1866 |
| **24h Volume** | $23.3K |
| **Liquidity** | $218.2K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 4y |
| **Top-10 Holders** | 87.3% of supply |
| **Buy / Sell Tax** | 1.5% / 1.5% |
| **24h Transactions** | 100 buys / 65 sells |

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

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x149148acc3b06b8cc73af3a10e84189243a35925)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bigshortbets-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-03*
