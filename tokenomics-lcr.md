# Tokenomics (LCR)

> Lucrar tokens and NFTs are not securities. Transactions on them are not subject to the rules applicable to the protection of investors in securities.

The Lucrar token (LCR) is a BEP-20 token on BNB Smart Chain (the BEP-20 standard extends ERC-20). It was created on 2 February 2022, after several months of testing, and audited by Fairyproof in 2022 with no issues found. It is a plain BEP-20 with no transfer fee.

* Contract: `0x1510211E6DC81F5724A1BecA33C5AC70Dcca6CE0`
* Network: BNB Smart Chain (chain id 56)
* Decimals: **9**, not 18
* Total supply: 100,000,000 LCR
* Price on 13 September 2026: 1 LCR = 0.0001969 BNB = USD 0.143
* Liquidity of the PancakeSwap pair on the same date: about USD 338,000
* BscScan: [bscscan.com/token/0x1510211e6dc81f5724a1beca33c5ac70dcca6ce0](https://bscscan.com/token/0x1510211e6dc81f5724a1beca33c5ac70dcca6ce0)
* Market: PancakeSwap, pair LCR/WBNB `0x949292e7eb14ed1f86a33e3d38eb3aceade66ba9`
* Chart: [www.dextools.io/app/bsc/pair-explorer/0x949292e7eb14ed1f86a33e3d38eb3aceade66ba9](https://www.dextools.io/app/bsc/pair-explorer/0x949292e7eb14ed1f86a33e3d38eb3aceade66ba9)
* Price reference: [www.coingecko.com/en/coins/lucrar](https://www.coingecko.com/en/coins/lucrar)

**Note for anyone integrating the token.** LCR has 9 decimals. Any integration that assumes the usual 18 is wrong by a factor of one thousand million. Every contract in the ecosystem works in the token's smallest unit.

## Supply

100,000,000 LCR, all minted on the day the contract was deployed. The contract has no mint and no burn function. The supply will never be more nor less than that.

## Release from the contract

At deployment the company's main cold wallet (the deployer) received 20% of the supply. The remaining 80% stayed inside the contract and cannot be used. The contract has one function, `releaseFunds`, that only the deployer can call, and each call moves exactly 1,000,000 LCR (1% of supply) from the contract to the deployer. It was designed for one call per quarter, from April 2022, so that the full supply would take twenty years to leave the contract (April 2042).

Releases are manual. They are not automatic and they have not been made every quarter. As of September 2026, five releases have been made and 75,000,000 LCR remain inside the contract. Since 4 August 2022, every released million goes to a permanent lock contract, not to the market.

## Distribution

There was no seed sale, private sale or public sale, and no allocation to the founder or the team. The project was funded by the founder. Nobody received LCR for free. The only way the token entered circulation was through the liquidity pool on PancakeSwap, where anyone, including the founder, buys at market price.

The company's team, marketing and development are paid from the company's profit, not from the LCR held by the company.

## Liquidity

On 15 March 2022 the company added around 81.8 BNB (about EUR 27,000 at the time, more than half of its share capital) plus LCR to the PancakeSwap pool, at an initial price of around EUR 0.01 per LCR. The liquidity tokens (LP) were locked with Mudra until 15 May 2024 and stayed there until 2026. The initial price was chosen so that the pool would have enough tokens to trade without slippage and the deployer would keep tokens to add liquidity over time.

The Mudra term ended on 15 May 2024 and the tokens sat there for **two years and four months with no effective lock**, simply because nobody went to collect them. This is stated here because it is true and because it explains the decision that follows.

On 16 September 2026 the liquidity was withdrawn from Mudra (record no. 60080) and locked again with **UNCX**, contract `0xC765bddB93b0D1c1A88282BA0fa6B2d00E3e0c83`, lock no. 0, **until 14 September 2028 at 23:00 UTC** (15 September at 00:00 Lisbon time). The two-year term was chosen deliberately: if PancakeSwap V2 is discontinued, two years leave room to migrate the pool.

The numbers, to the digit. 0.484157675489798933 Cake-LP left the main wallet. 0.479316098734900897 stayed locked with UNCX, which is **93.35% of all the liquidity tokens of the pair**. The founder's personal wallet holds 0.029317541633474196, or 5.71%, which is **not locked**.

**What it cost.** UNCX charged its service fee in liquidity tokens rather than in BNB: 1% of what was locked, 0.004841576754897991 Cake-LP, about USD 3,100 at the price of the day. It was not an execution mistake, it was the price of the service, and it is written here because a document that only tells the good part is worth less than one that says what it cost.

**What did not move.** Comparing the readings before and after (blocks 122168890 and 122182423), the pool reserves, the liquidity token supply and the main wallet balance stayed the same. No LCR left anywhere: the vault receipt changed, the pool did not.

![](https://lucrar.pt/wp-content/uploads/2026/09/uncx-lcr-wbnb-bloqueio.png)

_The LCR/WBNB liquidity lock as UNCX itself shows it. Check it yourself at [app.uncx.network](https://app.uncx.network/lockers/manage/lockers-v2?service=edit&chain=56&pool=0x949292e7eb14ed1f86a33e3d38eb3aceade66ba9&locker=0xc765bddb93b0d1c1a88282ba0fa6b2d00e3e0c83&lock=0&wallet=0x34cfbb3a3533de9d2574cbfd8e8aee1119273233)._

Liquidity providers, including the company, earn the PancakeSwap fee on every trade in proportion to their share of the pool.

## The economy being built

Two of the contracts described below are published on the main network and verified on BscScan: `LcrCaixa` and `PasseDaAldeia`. **Nothing has run through them yet** — no payment has been split and no pass has been issued. The rest are specified and not written. They go to the BSC testnet and through an external review before anything runs for real, and the dates are not promised.

## One exit point, and an address nobody holds the key to

All LCR spent inside the ecosystem passes through a single contract, `LcrCaixa` (`0xcc7B907100D55606591889d51FB75043073d9B1d`), which splits the payment in the same transaction and never holds a balance:

| Share | Where it goes | Address |
|---|---|---|
| 70% | a public address nobody holds the private key to | `0x000000000000000000000000000000000000dEaD` |
| 20% | the company treasury | `0x72626707f2148124cea8a7529fbc6e9e7bc2801e` |
| 10% | the financial education fund | `0xeA248d510b30A361d3C32d41bC89b754515b3900` |

**This is not a burn, and we do not call it one.** The LCR contract has no burn function: `burn(uint256)`, `burnFrom(address,uint256)` and `_burn` are all absent from the published bytecode. The total supply is 100,000,000 LCR and it never goes down. Anyone reading `totalSupply()` on BscScan will always see that number.

What happens to the 70% is a transfer to `0x…dEaD`, a public address nobody holds the private key to. Those tokens leave circulation and do not come back, but they keep counting towards the total supply. How many are there at any moment is the `balanceOf` of that address, which anyone can read. So the circulating supply falls and the total supply stays where it is. Saying "burned" would suggest the second number drops. It does not, and we do not know what effect any of this has on the price.

**An honest note about the code.** In the verified source of `LcrCaixa`, that share is called `pQueima` — "burn share" — and the corresponding field of the `Pago` event is called `queimado`, "burned". Those were the names given when the code was written, the contract is published, and its code cannot be changed. The names are wrong: what the code does is a `transfer`. We would rather say it here than have someone find it on BscScan and draw their own conclusion.

**What the owner of LcrCaixa can still change.** The code is fixed, but three things in it are parameters the owner can change: the 70/20/10 split (`mudarRepartacao`), the treasury and fund addresses (`mudarDestinos`), and whether the contract accepts payments at all (`parar`). The destination of the 70% is not one of them — `MORTE` is a constant written into the code. Ownership moves in two steps, proposal and acceptance; today the owner is the company's profits wallet. Every change of this kind emits an event and will be listed in Changes since launch.

Any remainder of the integer division is added to the 70% share, so the contract always ends at zero. There is no custody at any point. Each payment carries a unique reference and the contract refuses a reference it has already seen, so the same payment cannot be credited twice.

## How LCR is obtained

* **By playing.** Prizes in Aldeia Lucrar are paid in LCR, capped at 40 LCR per member per month. That cap is enforced by the server today and moves inside the `PremiosDaAldeia` contract, so that it becomes something anyone can verify rather than something the company says.
* **By buying.** The open market on PancakeSwap, for anyone who does not want to wait.

## What LCR pays for

The Aldeia pass (the subscription that opens the game, the Patreon area and the reserved areas of the website), part of the price of the courses, and goods inside the game.

## The two rules of this economy

**The shop floor.** For paying inside the Lucrar shop, one LCR is always counted as at least EUR 0.40. If the market price is higher, the market price is used, so that nobody who held LCR is worse off. The conversion is read from an oracle at the moment of purchase. At today's price that means LCR buys roughly three times more inside the shop than it is worth outside, and that difference is what creates demand for the token without anyone having to be convinced of anything. The floor is commercial policy and can be revised. It is not a price guarantee, not a promise to buy back, and it applies only to purchases inside the platform.

**The 50% rule.** Nothing is ever free. At most 50% of the price of any purchase can be paid in LCR; the rest is always money. This protects the company's revenue, caps the cost of the discount programme at a known figure, and stops the system being drained.

On a course of EUR 97:

| LCR used | Earned by playing | Discount | Share of the price |
|---|---|---|---|
| 40 LCR | 1 month | EUR 16 | 16% |
| 80 LCR | 2 months | EUR 32 | 33% |
| 120 LCR | 3 months | EUR 48 | 49% (the cap) |

## The Aldeia pass

An NFT with an expiry date, non-transferable (soulbound, the ERC-5192 standard), with an ERC-721 face so that it shows up in wallets and on BscScan. One pass per wallet. It is not the Lucrar Pass collection of 2022: that one is closed, it is a different asset, and it has its own page.

It is the single source of truth: the game, the website and the Patreon area all read the same function, `ativo(wallet)`, instead of each keeping its own database. There are two ways to pay and one place to check: whoever pays in LCR extends the pass themselves, and the 70% share goes to the address with no owner; whoever pays by card or through Patreon is extended by the server, with no LCR spent.

It is non-transferable on purpose. If a pass could be resold, one pass would be bought, used and sold on, and the locking effect would disappear. Extending adds up: with a live pass, new months are added to what is left.

## Wallets and gas

Every player gets a wallet created from their email login: no seed phrase, nothing to install, no need to hold BNB. The gas is paid by the project. Anyone already using crypto can connect their own wallet instead.

Gas measured on 13 September 2026, with BSC at 0.05 gwei and BNB at USD 728:

| Action | Cost |
|---|---|
| Claim prizes | USD 0.011 |
| Pass | USD 0.014 |
| Course | USD 0.019 |

An active player costs about USD 0.017 a month in gas.

## The contracts

`LcrCaixa` (`0xcc7B907100D55606591889d51FB75043073d9B1d`) and `PasseDaAldeia` (`0xfD60a06E1d6C01FfAEc272c8754932D22a674310`) are written, tested with 27 tests passing, published on the main network and verified on BscScan. Neither has been used yet.

Then, in this order:

* `CursoLucrar` — access to the courses, and where the EUR 0.40 floor and the 50% rule live, with the oracle.
* `PremiosDaAldeia` — prizes in LCR with the monthly cap inside the contract.
* `TorneioSemanal` — the weekly pot through a Merkle tree, one transaction per week.
* `Aldeoes` — characters as NFTs with the image generated inside the contract. The only transferable one.

All of them without external dependencies, 200 to 350 lines each, written that way on purpose so that one person can review them in an afternoon. Publication on the BSC testnet and an external review come before the main network.

## Price

The price is set by supply and demand on PancakeSwap and it follows BNB, because the pool is LCR/BNB. The company does not manage the price and does not promise any price. The token started at around EUR 0.01 in March 2022; on 13 September 2026 the reference was USD 0.143. These are historical values, not a forecast.

## Mechanics

Because there was no sale below the initial price, if everyone sold, the price would return approximately to the initial value; nobody holds tokens bought cheaper than the pool. Large sales move the price down along the pool curve, so a large seller takes fewer BNB out. This is the standard behaviour of an automated market maker, not a feature of the token.

The company's stated measures on top of that:

* A reserve wallet in stablecoin to buy LCR after large drops (25% of the reserve after a 50% drop from the all-time high, the remaining 75% after a 90% drop, at most once a year). See Security and protection for the state of that reserve.
* Purchases of LCR by the company on the open market, at its discretion. Two have been made so far (see Utility).

## Decentralisation over time

The company's long-term plan, unchanged since 2022, is for LCR to become decentralised as the supply leaves the contract and enters the liquidity pool, so that over the years the company no longer holds the majority. That depends on the release schedule described above and on holders choosing to provide liquidity. It has no fixed date.

## What this page does not say

None of this is financial or legal advice. LCR is a utility token. In the EU, MiCA also covers utility tokens, and the company will take legal advice before selling courses in LCR. The liquidity of the pair is limited (about USD 338,000), so a very large purchase moves the price. The EUR 0.40 floor is commercial policy inside the shop, revisable, and neither a price guarantee nor a promise to buy back.
