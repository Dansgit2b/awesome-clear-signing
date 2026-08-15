<div align="center">

# Awesome Clear Signing [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of standards, tools, registries, wallets, and knowledge for **Clear Signing** on Ethereum & the EVM — making transaction and message signing human‑readable, so users know exactly what they approve.

**Clear Signing** is the open standard ([ERC‑7730](https://eips.ethereum.org/EIPS/eip-7730)) for turning opaque hexadecimal calldata, EIP‑712 messages, and UserOperations into clear, contextual, human‑readable intent at the moment of signing — the opposite of *blind signing*.

[Website](https://clearsigning.org) · [ERC‑7730](https://eips.ethereum.org/EIPS/eip-7730) · [Registry](https://github.com/ethereum/clear-signing-erc7730-registry) · [Discussion](https://ethereum-magicians.org/)

</div>

---

## Contents

- [What Is Clear Signing?](#what-is-clear-signing)
- [Standards & Specifications](#standards--specifications)
- [Official Resources](#official-resources)
- [Developer Tools & Builders](#developer-tools--builders)
- [Registries & Metadata](#registries--metadata)
- [Wallets & Implementations](#wallets--implementations)
- [Security, Simulation & Verification](#security-simulation--verification)
- [Libraries & SDKs](#libraries--sdks)
- [Articles, Talks & Learning](#articles-talks--learning)
- [Community & Governance](#community--governance)
- [📚 Knowledge: EVM Messages, Transaction & Signing Formats](#-knowledge-evm-messages-transaction--signing-formats)
- [Contributing](#contributing)

---

## What Is Clear Signing?

When you sign a blockchain transaction, your wallet often shows you a wall of hex — `0x38ed1739…` — or a raw EIP‑712 struct with no explanation. **Blind signing** means approving something you cannot read, and it is the root cause of many drainer and phishing losses.

**Clear Signing** solves this by pairing on‑chain data with a machine‑readable *descriptor* ([ERC‑7730](https://eips.ethereum.org/EIPS/eip-7730)) that tells the wallet how to render intent — *"Swap 1.5 ETH for at least 4,200 USDC on Uniswap V3"* — including token amounts, recipients, and network, verifiable right down to the hardware wallet screen.

> **Stewards & contributors** include the Ethereum Foundation, Ledger, WalletConnect, Fireblocks, Sourcify, Trezor, Cyfrin, Zama, Keycard, ZKnox, MetaMask, and Blockaid. Governance of ERC‑7730 was transferred from Ledger to the Ethereum Foundation for long‑term neutrality.

---

## Standards & Specifications

The Ethereum standards that make clear signing possible — the formats being signed and the descriptor format that explains them.

- **[ERC‑7730 — Structured Data Clear Signing Format](https://eips.ethereum.org/EIPS/eip-7730)** — The core standard. JSON descriptors that enrich ABIs and EIP‑712 schemas with formatting + intent metadata. `spec`
- **[ERC‑7730 spec (registry copy)](https://github.com/ethereum/clear-signing-erc7730-registry/blob/master/specs/erc-7730.md)** — Canonical, versioned spec text maintained in the registry repo. `spec`
- **[EIP‑712 — Typed Structured Data Hashing and Signing](https://eips.ethereum.org/EIPS/eip-712)** — Human‑readable typed message signing; the basis for permits, orders, and UserOp hashes. `spec`
- **[EIP‑191 — Signed Data Standard](https://eips.ethereum.org/EIPS/eip-191)** — The `0x19` prefix scheme that namespaces signed data (version `0x01` = EIP‑712). `spec`
- **[ERC‑4337 — Account Abstraction via EntryPoint](https://eips.ethereum.org/EIPS/eip-4337)** — Defines the `UserOperation` — a first‑class clear‑signing target. `spec`
- **[EIP‑7702 — Set EOA Account Code](https://eips.ethereum.org/EIPS/eip-7702)** — Lets an EOA delegate to contract code via a signed authorization tuple. `spec`
- **[EIP‑2718 — Typed Transaction Envelope](https://eips.ethereum.org/EIPS/eip-2718)** — The envelope that makes new transaction types (1559, 2930, 4844, 7702) possible. `spec`
- **[EIP‑1559 — Fee Market](https://eips.ethereum.org/EIPS/eip-1559)** — The default `0x02` dynamic‑fee transaction type. `spec`
- **[Cyfrin EIP/ERC Glossary](https://www.cyfrin.io/glossary/eip-191)** — Plain‑language reference entries for EIP‑191, 712, 4337, and more. `reference`

## Official Resources

- **[clearsigning.org](https://clearsigning.org)** — The initiative's home: overview, ecosystem, build guides, and governance. `official`
- **[ethereum/clear-signing-erc7730-registry](https://github.com/ethereum/clear-signing-erc7730-registry)** — The community registry of ERC‑7730 descriptors, plus the spec. `official`
- **[Ledger Clear Signing Docs](https://developers.ledger.com/docs/clear-signing/references/erc7730-standard)** — The most complete developer documentation for ERC‑7730. `official`
- **[ERC‑7730 Specifications (Ledger)](https://developers.ledger.com/docs/clear-signing/reference/specifications)** — Field‑by‑field reference for writing descriptors. `official`
- **[External Resources (Ledger)](https://developers.ledger.com/docs/clear-signing/reference/external-resources)** — Curated links from the Ledger dev portal. `official`
- **[Ethereum Magicians — ERC‑7730 discussion](https://ethereum-magicians.org/)** — Governance and design discussion thread. `community`

## Developer Tools & Builders

Build, validate, preview, and audit clear‑signing descriptors.

- **[ERC‑7730 JSON Builder](https://github.com/LedgerHQ/clear-signing-erc7730-developer-tools)** — Web tool to generate a valid descriptor from a mainnet contract in minutes. `tool`
- **[LedgerHQ/clear-signing-erc7730-developer-tools](https://github.com/LedgerHQ/clear-signing-erc7730-developer-tools)** — Open‑source Builder, Linter, Tester, and Analyzer for descriptors. `tool`
- **[python-erc7730](https://github.com/LedgerHQ/python-erc7730)** — Python library and CLI to parse, validate, lint, and convert ERC‑7730 descriptors. `tool`
- **[Device preview / emulator (Speculos)](https://github.com/LedgerHQ/speculos)** — Emulate a Ledger device to preview how a descriptor renders on‑screen. `tool`

## Registries & Metadata

Where descriptors and contract metadata live so wallets can resolve intent.

- **[ERC‑7730 Registry](https://github.com/ethereum/clear-signing-erc7730-registry)** — The canonical, open registry of descriptors — submit yours via PR. `official`
- **[Sourcify](https://sourcify.dev)** — Decentralized source‑code & metadata verification; a key input for trustworthy decoding. `security`
- **[Etherscan Verified Contracts](https://etherscan.io/contractsVerified)** — Verified ABIs used to decode calldata into named functions and params. `reference`
- **[4byte Directory](https://www.4byte.directory)** — Reverse‑lookup of 4‑byte function selectors → signatures. `reference`

## Wallets & Implementations

Wallets and platforms that render clear‑signing intent to users.

- **[Ledger](https://www.ledger.com)** — Originated Clear Signing (2023) and ERC‑7730; renders descriptors on‑device. `wallet`
- **[Trezor](https://trezor.io)** — Hardware wallet steward contributing to the standard. `wallet`
- **[MetaMask](https://metamask.io)** — Decoding + simulation and signature‑insight for transactions and messages. `wallet`
- **[WalletConnect](https://walletconnect.network)** — Connection layer surfacing decoded intent across dApps and wallets. `wallet`
- **[Fireblocks](https://www.fireblocks.com)** — Institutional signing with policy + transaction transparency. `wallet`
- **[Keycard](https://keycard.tech)** — Open smartcard hardware wallet contributor. `wallet`

## Security, Simulation & Verification

Complementary layers — decode, simulate, and score a transaction before signing.

- **[Blockaid](https://www.blockaid.io)** — Transaction simulation + threat detection at the point of signature (used by MetaMask, Ledger, Coinbase). `security`
- **[Ledger "Transaction Check"](https://www.blockaid.io/blog/how-blockaid-helps-ledgers-transaction-check-mitigate-blind-signing-risks)** — Blockaid‑powered warnings that mitigate blind‑signing risk. `security`
- **[Transaction Verification vs. Blind Signing](https://www.blockaid.io/blog/transaction-verification-a-solution-to-blind-signing-in-hardware-wallets)** — Why simulation must be cryptographically bound to what's signed. `article`
- **[Tenderly Simulator](https://tenderly.co/transaction-simulator)** — Simulate state changes of a transaction before submitting. `security`
- **[Cyfrin](https://www.cyfrin.io)** — Smart‑contract security education and audits; ERC‑7730 contributor. `security`

## Libraries & SDKs

- **[python-erc7730](https://github.com/LedgerHQ/python-erc7730)** — Reference Python implementation for descriptors. `tool`
- **[viem](https://viem.sh)** — TypeScript library with first‑class EIP‑712 typed‑data signing & hashing. `tool`
- **[ethers.js](https://docs.ethers.org)** — `signTypedData` / EIP‑712 helpers and ABI encoding. `tool`
- **[abitype](https://abitype.dev)** — Strict TypeScript types for ABIs and EIP‑712 typed data. `tool`
- **[permit2 (Uniswap)](https://github.com/Uniswap/permit2)** — Canonical EIP‑712 permit patterns worth clear‑signing correctly. `reference`

## Articles, Talks & Learning

- **[ERC‑7730 v2 & The Evolution of Clear Signing](https://www.ledger.com/blog-the-evolution-of-clear-signing)** — Ledger's overview of the standard's direction. `article`
- **[EIP‑712 explained (blockchain‑wiki)](https://github.com/fullstack-development/blockchain-wiki-en/blob/main/EIPs/eip-712/README.md)** — Deep dive on typed‑data hashing. `article`
- **[Guide for Wallet Devs: EIP‑7702 + ERC‑4337](https://erc4337.substack.com/p/guide-for-wallet-devs-for-getting)** — How the two combine for smart‑account UX. `article`
- **[Is WalletConnect Safe? v2 Security Guide](https://ndlabs.dev/is-walletconnect-safe)** — Threat model behind approval‑based drainer scams. `article`

## Community & Governance

- **[Ethereum Foundation](https://ethereum.org/foundation)** — Now stewards ERC‑7730 governance. `community`
- **[Ethereum Magicians](https://ethereum-magicians.org)** — Standards discussion forum. `community`
- **[ERC‑7730 Registry Issues](https://github.com/ethereum/clear-signing-erc7730-registry/issues)** — Propose changes, report gaps, submit descriptors. `community`

---

## 📚 Knowledge: EVM Messages, Transaction & Signing Formats

*The heart of clear signing is understanding **what** is actually being signed.* This section maps the formats a wallet may ask you to approve — and where clear signing applies to each.

### Two things you can sign

| | Transactions | Off‑chain messages |
|---|---|---|
| **What it is** | State‑changing operations broadcast to the network and mined | Signatures proving intent/authorization, **not** broadcast on their own |
| **Costs gas?** | Yes | No (until relayed/settled by someone) |
| **Examples** | ETH transfer, contract call, token approval | Login (SIWE), `permit`, limit orders, `UserOperation`, EIP‑7702 authorization |
| **Signing schemes** | Type‑prefixed RLP (see below) | EIP‑191 / EIP‑712 |
| **Clear signing via** | Decode calldata + ERC‑7730 descriptor | ERC‑7730 descriptor on the EIP‑712 schema |

### EVM transaction types (EIP‑2718 typed envelope)

Since [EIP‑2718](https://eips.ethereum.org/EIPS/eip-2718), each transaction begins with a **type byte** that selects how the remaining payload is decoded. A leading byte `≥ 0xc0` means a legacy (untyped) RLP transaction.

| Type | Name | Introduced by | Key fields added |
|---|---|---|---|
| `0x00` (legacy) | Legacy | pre‑Berlin | `nonce, gasPrice, gasLimit, to, value, data, v, r, s` |
| `0x01` | Access List | [EIP‑2930](https://eips.ethereum.org/EIPS/eip-2930) | `accessList`, `chainId` |
| `0x02` | Dynamic Fee | [EIP‑1559](https://eips.ethereum.org/EIPS/eip-1559) | `maxFeePerGas`, `maxPriorityFeePerGas` |
| `0x03` | Blob | [EIP‑4844](https://eips.ethereum.org/EIPS/eip-4844) | `maxFeePerBlobGas`, `blobVersionedHashes` |
| `0x04` | Set Code | [EIP‑7702](https://eips.ethereum.org/EIPS/eip-7702) | `authorizationList` (delegate EOA → contract) |

**Anatomy of a call.** For a contract interaction, the human‑meaningful part lives in the `data` (calldata) field:

```
0xa9059cbb                                                        ← 4-byte selector: transfer(address,uint256)
  000000000000000000000000ab5801a7d398351b8be11c439e05c5b3259aec9b  ← arg 1: recipient (address, left-padded to 32 bytes)
  0000000000000000000000000000000000000000000000000de0b6b3a7640000  ← arg 2: amount = 1e18 (1 token, 18 decimals)
```

A blind‑signing wallet shows the raw hex. A **clear‑signing** wallet uses the ABI + an ERC‑7730 descriptor to render: *"Send 1.0 TKN to 0xAB58…AEC9b."*

### Off‑chain message signing schemes

| Scheme | Prefix / format | What it's for | Risk if blind‑signed |
|---|---|---|---|
| **`eth_sign`** | raw 32‑byte hash, no prefix | Legacy raw‑hash signing | 🔴 Highest — can be a disguised transaction hash. Most wallets warn/block. |
| **`personal_sign` (EIP‑191 `0x45`)** | `"\x19Ethereum Signed Message:\n" + len + msg` | Human‑readable string signing, logins | 🟡 Safer, but phrasing can still mislead |
| **[SIWE (EIP‑4361)](https://eips.ethereum.org/EIPS/eip-4361)** | structured `personal_sign` text | "Sign‑In with Ethereum" auth | 🟢 Structured & readable |
| **EIP‑712 (EIP‑191 `0x01`)** | `0x19 0x01 ‖ domainSeparator ‖ hashStruct(message)` | Typed data: permits, orders, UserOps | 🟡 Readable *if* the wallet renders the struct + descriptor |

**EIP‑191 byte layout:**

```
0x19  <1-byte version>  <version-specific data>  <data to sign>
      0x00 → intended validator     (address of validator)
      0x01 → structured data         (EIP-712: domainSeparator)
      0x45 'E' → personal_sign       ("thereum Signed Message:\n" + len)
```

**EIP‑712 digest that actually gets signed:**

```
digest = keccak256( 0x19 ‖ 0x01 ‖ domainSeparator ‖ hashStruct(message) )

domainSeparator = hashStruct(EIP712Domain{ name, version, chainId, verifyingContract, salt })
hashStruct(s)   = keccak256( typeHash ‖ encodeData(s) )
typeHash        = keccak256( "Transfer(address to,uint256 amount)" )
```

Binding to `chainId` and `verifyingContract` is what prevents a signature from being replayed on another chain or contract — a core reason EIP‑712 is preferred for anything with value.

### ERC‑4337 UserOperations

A `UserOperation` is a **pseudo‑transaction** for smart accounts. It is signed as an **EIP‑712 hash over the EntryPoint's domain** (so it depends on `chainId` and the EntryPoint address to prevent replay), then bundled and submitted by a bundler. Fields a clear‑signing wallet should surface include `sender`, `callData`, `callGasLimit`, `maxFeePerGas`, `paymasterAndData`, and `nonce`.

```
UserOpHash = keccak256( 0x19 ‖ 0x01 ‖ entryPointDomainSeparator ‖ hashStruct(userOp) )
```

### EIP‑7702 authorizations

EIP‑7702 lets an EOA sign an **authorization tuple** `(chainId, address, nonce)` delegating its code to a contract. It is signed as `keccak256(0x05 ‖ rlp([chainId, address, nonce]))`. Because signing one grants a contract the power to act *as your account*, clear rendering of the delegate address is safety‑critical.

### The ERC‑7730 descriptor (how intent is defined)

A descriptor is JSON with two halves — **`context`** (what schema it binds to: an EVM contract ABI or an EIP‑712 domain) and **`display`** (how to format each function/message into fields):

```json
{
  "context": {
    "contract": { "abi": "…", "deployments": [{ "chainId": 1, "address": "0x…" }] }
  },
  "display": {
    "formats": {
      "transfer(address,uint256)": {
        "intent": "Send",
        "fields": [
          { "path": "to",     "label": "To",     "format": "addressName" },
          { "path": "amount", "label": "Amount", "format": "tokenAmount",
            "params": { "tokenPath": "@.to", "nativeCurrencyAddress": "…" } }
        ]
      }
    }
  }
}
```

The wallet resolves the descriptor for the target contract/message, applies each field `format` (e.g. `tokenAmount`, `addressName`, `date`, `amount`, `raw`), interpolates on‑chain values, and shows the result — the same on a phone screen and a hardware‑wallet display.

### Reader's checklist before you sign

- 🔎 **Is it a message or a transaction?** A raw‑hash `eth_sign` prompt is a red flag.
- 🏷️ **Does the intent match the app?** "Approve unlimited" on a page you thought was a swap = stop.
- 🔗 **Right `chainId` and `verifyingContract`?** Domain mismatch = possible replay/phishing.
- 💰 **Amounts, decimals, recipient** rendered in human units — not raw `uint256`.
- ✅ **Simulated + verified?** Clear signing + simulation (Blockaid/Tenderly) is defense in depth.

---

## Contributing

Contributions welcome! Please read the (forthcoming) `CONTRIBUTING.md`. In short:

- One link per entry, `Name — one‑line description.` with a trailing category tag.
- Keep it **relevant to clear signing** on Ethereum/EVM (standards, tools, registries, wallets, security, learning).
- No dead links, no pure marketing. Prefer primary sources (specs, repos, docs).
- Open a PR — descriptor submissions for real contracts go to the [ERC‑7730 registry](https://github.com/ethereum/clear-signing-erc7730-registry), not here.

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, contributors have waived all copyright and related rights to this work. See [`LICENSE`](LICENSE).
