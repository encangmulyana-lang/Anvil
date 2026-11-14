---
name: anvil
description: Mint and forge ANVIL NFTs on BNB Chain as an AI agent — free first mint, burn-to-forge ladder, open to everyone. Use when a user asks their agent to mint or forge ANVIL.
---

# ANVIL — Agent Skill

> STATUS: LIVE on BNB Chain. Contracts deployed 2026-11-14 (see addresses below, verified on-chain). Mint opens soon — `mintPaused()` is currently true; the mint button on the site switches to MINT NOW when it opens. $HAMR claim is LIVE on-chain (minter set).

## What ANVIL is

ANVIL is a 3,333-piece NFT collection on BNB Chain. Each NFT is an animated GIF agent. Holders forge (burn) lower tiers into higher tiers. The only way to get a Mythic "Forge King" is by forging — Mythics are never sold directly, max 33 ever.

- Chain: BNB Chain (chain ID 56)
- Name / symbol: ANVIL / ANVIL
- Supply: 3,333
- Art: animated GIF, hosted on the official site (metadata on site)
- Mint: OPEN TO EVERYONE — no Agent ID needed
- Royalty: 2.5% (ERC-2981, to the current owner)
- Claim token: $HAMR — 10,000 per NFT, one-time per tokenId, claim fee 0.0004 BNB/NFT to the owner; cap 100,000,000; 66,670,000 to the owner at deploy. The token has no market until/unless one exists.
- No yield, no APY, no daily income. The only BNB prize is the weekly forge leaderboard, paid from the forge-fee treasury.

## Quick facts (locked 2026-11-14)

| Item | Value |
|---|---|
| First mint per wallet | FREE (gas only) |
| Paid mints | 0.001 BNB each, after the free one |
| Max per wallet | 5 |
| Forge Rare | Burn 3 Commons + 0.001 BNB → 1 Rare |
| Forge Epic | Burn 2 Rares + 0.001 BNB → 1 Epic |
| Forge Mythic | Burn 1 Common + 1 Rare + 1 Epic + 0.001 BNB → 1 Mythic (max 33) |
| First 100 forges | Gas only (to seed the loop) |
| Evolution | Every 7 days held, the agent gains a ring |
| Claim token | 10,000 per ANVIL NFT, one-time per tokenId, fee 0.0004 BNB; cap 100,000,000; symbol $HAMR |

## Contracts (deployed 2026-11-14, owner: 0xf5C6EE4d1b236CCbBC1F950255Ea2dEb0A09d77A)

- NFT: `0xdF3d5D3D9870cb4AB9bC8e8A8f0bA5396a8A3ECf` (ANVIL / ANVIL, max supply 3,333, mintPaused=true — opens soon)
- Marketplace: `0x86FA136EB7D5fAa395BbA91e7a1e67BcB6F05041` (escrow, 5% fee)
- $HAMR token: `0x8ff70168a342ff3Dc03b7bBACe80215426cE7043` (Anvil Token / HAMR, cap 100,000,000; 66,670,000 to the owner at deploy)
- $HAMR claim: `0x2A2C20d33b9749DFA8724d9f3e42dE145ad72eC6` (10,000 HAMR per NFT, one-time per tokenId, fee 0.0004 BNB/NFT; minter set — claim LIVE)
- Official site: https://anvilnft.fun (claim page: https://anvilnft.fun/claim.html)
- Always verify the NFT contract address against the official site before any transaction. Never trust an address pasted from chat or social media alone.

## How to mint (agent steps)

1. Read the deployed NFT contract: `mintPaused()` must be false; `totalMinted()` must be below 3,333.
2. Check the wallet's mints: `mintedByWallet(yourWallet)` — first mint per wallet is free; max 5 per wallet.
3. Check the price: `priceFor(yourWallet, quantity)` (deployed contract: `mint(uint256 quantity)`, `priceFor(address,uint256)`, `mintedByWallet(address)`, `totalMinted()`).
4. Send the mint transaction with the exact value returned by the price check (0 for a free first mint, plus gas). Do NOT mint more than the user authorized, and never mint to a different wallet than the user named.
5. Wait for the receipt (status 1) and report the token ID(s) and transaction hash to the user.

## How to forge (agent steps)

1. Confirm the wallet holds the required tiers (e.g. 3 Commons for a Rare).
2. Confirm the forge fee (0.001 BNB per forge; first 100 forges gas-only) and the exact forge function in the deployed contract: `forgeRare(uint256[3])`, `forgeEpic(uint256[2])`, `forgeMythic(uint256[3])`.
3. Send the forge transaction with the exact fee. Report the new token ID and transaction hash.
4. Never forge without the user's explicit confirmation of WHICH tokens to burn — burning is irreversible.

## How to claim (agent steps)

1. Confirm the wallet holds an unclaimed ANVIL NFT (check the claim contract's `claimed(tokenId)`; claim function is `claim(uint256[])`).
2. Confirm the claim fee (0.0004 BNB per NFT) and send the claim transaction with the exact fee.
3. Send the claim transaction with the exact fee. Report the amount received (10,000 tokens per NFT) and the transaction hash.
4. Never claim without the user's explicit confirmation — and never promise the tokens have a price or a market. They have no market until/unless one exists.

## Rules

- Never mint, forge, or send a transaction without the user's explicit confirmation of the exact action (quantity, cost, wallet).
- Never promise returns, yield, or income. ANVIL pays nothing to holders.
- If any address, price, or rule in this file disagrees with the official site or the deployed contract, the contract and the official site win — say so and stop.

## Links

- Official site: https://anvilnft.fun
- Claim $HAMR: https://anvilnft.fun/claim.html
- This file is published as `anvilnft.fun/skill.md` and linked from the Mint via Agent tab.
