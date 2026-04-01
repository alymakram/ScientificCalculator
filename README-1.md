# BaseCalc × Mini App Builder

> Scientific calculator DApp on Base — every computation triggers an on-chain transaction.  
> Owner: `0xdBF45AF1cD37deBEDD059BEe0525289d2b5E5CF4`

---

## Files

| File | Purpose |
|------|---------|
| `ScientificCalculator.sol` | Smart contract — deploy on Base via Remix |
| `index.html` | Frontend DApp (calculator + mini app builder) |
| `vercel.json` | Vercel static deployment config |
| `README.md` | This file |

---

## Step 1 — Deploy Contract on Base via Remix

1. Go to **https://remix.ethereum.org**
2. Create a new file → paste `ScientificCalculator.sol`
3. **Compile**: Solidity `^0.8.20`, EVM version `paris` (or default)
4. **Deploy**:
   - Environment: **Injected Provider — MetaMask**
   - Switch MetaMask to **Base Mainnet** (Chain ID: 8453)
   - Deploy `ScientificCalculator`
5. Copy the deployed contract address.

---

## Step 2 — Verify on Basescan

1. Go to **https://basescan.org/verifyContract**
2. Paste your contract address
3. Compiler: `0.8.20`, Optimization: **No** (default)
4. Paste the full source from `ScientificCalculator.sol`
5. Submit — you'll get a green ✓ checkmark

---

## Step 3 — Update the Frontend

Open `index.html` and replace line ~220:

```js
const CONTRACT_ADDRESS = "0x0000000000000000000000000000000000000000";
```

with your deployed address:

```js
const CONTRACT_ADDRESS = "0xEbA40303eA3FD39Ccd0F8B6F83428ee1731f73fd";
```

Your live URL: **https://scientific-calculator-two-ivory.vercel.app**
```

---

## Step 4 — Deploy to Vercel via GitHub

1. Push these files to a new GitHub repo:
   ```
   basecalc/
   ├── index.html
   ├── vercel.json
   └── README.md
   ```
2. Go to **https://vercel.com/new**
3. Import the GitHub repo
4. Framework Preset: **Other**
5. Click **Deploy** — done!

---

## Features

### Scientific Calculator
- Basic: `+ − × ÷ mod`
- Scientific: `sin cos tan log ln √ x² x³ xⁿ 1/x |x| n! eˣ ⌊x⌋`
- Constants: `π e`
- **Every calculation logs a transaction on Base**
- Full keyboard support

### Mini App Builder
- Deploy app configs **on-chain** (stored permanently)
- 4 built-in templates: Counter, Token Swap, NFT Card, DAO Vote
- Live HTML preview
- Toggle apps active/inactive
- View all deployed apps with Basescan links

### On-Chain History
- Query your full computation history from the contract
- Paginated, most-recent first

---

## Contract Architecture

```
ScientificCalculator
├── Operations: add, subtract, multiply, divide, modulo, power, sqrt
├── Scaling: all values × 1e6 for decimal precision
├── History: every call stored in history[] mapping
├── MiniApps: deployMiniApp(name, config) stores JSON on-chain
└── Events: Computed | MiniAppDeployed
```

---

## Tech Stack

- **Solidity 0.8.20** — Base Mainnet
- **ethers.js v6** — wallet + contract interaction
- **Pure HTML/CSS/JS** — zero build step, Vercel-ready
- **Base Network** — fast, cheap L2 on Ethereum

---

*Built for `0xdBF45AF1cD37deBEDD059BEe0525289d2b5E5CF4`*
