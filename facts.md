# The Glass Forest — fact inventory

Every interesting finding, with numbers and evidence links.

## Headline stats

- Scanned 3,759,607,584 signature records from 1,412,921,348 transactions (760 GB, ~30 min on 32 cores, local Bitcoin Core node: block files + txindex)
- 475 verified nonce-reuse findings across 432 addresses
- 3,207 keys total: 1,486 from same-key + transitive nonce analysis, plus 1,721 net-new from the cross-key census
- 2,354.28513476 BTC spent after exposure; 255.73643522 BTC more inside exposure blocks; 8,405.04393680 BTC lifetime
- 0 BTC in any affected address at snapshot (block 962,942, 2026-08-17)
- ~85% of the 475 keys leaked in 2012–2015; the newest leaked in 2026
- Every key recovered in memory and verified d·G == pubkey; no private keys stored anywhere; balances matched the node's UTXO set with zero mismatches

## The wallet that never noticed

- Address: [1BMzWp77j7x3GKDYNbCP3df7YG3UEw1vVE](https://mempool.space/address/1BMzWp77j7x3GKDYNbCP3df7YG3UEw1vVE)
- Exposed 2013-02-12 (block 220,772): two inputs of [one transaction](https://mempool.space/tx/6c2d0bbb87350cd18d93ede269817767b84715a6292a022c68b327f704ce486f) signed with the same nonce (identical r, different s) — key computable by anyone from that block on
- [533.82 BTC spent four days later](https://mempool.space/tx/f1021b6e62eccb35c88cb4e88ad34133d8121c065802d8eaf609664c621f6f03); ~1,930.26 BTC moved post-exposure; 6,622.25 BTC lifetime; last seen spending 9,749 sats in December 2025
- Balance curve: 619.40 BTC peak (2013-01-20) → 131.18 (exposure day) → 42.71 (+1 month) → 0.00 (May 2013)
- Accounts for 82% of the audit's 2,354 BTC spent-after-exposure total
- The exposing transaction was publicly dissected on [bitcointalk](https://bitcointalk.org/index.php?topic=919194.0) in January 2015 (Evil-Knievel cites it by txid as the same-r/different-s example)

## One nonce, 2.55 million signatures

- Constant nonce k = (n−1)/2; signature fingerprint r starts `0000…3b78ce…`
- July 2015 dust-sweep trick: exceptionally short DER encoding saved fees; known constant, so one signature exposes the key
- 2,552,742 signatures → **1,956 distinct private keys** recovered and verified; 1,034 of them signed only once
- Only 237 of the 1,956 were already proven by earlier passes; the census found the other 1,719
- Evidence: [an early cluster transaction](https://mempool.space/tx/05f331dfd6e16ecb28eb05f2b4cb0ffa25e82ec6489a5f37be3242a8e044faa9), [a November 2024 puzzle transaction](https://mempool.space/tx/2646b0f5633b45c5e2acb0eec639dea8da92d5d17a16fa9479ef988bede06d4a)
- Publicly documented since 2015: [the most repeated r value on the blockchain](https://bitcointalk.org/index.php?topic=1118704.0)

## Brainwallets

- 14.34-million-word dictionary → 6,439 passwords hit → 6,367 funded addresses
- [`sha256("password")`](https://mempool.space/address/16ga2uqnF1NqpAuQeeg7sTCAdtDUwDyJav) — funded
- [`sha256("correct horse battery staple")`](https://mempool.space/address/1JwSSubhmg6iPtRjtyqhUYYH7bZg3Lfy1T) — funded
- [`sha256("satoshi nakamoto")`](https://mempool.space/address/1Q7f2rL2irjpvsKVys5W2cmKJYss82rNCy) — funded

## Timestamp keys

- 26 funded addresses whose private keys are Unix timestamps (2009–2029)
- February 2009, weeks after launch: [14xTHSRP6vbJv3xcXih2EnHYYCopR5ghJJ](https://mempool.space/address/14xTHSRP6vbJv3xcXih2EnHYYCopR5ghJJ)
- March 2010, received 7.21 BTC: [137ZSN8hYxMRqwSJErvyTnu3jsh5LLwMGa](https://mempool.space/address/137ZSN8hYxMRqwSJErvyTnu3jsh5LLwMGa)
- Future dates: [September 2026](https://mempool.space/address/1CZHMQ1JQxat7j6JCQ1yiarMrc1eoU3y9w), [August 2027](https://mempool.space/address/16v3NVGXBos3rUrXvPc9b4W3ucRzgS96ue), [June 2029](https://mempool.space/address/1DEWpQMzPjPsjszPXHHhVpYi65zX6xdUit), [September 2029](https://mempool.space/address/1AGsfSTyPEp4FYpJgQsUJ9rndVtpDpE8kg)
- Holidays: [New Year's Day 2022](https://mempool.space/address/144b482SWaZEHabsciLnMi7JKYGus7WDFr), [Christmas Day 2023](https://mempool.space/address/13mGNhszax9hRcgbBw2nAjiqs6fykEFTiZ)

## Small scalars

- 370 distinct keys with d ≤ 2^24, including the 2015 puzzle keys
- d = 1 backs both [`1EHNa6Q4Jz2uvNExL497mE43ikXhwF6kZm`](https://mempool.space/address/1EHNa6Q4Jz2uvNExL497mE43ikXhwF6kZm) and the BIP-173 [example bech32 address](https://mempool.space/address/bc1qw508d6qejxtdg4y5r3zarvary0c5xw7kv8f3t4) — still dusted and swept the week of the snapshot
- [keys.lol](https://keys.lol/) enumerates every possible private key as an infinite book

## Vanity nonces

- k = 1337 ×5 ([example](https://mempool.space/address/1M8qDbYTeo1AxRinLJP6vxFkU92tGSHoxy))
- k = 12345678 ×6 ([example](https://mempool.space/address/1HXSnvNGK8oYQCyLDkpHNZ2sWPvFsYQcFU))
- k = 7 ×16 ([example](https://mempool.space/address/19jY65TFM1Rfhew7iWhLh5Eo3XQRHzyw7Q))
- k = 111 ×5 ([example](https://mempool.space/address/1D1jAubLTtS7PAosNkhnFa8UUY7eLCkPme))
- k = 133337 and k = 1333337, one each
- 336 signatures total with |k| ≤ 2^24

## Keys posted as public data

- 5,095 distinct private keys embedded in the chain as data, each matching a public key used on chain (OP_RETURNs, test strings, puzzle material)
- [One transaction](https://mempool.space/tx/7342ee671991a000081ec7b248772e2ae0197252e90a862c4ba18c7f159501f0) embeds `sha256("")` as a key; it controls a funded address

## Stranger corners

- Oldest exposure in the audit: [`1A8TY7dxURcsRtPBs7fP6bDVzAgpgP4962`](https://mempool.space/address/1A8TY7dxURcsRtPBs7fP6bDVzAgpgP4962) reused a nonce in block 121,481 (May 2, 2011), 20 months before the attack's first public write-up; same key still spending in April 2026, 0.77 BTC since the leak
- Unluckiest week: [`1BTrViTDXhWrdw5ErBWSyP5LdzYmeuDTr2`](https://mempool.space/address/1BTrViTDXhWrdw5ErBWSyP5LdzYmeuDTr2) leaked 8 times in 11 days in March 2016, 7 of them inside six hours; 160.27 BTC moved after exposure
- Undocumented burst: 13 findings first exposed across 2022 and early 2023, 11 of them packed into the same weeks of August–September 2022
- 71,749 legacy SIGHASH_SINGLE signatures commit to the constant z = 1 and are replayable against another compatible UTXO of the same key; [one address](https://mempool.space/address/15iwPhxErFDyQTJew81ok9hCbQNhyWuXq1) has 7
- 287 signatures from at least 46 keys used k = 1 ([example](https://mempool.space/address/1KonZ9DA1eW4rW6eKzjhw2yTjjvXEDTKia)); one signature used k = d, its own private key as the nonce, in [block 450,655](https://mempool.space/tx/ee3a72eaeb28bdc5b5dd550de526e167b5e9d35e4a42070bd9d5fde2bcb4fea3)
- Cross-key join: every signature's r matched against all 135.7 million signing keys with 2+ signatures, plus a filtered pass over the rest; [one 2020 spend](https://mempool.space/tx/ae151af74211c679c13054bb5a96c7c8296797ae8c601b34fe226230988e2c1a) used a 2015-compromised key's private scalar as its nonce
- Deep sample: in 2,000,000 keys, 24 more fell outside the primary grouping — 13 repeated-nonce cases, 7 with nonces differing by exactly 1, 4 by a lattice (HNP) attack

## The Android bug's footprint

- 9 of the 475 findings first exposed in the four weeks around the 2013-08-11 Android SecureRandom alert
- [17HHdLh4oXncuTejALwC6fgArVqPUxh2Sr](https://mempool.space/address/17HHdLh4oXncuTejALwC6fgArVqPUxh2Sr) — exposed August 6, five days before the alert
- [1HgRa96fuHCde6Rie4nwhaz1hZR694X4wj](https://mempool.space/address/1HgRa96fuHCde6Rie4nwhaz1hZR694X4wj) — exposed September 4, three weeks after

## What held up

- Taproot/Schnorr: zero same-key nonce reuse, zero key-path k = d across 352 million outputs
- Mainstream wallets with deterministic nonces (RFC 6979 for ECDSA, BIP340 for Schnorr) appear nowhere in the findings
- Chain-wide scans found zero signatures with k = s, zero with k = r, zero nonce-chaining relations, zero nonces derived from block hashes or merkle roots (5.7 million candidates, orphan blocks included)

## So were the coins stolen?

- Unknown from chain data; the 2,354.29 BTC is value in motion while keys were public, not proof of theft
- [17.23643265 BTC in a 3-of-5 multisig](https://mempool.space/address/31oSGBBNrpCiENH3XMZpiP6GTC4tad4bMy) (881 UTXOs): one participating key leaked at the empty address [`19zqrJ8K9LLQJzv5do4Di9GrWi7fAjCwcy`](https://mempool.space/address/19zqrJ8K9LLQJzv5do4Di9GrWi7fAjCwcy); spending still needs three signatures. Evidence: [transaction 1](https://mempool.space/tx/74816056467f652d2fb4e21c00abce572e244a1ed75b77724d0133b7e75c27dc), [transaction 2](https://mempool.space/tx/f4f669130bc9cb8007da39ffd03148d1263c991b875ce0c11f34e45ed683751e)
- 18 hashlocked outputs, 859,986 sats: preimages public, but every reviewed spend path still needs an uncompromised signature

## The hunters

- Puzzle #66 (September 2024): solver broadcast the 6.6 BTC claim; a bot [replaced the unconfirmed transaction with a higher-fee copy](https://mempool.space/tx/57a88f47e4c047740b782a5562fca143ce85de0373cbff3a7d406e9ae7fc2f5f) and took 5.94 BTC. The next prize solver [skipped the public mempool entirely](https://mempool.space/tx/0be77ec8bec331da8750c8b715085c6cf6c374ca31f829a515c62b9846e32986)
- The "bus × 12" seed (August 12, 2026): [`bc1qqhx2nydhdw5qhruslhwf74hdjq88lh662m8xy2`](https://mempool.space/address/bc1qqhx2nydhdw5qhruslhwf74hdjq88lh662m8xy2), provably derived from the seed phrase "bus" × 12 (BIP-84 index 1). Four deposits totaling 1.771 BTC in one block; every sweep confirmed in that block paid [100% of the money as miner fees](https://mempool.space/tx/1d2e80606dbb09a49e0c06779d5bc33ac68523d89eee474b2812c8a0d35dc090). Even a 546-sat dusting two days later was swept. Sources: [@ottosch_](https://x.com/ottosch_/status/2087534668945989928), [@narcelio](https://x.com/narcelio/status/2087597065354322333)
- The BIP-173 example address (d = 1) still receives dust every week; bots sweep deposits within minutes
- The smallest post-exposure spend in the audit is [a single satoshi](https://mempool.space/address/1817ZWpXpXek7WxvUQ1Seh3jEQ2KSKsRWw)

## The chain as a message board (anyone-can-spend, unspent, 15,285 sats total at block 963,084)

- The PortlandHODL open letter ([one April 2026 transaction](https://mempool.space/tx/7372defce8713521da62fe0284b4fd23c3f33c8a7a23275788b50762db8fc0a3), seven 21-sat outputs):
  - "PortlandHODL here -> MARA: I resign effectively when this TX is mined."
  - "Gratitude is extended to Fred Thiel and Mike."
  - "Slipstream is freedom and censorship resistance."
  - "Slipstream should be shuttered, nobody with competence to maintain remains."
  - "The flame of innovation burns bright in my soul and a hunger for success remains"
  - "Listening to Linkin Park, reminiscing all that has transpired during the last 2 years. A lot."
  - "Praise the Lord and may Christ guide me."
- [A July 2026 transaction](https://mempool.space/tx/84b577cb8c5862ff16671db007b5690ff0929fea60c39c1437f25ee0c2b9c299) with 88 outputs ends in a 4,096-sat output whose entire locking script is the text "Money money money"; its OP_RETURN reads "You owe me money"
- "A pagar las deudas!" and one more bare-push output (21 sats each)
- 11,173 bare OP_TRUE outputs: 11,000 holding one satoshi each and 173 empty; every bigger one was already swept long ago

## The canon (history of exposed keys, with links)

- Dec 2010: fail0verflow shows Sony signed PS3 software with a constant "random" number, recovering its root key — [the 27C3 "Epic Fail" talk](https://media.ccc.de/v/27c3-4087-en-console_hacking_2010)
- Jan 2013: Nils Schneider publishes the first public Bitcoin key recovery from reused nonces ([archived copy](https://allprivatekeys.com/random-vulnerability)); his example key signed **76 times with the same nonce** — [`1BFhrfTTZP3Nw4BNy4eX4KFLsn9ZeijcMm`](https://mempool.space/address/1BFhrfTTZP3Nw4BNy4eX4KFLsn9ZeijcMm), [his example transaction](https://mempool.space/tx/9ec4bc49e828d924af1d1029cacf709431abbde46d59554b62bc270e3b29c4b1)
- Aug 2013: Android SecureRandom collides nonces chain-wide — [bitcoin.org alert](https://bitcoin.org/en/alert/2013-08-11-android)
- Dec 2014: blockchain.info's RNG breaks for hours; white-hat johoe sweeps hundreds of BTC and returns it — [his thread](https://bitcointalk.org/index.php?topic=581411.0), [Finance Magnates](https://www.financemagnates.com/cryptocurrency/news/blockchain-info-hacker-johoe-returns-255-btc-says-1019-addresses-compromised/)
- 2015: the 1,000 BTC puzzle ([announcement](https://bitcointalk.org/index.php?topic=1306983), [funding transaction](https://mempool.space/tx/08389f34c98c606322740c0be6a7125d9860bb8d5cb182c02f98461e5fa6cd15)); [#135 fell in July 2026](https://privatekeys.pw/puzzles/bitcoin-puzzle-tx), 13.5 BTC to a solver with 200 GPUs
- 2015: Castellucci's DEF CON talk, [Cracking Cryptocurrency Brainwallets](https://rya.nc/files/cracking_cryptocurrency_brainwallets.pdf)
- 2016: [The Bitcoin Brain Drain](https://jbonneau.com/doc/VBCKM16-FC-bitcoin_brain_wallets.pdf) counts 884 live brainwallets and documents the competing "drainer" bots
- 2018: Bitcoin Core adopts low-r signature grinding ([PR 13666](https://github.com/bitcoin/bitcoin/pull/13666)) — the 2015 trick done safely, fresh nonce each try
- 2019: Breitner and Heninger compute hundreds of keys from biased nonces ([Biased Nonce Sense](https://eprint.iacr.org/2019/023)); ISE's Ethercombing finds the "Blockchain Bandit" ([paper](https://www.ise.io/casestudies/ethercombing/))
- 2023: Milk Sad's broken `bx seed` ([CVE-2023-39910](https://milksad.info/), [address lookup](https://milksad.info/lookup.html)); Randstorm's weak browser wallets ([Unciphered](https://www.unciphered.com/disclosure-of-vulnerable-bitcoin-wallet-library-2/))
- 2024: Dark Skippy, seed exfiltration inside signatures ([disclosure](https://darkskippy.com/)); never seen in the wild
- 2025: a known linear relation between two nonces is enough to recover the key in closed form ([Gilchrist et al., ePrint 2025/705](https://eprint.iacr.org/2025/705)); this audit's sample found 7 keys whose nonces differed by exactly 1
- 2026: the Coldcard entropy flaw — seeds leaked at generation time for five years ([incident report](https://wizardsardine.com/blog/coldcard-vuln-deep-dive/), [official advisory](https://blog.coinkite.com/coldcard-mk3-seed-generation-warning/)); the coordinated sweep is itself on-chain: 517 drain transactions and 134.9 BTC of dormant coins in [block 960,185](https://mempool.space/block/00000000000000000000197fc747ebee54c64dd263e9e00c4e88902165085e57)

## Method

- 760 GB of chain data, about 30 minutes on 32 cores, local Bitcoin Core node (block files + transaction index)
- Every reported key recovered in memory and verified against the on-chain public key; no private keys stored in any artifact
- Balances from a local chain scan and transaction index, matched against the node's UTXO set with zero mismatches
- Full address table + CSV download on the site
