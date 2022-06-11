# Trinley Transformation Technical Description

![Sequence](tr2.png)

## System Components

(Some minor simplifications and names changed for clarity)

|Logical Part|Name|Type|Environment/VM Type| Description|
|----------|-------------|---------------|---------|-----------|
|Front End |`figures.html`   |HTML/JavaScript|Browser  |Store web page where users purchase and receive their figure transformation.|
|Front End |`trinley.py`  |Stateful Contract |AVM      |Smart contract used by `figures.html` to track user order state and send orders to `nftgen.py` app. |
|Back End  |`nftgen.py`  |Stateful Contract | AVM |Smart contract that receives the orders and fulfills them by minting and transferring to `trinley.py` app. |
|Back End | `algofilter` | Shell (bash)|Ubuntu|Watches blockchain for calls to `nftgen.py` contract and executes `cmdrun.mjs` when found.|
|Back End | `cmdrun.mjs` | JavaScript|Node.js|Generates image with `char-gen`, pins to IPFS, and then fulfills the order using `nftgen.py` app.|
|Back End | `char-gen` | JavaScript | Docker (Sysbox): Node.js | |

<!-- |Back End  |algonfts.mjs|JavaScript   |Node.js|       |         |   | -->

