# Trinley Transformation Technical Description

![Sequence](tr2.png)

## System Components

(Some names changed for clarity)

|Logical Part|Name|Type|Environment/VM Type| Description|
|----------|-------------|---------------|---------|-----------|
|Front End |figures.html   |HTML/JavaScript|Browser  ||
|Front End |trinley.py  |Smart Contract |AVM      | |
|Back End  |nftgen.py  |Smart Contract | AVM | |
|Back End | watcher | Shell/JavaScript|bash/Node.js| |
|Back End | char-gen | JavaScript | Docker (Sysbox), Node.js | |

<!-- |Back End  |algonfts.mjs|JavaScript   |Node.js|       |         |   | -->

