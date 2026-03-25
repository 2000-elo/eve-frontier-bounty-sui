# EVE Frontier Bounty Board

A decentralized bounty board for EVE Frontier built on Sui. Players can post SUI-backed bounties on targets, and hunters claim the rewards when kills are verified on-chain. All funds are escrowed in a Move smart contract — no middleman, no trust required.

## How It Works

1. **Post a Bounty** — Connect your Sui wallet, pick a target player, set a reward amount. Your SUI gets locked in a smart contract on-chain.
2. **Hunt** — When the target is killed in EVE Frontier, the kill is recorded on-chain.
3. **Claim** — The hunter calls `claim_bounty` and receives the escrowed SUI directly to their wallet.
4. **Cancel** — If nobody claims before expiry, the poster can cancel and get their SUI refunded.

## Smart Contract

- **Package ID:** `0xcba00d2124a22a21fb5fb3e9c4addc5542339f262a7e48bc9ade02a8c41e1100`
- **Network:** Sui Testnet
- **Module:** `bounty_board::bounty_board`

### Contract Functions

| Function | Who Can Call | What It Does |
|----------|-------------|-------------|
| `post_bounty` | Anyone | Escrows SUI in a new Bounty object |
| `claim_bounty` | Anyone | Claims the bounty, SUI goes to caller |
| `cancel_bounty` | Poster only | Refunds SUI after bounty expires |

## Tech Stack

- **Frontend:** React 19 + Vite
- **Blockchain:** Sui (Testnet)
- **Smart Contract:** Move
- **Wallet:** Any Sui wallet (Slush, Sui Wallet, etc.)
- **Data Source:** EVE Frontier on-chain kill data via GraphQL

## Run Locally

```bash
npm install
npm run dev
```

## Deploy Contract

```bash
cd contracts/bounty_board
sui move build
sui client publish --gas-budget 100000000
```

## Links

- **Live Site:** https://2000-elo.github.io/eve-frontier-bounty-sui/
- **EVE Frontier:** https://evefrontier.com
