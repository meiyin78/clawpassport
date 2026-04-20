# clawpassport
ClawPassport — Solana .claw domain NFT minting dApp
# 🐾 ClawPassport

The first **`.claw` domain NFT** on Solana Mainnet — your on-chain identity primitive.

[![Website](https://img.shields.io/badge/Website-clawpassport.cc-blue)](https://clawpassport.cc)
[![Twitter](https://img.shields.io/badge/X-@Controlmeiyin-black)](https://x.com/Controlmeiyin)
[![Solana](https://img.shields.io/badge/Network-Solana%20Mainnet-9945FF)](https://solana.com)

## 🔗 Links

- **Website:** https://clawpassport.cc
- **Mint page:** https://clawpassport.cc/mint.html
- **Twitter / X:** https://x.com/Controlmeiyin

## ⚙️ Tech Stack

- **Network:** Solana Mainnet
- **NFT Standard:** Metaplex Core
- **Wallet Library:** `@solana/web3.js` v1.98
- **Hosting:** Cloudflare edge + SSL Full Strict (TLS 1.2+)
- **Supported Wallets:** Phantom, Solflare, Backpack, OKX

## 🔐 Security

ClawPassport follows a **minimal-permission** transaction model:

- ✅ **No token approvals**
- ✅ **No `setAuthority` calls**
- ✅ **No delegate operations**
- ✅ **No drain patterns**
- ✅ Single `SystemProgram.transfer` of 0.8 SOL from user to service wallet
- ✅ Service wallet is publicly auditable on Solana Mainnet:
- by6njX5hhApPbNq42C1qioZjkrcDhhRVbjEkdT9Muuk

## 🌀 Mint Flow

1. User connects a Solana wallet (Phantom / Solflare / Backpack / OKX)
2. User signs a verification message (`signMessage` — no on-chain effect)
3. User signs a single `SystemProgram.transfer` of **0.8 SOL** to our service wallet
4. Our backend signs and submits a **Metaplex Core NFT mint** transaction to the user's address

That's it. No hidden transactions. No approvals. No surprises.

## ⚠️ Phantom Wallet Warning Notice

Since `clawpassport.cc` is a **newly registered domain**, the Phantom wallet may display a **"request blocked"** warning when interacting with our site. This is Phantom's **automatic protection for new domains**, not an indication that ClawPassport is malicious.

We have submitted a whitelist review request to Phantom. In the meantime, the following wallets work without any warning:

- ✅ Solflare
- ✅ Backpack
- ✅ OKX Wallet

## 📫 Contact

- **Twitter/X:** [@Controlmeiyin](https://x.com/Controlmeiyin)
- **GitHub Issues:** Open an issue in this repo
- **Website:** https://clawpassport.cc

## 📜 License

[MIT License](LICENSE) — see LICENSE file for full text.

---

_Source code will be progressively open-sourced. For early code review access (e.g., security audit teams, wallet review teams), please [open an issue](https://github.com/meiyin78/clawpassport/issues/new) or reach out via Twitter._
