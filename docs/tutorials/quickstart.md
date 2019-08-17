# Quick Start

Until Steam Workshop support is added, this is the process for testing your own custom levels:

Switch to the `debug` branch in Chippy's steam Properties.

<img src="https://files.facepunch.com/ryleigh/1b2911b1/betas.png" width="600"/>

Browse to the `custom` folder in Chippy's directory.

<img src="https://files.facepunch.com/ziks/1b2911b1/explorer_tF6TMxGdZU.png" width="600"/>

The "Template" folder contains an example stage (Kraken from the main game), so to get started messing around with your own stuff you should create a copy of that folder (with a name you choose) in the "custom" directory. You can load a custom stage from that directory (but only on the "debug" branch) by setting Chippy's launch options to this:

```
--initial-stage <your stage folder>:<stage index>
```

Each folder contains a list of stages, so the "stage index" at the end tells the game which to load. So for example, to load the Template folder, you will set it to this:

<img src="https://files.facepunch.com/ryleigh/1b2911b1/launch3.png" width="600"/>

For more information you can ask us in the #workshop channel on our Discord:

https://discord.gg/xNguzDH