# Trinley Transformation Technical Description

![Sequence](tr2.png)

## System Components

(Some names changed for clarity)

|Logical Part|Name|Type|Environment/VM Type| Description|
|----------|-------------|---------------|---------|-----------|
|Front End |`figures.html`   |HTML/JavaScript|Browser  |Store web page where users purchase and receive their figure transformation.|
|Front End |`trinley.py`  |Smart Contract |AVM      |Smart contract used by `figures.html` to track user order state and send orders to the backend contract. |
|Back End  |`nftgen.py`  |Smart Contract | AVM |Smart contract that receives the orders and fulfills them by minting and transferring to front end contract. |
|Back End | `watcher` | Shell/JavaScript|bash/Node.js|Block watcher which executes generates with `char-gen` and then fulfills the order using `nftgen.py`|
|Back End | `char-gen` | JavaScript | Docker (Sysbox): Node.js | |

<!-- |Back End  |algonfts.mjs|JavaScript   |Node.js|       |         |   | -->

