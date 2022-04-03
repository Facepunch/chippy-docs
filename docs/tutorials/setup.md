# Getting Started

## Custom Folder

Chippy looks for local custom content in a folder named `custom`, which is in the Chippy Steam folder.

Right-click Chippy in your Steam library, select **Properties**, click the **Local&nbsp;Files** tab, and select **Browse Local Files**.

<img src="https://files.facepunch.com/ryleigh/1b1111b1/Steam_2019-10-11_21-08-35.png" />

Now enter the `custom` folder.

<img src="https://files.facepunch.com/ryleigh/1b1111b1/explorer_2019-10-11_21-11-01.png" />

There should already be an example plugin ([example.zip](https://files.facepunch.com/ryleigh/200115-aZigXG/example.zip)) included.

<img src="https://files.facepunch.com/ryleigh/1b1511b1/explorer_2019-10-15_22-30-50.png" />

Create a copy of the `example` folder, and rename it to whatever you want.

<img src="https://files.facepunch.com/ryleigh/200115-uhSQc2/explorer_2020-01-15_23-57-55.png" />

## Debug Branch

Back in Chippy's properties, click the **Betas** tab and select the `debug` branch.

<img src="https://files.facepunch.com/ryleigh/200116-iwFnBB/Steam_2020-01-16_18-24-02.png" />

While on the `[debug]` branch, the console will display any script errors encountered while running your stage, and `debugText` and `debugVector` properties will display. Also, you can press `G` to completely reload a stage, or hold `H` to show hitboxes.

## Testing Custom Content

Run Chippy and select the **Workshop** tab.

<img src="https://files.facepunch.com/ryleigh/200116-KGRNBe/Chippy_2020-01-16_18-22-34.png" />

On the bottom left, you should see a **Local** section, which displays campaigns in your `custom` folder.

<img src="https://files.facepunch.com/ryleigh/200116-fMCMAS/Chippy_2020-01-16_18-16-23.png" />

## Modifying Content 

Now that you have a copy of the `example` campaign, you can mess with the values without worrying about screwing anything up - to start over, simply make a new copy of it.

### Hotloading

Most of the values you can modify in Chippy scripts are *hotloaded*, meaning you don't need to restart the game to apply them. Simply edit the json file, save your changes, and view them in-game.

Some changes may require you to reset the stage (by holding `R`) to see them take effect.

And a few things will require a full-reload of the stage - accomplish this by pressing `G` while running on the `[debug]` branch.


!!! tip 
    Download a good free text editor such as [VS Code](https://code.visualstudio.com/).