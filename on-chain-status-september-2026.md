# On-chain status (September 2026)

Everything on this page was read directly from BNB Smart Chain on 13 September 2026, except the reserve, re-read on 15 September 2026 after the conversion described below. Anyone can repeat the reading on BscScan. It will be refreshed at each revision of this whitepaper.

## Where the 100,000,000 LCR are

| Where | LCR | % of supply |
|---|---|---|
| Inside the token contract, not yet released | 75,000,000 | 75.00% |
| Company main wallet (deployer) | 18,166,653 | 18.17% |
| Permanent lock contract | 4,124,604 | 4.12% |
| PancakeSwap liquidity pool | 1,177,177 | 1.18% |
| Founder's personal wallet | 772,013 | 0.77% |
| Team lock contract (temporary lock from 2022) | 524,683 | 0.52% |
| Company profit wallet | 71,703 | 0.07% |
| Early contributors' wallet | 9,772 | 0.01% |
| Financial education fund wallet | 4,936 | 0.00% |
| Everyone else (public holders) | about 148,000 | 0.15% |

* Holders: 290 addresses. Transfers since creation: 33,940.
* The first line of that table is the token contract itself. Tools that rank holders show it as one address holding 75% of supply; it is the undistributed supply, released at one million per quarter and no faster. See Security and protection for what the contract can and cannot do.
* The reserve wallet holds no LCR (it is meant to hold stablecoin; see Security and protection).

## The reserve

| What | Amount | Read on |
|---|---|---|
| Reserve wallet `0x39B6Cb2f…3b334c`, in USDT | 580.18 USDT | 15 September 2026 |

* On 15 September 2026 the reserve was converted from BUSD to USDT: 585 BUSD became 580.18 USDT. Transaction `0xc061a79fb351cbe3c62d8a10f4cf970fd6c45a35c3b9e1d9c22e914e35f1a9d1`.
* The main wallet still shows 11.22 BUSD. That is a leftover, it is not the reserve and it has no function.

## The pool

* 1,182,347.435155876 LCR and 231.020709233 WBNB in the LCR/WBNB pair, about USD 338,000 of liquidity at the BNB price of the day. Read at block 122,184,387 on 16 September 2026.
* 1 LCR = 0.0001969 BNB at the time of reading, about USD 0.143.
* The liquidity tokens, read at block 122,184,387: **93.35%** are held in the UNCX vault `0xC765bddB93b0D1c1A88282BA0fa6B2d00E3e0c83` (lock no. 0, created on 16 September 2026, unlocking on 14 September 2028); **5.71%** are in the founder's personal wallet and are **not locked**; the remaining 0.94% was the 1% fee paid to UNCX. The Mudra contract `0xAe7e6CAbad8d80f0b4E1C4DDE2a5dB7201eF1252`, where the liquidity sat from May 2022 to September 2026, is at zero.

## The locks

* **Permanent lock** `0xb061dac5ab20fd7c5b4c4848689e74fa8925e887`: 4,124,604 LCR. Four of the quarterly releases (4,000,000) plus the 124,604 LCR of the contributors who sold part of their tokens in May 2022, locked for good.
* **Team lock** `0x60f43042c8bf7d13264ba47a71c08c337f4b9f0c`: 524,683 LCR remaining of the 1,537,292 locked on 26 May 2022 (founder, team and contributor wallets above 50,000 LCR, six-month lock and then 5% per month).

## What this means in plain words

* 97.3% of the supply is in the contract, in the company's main wallet or in locks. None of it is for sale.
* The tokens that actually change hands are the ones in the pool and in public wallets: about 1.3 million, a little over 1% of supply.
* The company's ability to influence the price is limited to what it publishes: its own purchases of LCR and additions of liquidity, disclosed after the fact. It has never sold.
