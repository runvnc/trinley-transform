# Trinley Transformation Technical Description

![Sequence](tr2.png)

## System Components

(Some simplifications, such as module files omitted and names changed, for clarity)

|Logical Part|Name|Type|Execution Environment| Description|
|----------|-------------|---------------|---------|-----------|
|Trinley App|`figures.html`   |HTML/JavaScript|Browser  |Store web page where users purchase and receive their figure transformation.|
|Trinley App |`trinley.py`  |Stateful Contract |AVM      |Smart contract used by `figures.html` to track user order state and send orders to `nftgen.py` app. |
|NFTGEN  |`nftgen.py`  |Stateful Contract | AVM |Smart contract that receives the orders and fulfills them by minting and transferring to `trinley.py` app. |
|NFTGEN | `algofilter` | Shell (bash)|Ubuntu|Watches blockchain for calls to `nftgen.py` contract and executes `cmdrun.mjs` when found.|
|NFTGEN | `cmdrun.mjs` | JavaScript|Node.js|Generates image with `char-gen`, pins to IPFS, and then fulfills the order using `nftgen.py` app.|
|NFTGEN | `char-gen.ls` | LiveScript/P5.js | Docker (Sysbox): Node.js | |

<!-- |Back End  |algonfts.mjs|JavaScript   |Node.js|       |         |   | -->

