<div align="center">

# 🐾 ClawPassport

**`.claw` domain NFTs on Solana Mainnet — an on-chain identity primitive for AI agents.**

[![Website](https://img.shields.io/badge/Website-clawpassport.cc-blue)](https://clawpassport.cc/)
[![X](https://img.shields.io/badge/X-@Controlmeiyin-black)](https://x.com/Controlmeiyin)
[![Network](https://img.shields.io/badge/Network-Solana%20Mainnet-9945FF)](https://solana.com/)

</div>

## 🔗 Links

- **Website:** https://clawpassport.cc
- **Mint page:** https://clawpassport.cc/mint.html
- **ICP-filing mirror:** https://mymxt78.com
- **X:** https://x.com/Controlmeiyin
- **Token (CLAW):** `CLAWxJzpyi3aamRmLh7mQKpyURmyBkNCovkHtTpWdUMV`

## ⚙️ Tech Stack

- **Network:** Solana Mainnet
- **NFT standard:** Metaplex Core
- **Wallet library:** `@solana/web3.js` v1.98
- **Hosting:** Cloudflare edge + SSL Full Strict (TLS 1.2+)
- **Supported wallets:** Phantom, Solflare, Backpack, OKX

## 🔐 Transaction model

The mint transaction is built in the browser and signed by the user's wallet. It contains **only** plain `SystemProgram.transfer` instructions plus one optional `Memo` instruction.

**No referral** — one transfer:

| To | Amount | Wallet |
|---|---|---|
| Service wallet | 0.80 SOL | `by6njX5hhApPbNq42C1qioZjkrcDhhRVbjEkdT9Muuk` |

**With a referral** — three transfers plus a memo:

| To | Amount | Wallet |
|---|---|---|
| Referrer | 0.15 SOL | the referrer's own wallet |
| Pool escrow | 0.15 SOL | `D9r9Vd5CymGkjueBYS9gtoLMv9mkNMZZQSzmeuMs5Vma` |
| Service wallet | 0.50 SOL | `by6njX5hhApPbNq42C1qioZjkrcDhhRVbjEkdT9Muuk` |

- The memo is a plain text note such as `claw-lp myname.claw 0.15SOL`, used to reconcile the escrow deposit off-chain.
- Both addresses are fixed constants in the client. They never come from a query string, a referrer, or the server.
- Total paid by the user is always 0.80 SOL, split or not.

What the transaction does **not** contain:

- ❌ no `Approve` / token delegation
- ❌ no `setAuthority`
- ❌ no `closeAccount`
- ❌ no CPI into an unknown program
- ❌ no program deployment
- ❌ no second signer

The `.claw` NFT itself is minted afterwards by our backend to the user's address — the user's wallet signs one payment transaction and nothing else.

## 🌀 Mint flow

1. User connects a Solana wallet (Phantom / Solflare / Backpack / OKX)
2. User types the `.claw` name; the client checks availability via `GET /api/check-name/:name`
3. User clicks Mint; the client builds the transfer transaction table above and asks the wallet to sign it
4. After confirmation, the backend mints the NFT to the user's address and returns its address

## 🪙 CLAW token facts (verifiable on-chain)

- Supply: 500,000,000, minted once, decimals 6
- Mint authority: **revoked (`null`)**
- Freeze authority: **revoked (`null`)**
- Standard SPL Token — no Token-2022 extensions, no transfer fee, no hooks

Note: CLAW is not sold, not distributed, and carries no promise of return. The product being sold on this site is the `.claw` NFT.

## ⚠️ Phantom warning notice

Since `clawpassport.cc` is a **newly registered domain**, Phantom currently shows a domain-level red block ("Request Blocked — dApp could be malicious") on this domain, before the signing screen appears.

- This is Phantom's automatic protection for new domains, not an indication that ClawPassport is malicious — the transaction is the plain SOL transfer described above.
- We have submitted a review request to Phantom Trust & Safety (`review@phantom.com`) with screenshots and the exact transaction structure.
- Until it clears, the same application is served at the ICP mirror **https://mymxt78.com** (softer "new domain" warning only), and Solflare / Backpack / OKX are unaffected.

## 📫 Contact

- **X:** https://x.com/Controlmeiyin
- **GitHub Issues:** open an issue in this repo
- **Email:** fxtaip@gmail.com

## 📜 License

MIT — see [LICENSE](LICENSE).
