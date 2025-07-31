

I cracked Infinity Scripts because the dev ripped me off and its overpriced. All features currently work except for mixer wallets as of 7/31/25.

<video
  src="https://github.com/user-attachments/assets/296e0bce-ba6a-49cc-af4a-c769def6b4f7/crackedinfinity.mp4"
  controls
  style="max-width:100%;height:auto;">
</video>



## MOST UP TO DATE GUIDE
https://infinity-scripts.gitbook.io/infinity-aio



## First Time Installation
1. Install NodeJS (https://nodejs.org/en/download/)
2. Install Dependencies (npm install)
3. Run the project (npm run start)

> **⚠️ DO NOT SHARE YOUR PRIVATE KEYS WITH ANYONE**
> 
> **I SUGGEST HIGHLY TO RUN STEPS 1-6 IN ORDER (4 is optional) FOR BEST RESULTS**
> 
> **STOP USING FREE RPCS AND COMPLAINING NOTHING LANDS, USE A PAID RPC**

## ENV SETUP
RENAME THE .ENV.EXAMPLE FILE TO .env

```
LICENSE_KEY = YOUR INFINITY BUNDLER LICENSE KEY
SIGNER_PRIVATE_KEY = PRIVATE KEY OF DEV WALLET (BASE58 FORMAT - PHANTOM EXPORT FORMAT)
DEV_ADDRESS = WALLET ADDRESS OF DEV WALLET (PUBLIC KEY)
FUNDER_PRIVATE_KEY = PRIVATE KEY OF FUNDER WALLET (BASE58 FORMAT - USED TO FUND SUB WALLETS)
SELLER_PRIVATE_KEY = PRIVATE KEY OF SELLER WALLET (BASE58 FORMAT - FOR TRANSFER SELL MODE ONLY - KEEP 0.1 SOL FOR FEES)
RPC_URL = YOUR RPC URL (HTTP OR HTTPS)
WS = YOUR WS URL (WSS OR WS)
BLOCKENGINEURL = JITO BLOCKENGINE URL (see list below)
JITO_TIP = JITO TIP AMOUNT (SOL)
SELL_TIP = SELL TIP AMOUNT (SOL)
DEVBUY = AMOUNT OF SOL TO BUY ON DEV WALLET
LUT_Address = LOOKUP TABLE ADDRESS (DO NOT EDIT THIS, THE BOT WILL CREATE & UPDATE THIS)
COMPUTE_LIMIT_PRICE = COMPUTE LIMIT PRICE (LAMPORTS) - LEAVE DEFAULT UNLESS EXPERIENCED
COMPUTE_UNIT_PRICE = COMPUTE UNIT PRICE (LAMPORTS) - LEAVE DEFAULT UNLESS EXPERIENCED
TARGET_MCAP = TARGET MARKET CAP FOR AUTO SELL (OPTIONAL) - CURRENTLY PUMPFUN ONLY
NEXTBLOCK_ENDPOINT = NEXTBLOCK TRANSACTION ENDPOINT (OPTIONAL) - SEE ENDPOINT LIST BELOW
NEXTBLOCK_API_KEY = YOUR NEXTBLOCK API KEY (OPTIONAL) - REQUIRED FOR NEXTBLOCK SERVICES
SLIPPAGE = SLIPPAGE FOR BUYING (DECIMAL FORMAT: 0.05 = 5%) - DEFAULT IS 5%
RPC_STAGGER = USE RPC FOR STAGGER BUYS (true/false)
```

**IMPORTANT NOTES:**
- All private keys must be in BASE58 format (Phantom Export Format)
- Keep default values for compute settings unless you understand the implications
- The LUT_Address is automatically managed by the bot - do not modify
- Ensure sufficient SOL balance in seller wallet when using transfer sell mode
- Please overfund wallets to avoid any insufficient fund errors
- DUE TO SLIPPAGE THESE VALUES MAY NOT BE EXACT SO FUND WALLETS WITH EXTRA SOL

## METADATA.JSON (METADATA SETUP)
1. Change the metadata in metadata.json to your desired metadata
2. MAKE SURE TO LEAVE IMAGE VALUE BLANK
3. YOU MUST PUT THE TOKEN IMAGE IN THE /img DIRECTORY 
4. TICKER / SYMBOL MAX 10 CHARACTERS

**ONE IMAGE IN DIRECTORY ONLY (NAME + EXTENSION DONT MATTER NOW)**

## BLOCKENGINE URLS
Pick the closest to your location:
- **🇳🇱 AMSTERDAM (Europe):** amsterdam.mainnet.block-engine.jito.wtf
- **🇩🇪 FRANKFURT (Europe):** frankfurt.mainnet.block-engine.jito.wtf
- **🇺🇸 NEW YORK (North America):** ny.mainnet.block-engine.jito.wtf
- **🇺🇸 SALT LAKE CITY (North America):** slc.mainnet.block-engine.jito.wtf
- **🇯🇵 TOKYO (Asia Pacific):** tokyo.mainnet.block-engine.jito.wtf
- **🇸🇬 SINGAPORE (Asia):** singapore.mainnet.block-engine.jito.wtf

## NEXTBLOCK ENDPOINTS (OPTIONAL):
- **NEW YORK (America):** https://ny.nextblock.io/api/v2/submit
- **FRANCE (Europe):** https://fra.nextblock.io/api/v2/submit

**Selection Guide:**
- Choose the endpoint closest to your physical location or server
- Consider network latency when selecting an endpoint
- For optimal performance, try to match your RPC location with your chosen block engine location

## MODES:

### 1. WALLET GEN
Generates wallets and stores the keypairs to /keypairs directory as JSON files & wallet.txt as pubkey:privkey 

### 2. WALLET UI:
  1. **FUND:** Funds the wallets with SOL (MUST RUN THIS BEFORE BUNDLER)
  2. **BALANCE:** Checks SOL Balance of all Sub Wallets
  3. **TRANSFER TOKENS:** Transfers the token from the SUB Wallets to the DEV wallet
  4. **REFUND SOL:** Returns all SOL from SUB wallets to Dev Wallet! (note 0.001 SOL is left in each wallet to pay rent fees)
  5. **VANITY GEN:** Creates a vanity token address ending in pump saved to /token directory
  6. **CLOSE TOKEN ACCTS:** Closes all token accounts in sub wallet to reclaim rent fees
  7. **EXIT:** Return to main menu

### 3. CREATE LOOKUP TABLE
Creates a lookup table to allow for 20 wallet buys in one go (MUST RUN THIS BEFORE BUNDLER)

### 4. PROFILE GEN
Generates profiles for the sub wallets on pump.fun (Random username + bio + coin holdings)

### 5. Launch UI:
  1. **BUY AMOUNTS:** SET THE BUY AMOUNTS PER WALLET
  2. **LAUNCH TOKEN:** LAUNCH & BUNDLE BUY YOUR TOKEN ON PUMP.FUN
  3. **PNL:** CHECK SUB WALLET PROFIT/LOSS AFTER YOU SELL (MAY BE INACCURATE)

### 6. SELL:
  1. **DUMP ALL:** DUMPS 100% of tokens in every SUB wallet AND DEV WALLET in 1 go 
  2. **DUMP %:** DUMPS A SPECIFIC PERCENTAGE OF TOKENS IN EVERY SUB WALLET AND DEV WALLET
  3. **DELAY SELL ALL:** Sells 100% of supply in all SUB wallets with a delay between each TX 
  4. **DELAY SELL %:** Sells a specific percentage of supply in all SUB wallets with a delay between each TX
  5. **SINGLE SELL (%):** Sells a specific percentage of supply in a single SUB wallet (enter 100 to sell all tokens in a single wallet)
  6. **DEV DUMP:** Transfers all tokens from SUB wallets -> Dev Address from .env then DUMPS 100% of tokens in Dev Wallet

### 7. RAYDIUM:
  1. **CREATE WSOL:** Creates WSOL Accounts for every wallet + dev wallet
  2. **RAY LUT:** Extends LUT to include Raydium Data (SUPER IMPORTANT)
  3. **RAY SELL:** Sells tokens on Raydium (Enter % and include dev (T F)) (T = True, F = False) (0-100 %)
  4. **UNWRAP:** Unwraps WSOL to SOL
  5. **EXIT:** Return to main menu

### 8. EXIT
Exits the program

## NOTES:

1. **WALLETS WILL BE OVERWRITTEN IF YOU RUN WALLET GEN AGAIN SO REMOVE ALL SOL FROM THEM BEFORE RUNNING WALLET GEN AGAIN**

**NOTE:** As of v0.04 All Keypairs/Wallets ever made on the version will be stored in /keypairBackup directory & /walletBackup directory

2. **DO NOT MODIFY MINT.JSON or ANY FILES IN THE /res directory**
3. **DO NOT MODIFY THE NFT STORAGE KEY IN .env**
4. **DO NOT MODIFY THE PUMP-IDL.JSON FILE**

---

> **⚠️ IMPORTANT REMINDERS:**
> 
> - **DO NOT SHARE YOUR PRIVATE KEYS WITH ANYONE**
> - **I SUGGEST HIGHLY TO RUN STEPS 1-6 IN ORDER (4 is optional) FOR BEST RESULTS**
> - **STOP USING FREE RPCS AND COMPLAINING NOTHING LANDS, USE A PAID RPC**
