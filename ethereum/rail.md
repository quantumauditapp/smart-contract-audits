---
token: Rail
ticker: RAIL
network: ethereum
risk_score: 57
status: medium
date: 2026-09-06
---

# Rail (RAIL) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/rail-eth)

---

## Audit Summary

The RailToken contract implements a standard ERC20 token with additional anti-bot logic within its transfer function. While leveraging well-audited OpenZeppelin libraries for core functionality, the custom anti-bot mechanism introduces considerable complexity and potential for unintended transfers. Centralization risks exist due to the owner's minting capabilities and the immutability of critical anti-bot parameters and whitelisted addresses. The contract is not upgradeable, which simplifies upgrade safety but means any issues with the anti-bot logic or parameters cannot be easily rectified post-deployment.

> **Final Recommendation:** It is highly recommended to thoroughly review and simplify the anti-bot logic within the `transfer` function. Consider making critical anti-bot parameters and the 'GARDENER' address configurable by the owner or a multi-signature wallet to allow for adjustments post-deployment. Implement clear and descriptive error messages for all `require` statements to improve user experience and debugging. Evaluate the necessity and implications of the owner's `governanceMint` function and consider implementing a timelock or multi-signature for such powerful actions to mitigate centralization risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract utilizes battle-tested OpenZeppelin libraries for ERC20 and Ownable functionalities, which contributes positively to its baseline security (7.2 Code Security). However, the custom… |
| **Governance / Economics** | 6/10 | Medium | The contract exhibits centralization risks as the `owner` has the exclusive ability to `governanceMint` new tokens, which could lead to token dilution if not managed responsibly (7.3 Access Control… |
| **Upgrades** | 5/10 | Medium | The RailToken contract is not designed as an upgradeable proxy. It is a standard implementation contract, meaning its logic cannot be changed after deployment. This eliminates upgrade-related risks… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 42.4% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 42.6% |
| **Top-3 Unlocked** | 57.6% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Complex and Potentially Exploitable Anti-Bot Logic  *(Severity: High · Status: Unresolved)*

The `transfer` function contains complex anti-bot logic that relies on `tx.gasprice` and `block.timestamp`. An attacker could manipulate `tx.gasprice` to intentionally trigger the anti-bot mechanism, causing a victim's tokens to be transferred to the hardcoded `GARDENER` address instead of the intended recipient. The `require("true")` error message is uninformative, hindering user understanding and debugging. The `GARDENER` address is hardcoded and cannot be changed, posing a risk if it becomes compromised or inaccessible. This impacts 7.2 Code Security and 7.4 Economic.

**Recommendation:** Simplify the anti-bot logic, if possible, and ensure it is robust against manipulation. Replace `tx.gasprice` checks with more reliable on-chain mechanisms or remove them if the risk outweighs the benefit. Implement clear and descriptive error messages for all `require` statements. Consider making the `GARDENER` address and anti-bot parameters configurable by the owner or a multi-signature wallet to allow for updates and emergency changes.


### `M-01` — Centralization Risk with Owner Minting Power  *(Severity: Medium · Status: Unresolved)*

The `owner` of the contract has the exclusive ability to call `governanceMint`, allowing them to mint new tokens up to the defined `cap`. While a `cap` exists, this still grants significant power to a single entity, potentially leading to token dilution for existing holders or misuse if the owner's key is compromised. There are no additional safeguards like timelocks or multi-signature requirements for this critical function. This impacts 7.3 Access Control and 7.5 Governance.

**Recommendation:** Consider implementing a multi-signature wallet for the `owner` address or introducing a timelock for sensitive operations like `governanceMint`. This would add an extra layer of security and decentralization, reducing the risk of a single point of failure or malicious action.


### `M-02` — Hardcoded Anti-Bot Parameters and Gardener Address  *(Severity: Medium · Status: Unresolved)*

Several critical parameters for the anti-bot mechanism, including `ANTI_BOT_LOCKTIME`, `ANTI_BOT_SOFT_GASLIMIT`, `ANTI_BOT_HARD_GASLIMIT`, `ANTI_BOT_AMOUNT_CAP`, and the `GARDENER` address, are hardcoded as constants. This immutability prevents any adjustments to the anti-bot strategy in response to changing market conditions, evolving bot tactics, or if the `GARDENER` address needs to be updated (e.g., due to compromise). This impacts 7.8 Operations.

**Recommendation:** Make critical anti-bot parameters and the `GARDENER` address configurable by the contract owner or a governance mechanism. This would allow for flexibility and adaptability in managing the anti-bot system post-deployment, ensuring its continued effectiveness and security.


### `L-01` — Immutable LP Whitelist  *(Severity: Low · Status: Unresolved)*

The `lps` mapping, which whitelists addresses to bypass the anti-bot logic, is populated only during contract deployment in the constructor. There is no function to add or remove addresses from this whitelist after deployment. This immutability can lead to operational inflexibility if new liquidity providers need to be added or if existing LP addresses change or become compromised. This impacts 7.8 Operations.

**Recommendation:** Consider adding an `onlyOwner` function to manage the `lps` whitelist, allowing the owner to add or remove addresses as needed. This would provide necessary flexibility for project operations without compromising security, especially if combined with multi-signature or timelock controls for the owner.


### `I-01` — Usage of tx.origin for Anti-Bot Logic  *(Severity: Informational · Status: Unresolved)*

The contract uses `tx.origin` as part of its anti-bot logic (`tx.origin == msg.sender`). While `tx.origin` is generally discouraged for access control due to phishing risks, its use here is to differentiate between direct calls and contract calls for anti-bot purposes, which is a common pattern. However, it's still a less robust identifier than `msg.sender` and can be a source of confusion or unexpected behavior in complex interactions. This impacts 7.2 Code Security.

**Recommendation:** While not a critical vulnerability in this specific context, it's generally best practice to avoid `tx.origin` where possible. If the intent is to prevent contract interactions, alternative methods like checking `msg.sender == address(this)` or using a specific whitelist for allowed contracts might be considered, though they come with their own complexities.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe76c...a33d`](https://etherscan.io/address/0xe76c6c83af64e4c60245d8c7de953df673a7a33d) |
| **Network** | Ethereum |
| **Price** | $2.2200 |
| **24h Volume** | $202.5K |
| **Liquidity** | $5.54M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 5y |
| **Top-10 Holders** | 79.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 133 buys / 77 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x2837809fd68e4a4104af76bbec5b622b6146b2cb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/rail-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-06*
