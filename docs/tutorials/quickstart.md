# Quick Start

Until Steam Workshop support is added, this is the process for testing your own custom levels:

Switch to the `debug` branch in Chippy's steam Properties.

<img src="https://files.facepunch.com/ryleigh/1b2911b1/betas.png" />

Browse to the `custom` folder in Chippy's directory.

<img src="https://files.facepunch.com/ryleigh/1b2411b1/Steam_2019-08-24_02-52-47.png" />

<img src="https://files.facepunch.com/ryleigh/1b2411b1/explorer_2019-08-24_02-50-29.png" />

The `Template` campaign folder contains an example stage (Kraken from the main game).

To begin messing around with your own creations you should make a copy of the `Template` folder (with a name of your choice) in the `custom` directory. 

<img src="https://files.facepunch.com/ryleigh/1b2611b1/explorer_2019-08-26_13-00-50.png" />

To load a stage from a custom campaign (while on the `debug` branch), set Chippy's launch options to this:

```
--initial-stage <your campaign folder>:<stage index>
```

Each campaign folder contains a list of stages, so the "stage index" tells the game which stage to load. So for example, to load the `Template` campaign's first (and only) level:

<img src="https://files.facepunch.com/ryleigh/1b2911b1/launch3.png" />

<br>
Hit `PLAY` to start testing your level.

Some script changes will take effect right away, some will require a **reset**, and some will require a **full reload** to see the results.

Press `R` to quickly reset the stage, and `G` to fully reload it.<br>