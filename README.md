# Trinley Transformation Technical Description

![Sequence](tr2.png)

## System Components

(Some simplifications, such as module files omitted and names changed, for clarity)

||Name/Part|Execution Environment| Description|
|----------|-------------|---------|-----------|
|Trinley - `figures.html`   |Browser  |Store web page where users purchase and receive their figure transformation.|
|Trinley -`trinley.py`  |AVM      |Smart contract used by `figures.html` to track user order state and send orders to `nftgen.py` app. |
|NFTGEN - `nftgen.py`  | AVM |Smart contract that receives the orders and fulfills them by minting and transferring to `trinley.py` app. |
|NFTGEN - `algofilter` |Ubuntu|Watches blockchain for calls to `nftgen.py` contract and executes `cmdrun.mjs` when found.|
|NFTGEN - `cmdrun.mjs` |Node.js|Generates image with `char-gen`, pins to IPFS, and then fulfills the order using `nftgen.py` app.|
|NFTGEN - `char-gen.ls`  | Docker (Sysbox): Node.js | Sysbox container running LiveScript code that uses the p5.js library to generate the image based on the trait definitions, images and code in `char` |
|Trinley - `char`  | `char-gen.ls` | Schema that defines the trait variants, images, rarity, and code used to generate the character image and metadata.|
|NFTGEN - `status.mjs` |  Node.js | Simple status system called by `figures.html` to get updates during order processing.|
|NFTGEN - `algonfts.art` | Browser/Node.js | Interactive tool for uploading images, editing trait definitions and code, saved to the `char` data file.|
