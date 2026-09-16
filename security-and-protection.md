# Security and protection

## The lock does not open by itself

The date of 14 September 2028 does not open the vault. It only makes withdrawal _possible_. The liquidity tokens stay in the UNCX contract indefinitely until someone, from wallet `0x34CfbB3a3533De9D2574cBfd8e8aeE1119273233`, signs a transaction to take them out. That is exactly what happened with the previous vault: the Mudra term ended in May 2024 and the liquidity stayed there until September 2026, with no effective lock, because nobody went to collect it. That is why the 2028 decision is written down here, in advance.

**The three options for 2028.**

* **Extend the term in the same vault**, withdrawing nothing. There is no window with the liquidity loose and no fee for creating a new lock.
* **Withdraw and lock again somewhere else**, if PancakeSwap V2 no longer serves. That is what was done in 2026 and it cost 1% of the liquidity.
* **Withdraw and leave it loose.** The unlocked-liquidity flag comes back, with everything that means to anyone looking at the token from outside.

> **The rule that failed in 2026:** before signing any of these operations, check in the application itself what it costs and whether there is an alternative way to pay — a flat fee in BNB instead of a percentage in liquidity tokens. Open the advanced options of the form and do not accept the default.

Three things this lock does **not** do, and that should not be read the other way round: it is not forever, it runs to a date; it does not cover all the liquidity, it covers 93.35%; and it does not guarantee the price nor protect buyers from losses. It only stops the locked liquidity from being pulled before the date.

## Four cold wallets

The company keeps LCR in four cold wallets with separate jobs. All four are public; balances can be checked on BscScan at any time, and the September 2026 reading is in the On-chain status page.

| Wallet | Address | Job |
|---|---|---|
| Main wallet (deployer) | `0x34CfbB3a3533De9D2574cBfd8e8aeE1119273233` | Receives the releases from the contract and adds liquidity to the pool. **Never sells.** |
| Financial education fund | `0xeA248D510B30a361d3C32d41Bc89b754515B3900` | The fund for the education mission (10% of results). |
| Company profit | `0x72626707f2148124Cea8A7529fbc6e9e7BC2801e` | The only wallet allowed to buy, sell or transfer LCR, used to allocate results. Owner of the NFT contracts. |
| Reserve | `0x39B6Cb2fe7f7E9dDf10121A5506EE5faDA3b334c` | Stablecoin reserve to buy LCR after large price drops. |

## The reserve and its rule

If LCR drops 50% or more from its all-time high, 25% of the reserve is converted to LCR. If it drops 90% or more, the remaining 75%. Because of limited resources this can be used at most once a year.

State of the reserve, read on 15 September 2026: the wallet holds **580.18 USDT** on BNB Smart Chain. It holds no BUSD, no USDC and no LCR.

Until that day the reserve was held in BUSD, the stablecoin chosen in 2022. Its issuer discontinued BUSD in 2023 and 2024 and it lost any reliable market, which in practice made the reserve unusable for the job it exists to do. On 15 September 2026 the company converted the whole balance: 585 BUSD became 580.18 USDT. The difference is what it costs to sell an asset that no longer has liquidity. The conversion is public and can be read on BscScan: transaction `0xc061a79fb351cbe3c62d8a10f4cf970fd6c45a35c3b9e1d9c22e914e35f1a9d1`, block 121,941,461.

The rule above stands and is executable again. The wallet is operated through a physical signing device (Ledger).

The reserve is small in absolute terms. At 580 USDT it is a gesture, not a floor under the price: it is not a guarantee of price and not a promise to buy anyone's tokens back.

## What the token contract can and cannot do

The LCR contract was deployed in February 2022 and cannot be changed. It is not a proxy and has no upgrade path. Its whole interface is nineteen functions, and the only one outside the ERC-20 standard is `releaseFunds()`.

**There is no function to** create tokens, destroy tokens, pause transfers, blacklist or whitelist an address, set a buy or sell fee, or hand the contract to a different owner. None of these exist in the code, so none of them can happen.

**releaseFunds() is the only function restricted to the owner.** It moves exactly 1,000,000 LCR from the contract to the company's main wallet, once per quarter, for at most eighty quarters, always to the address written in at deployment. There is no setter for that address, and the function refuses to run twice in the same quarter.

**Ownership cannot be renounced.** The contract has no `renounceOwnership()` and no `transferOwnership()`. Automated risk checkers therefore report LCR as "ownership not renounced", and that is accurate. The owner's entire power is the paragraph above, and because the contract is immutable this will never change. The company states it plainly rather than leaving it to be discovered.

**The largest holder of LCR is the contract itself**, with 75,000,000 LCR: the part not yet released. Tools that rank holders show this as a single address holding 75% of supply. It is not a person, and it is not a wallet anyone can spend from at will; it is the undistributed supply, leaving at one million per quarter and no faster.

## Gold as a reserve of value

The project also holds physical gold in Swiss vaults (Elementum) as a reserve for times of crisis. The purchase contract and the certification are published on lucrar.pt:

* [lucrar.pt/wp-content/themes/lucrar-hello-child/gold_backup/assets/pdfs/PT-TCG-GOLD02_TCG_Compra_e_Venda_Aurora_Gold.pdf](https://lucrar.pt/wp-content/themes/lucrar-hello-child/gold_backup/assets/pdfs/PT-TCG-GOLD02_TCG_Compra_e_Venda_Aurora_Gold.pdf)
* [lucrar.pt/wp-content/themes/lucrar-hello-child/gold_backup/assets/pdfs/H25-01056-2.pdf](https://lucrar.pt/wp-content/themes/lucrar-hello-child/gold_backup/assets/pdfs/H25-01056-2.pdf)

The gold belongs to the company. It is not backing for LCR and LCR holders have no claim on it.

## The main wallet never sells

The company's main wallet is used only to add liquidity to the pool, over twenty years or more. The company has not sold a single LCR since the project began. The only exception ever contemplated is bankruptcy, in which case the company simply could not add more liquidity.

## Smart contract audit

The company paid Fairyproof, a blockchain security firm (auditor of Tether, Venus, Beefy Finance, IDEX and others), to audit the LCR contract. Automated tools and manual review found no issues. The report (October 2022) is public:

[lucrar.pt/wp-content/themes/lucrar-hello-child/owner/assets/pdfs/LCRToken-Audit-Report-021022.pdf](https://lucrar.pt/wp-content/themes/lucrar-hello-child/owner/assets/pdfs/LCRToken-Audit-Report-021022.pdf)

## Company policy manual

The Manual of Policies of Cripteracia, Unipessoal, Lda., in Portuguese, sets the principles that guide the company's decisions and applies to everyone who works with it, whatever their role. Its approval was recorded in minutes. Both are published on [lucrar.pt/pt/informacoes-da-empresa](https://lucrar.pt/pt/informacoes-da-empresa/).

## Your own security

The website never stores crypto assets. When it reads a balance (to open the off-plan folder or the transaction register) it only reads; it never asks for a signature to move tokens. Keep your wallet's seed phrase offline and never share it. Nobody from the project will ever ask for it.
