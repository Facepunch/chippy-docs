# Workshop

## Playing Workshop Levels

Visit the [Chippy workshop](https://steamcommunity.com/app/602700/workshop/). <br />
Each workshop item is a campaign containing one or more levels.

[<img src="https://files.facepunch.com/ryleigh/1b1011b1/chrome_2019-10-10_20-50-48.png" />](https://steamcommunity.com/app/602700/workshop/)

Click the **Subscribe** button on campaigns that you want to play, then relaunch Chippy.

<img src="https://files.facepunch.com/ryleigh/1b1011b1/Chippy_2019-10-10_18-58-52.png" />

Visit the **Workshop** tab in Chippy to see campaigns that you're subscribed to.

<img src="https://files.facepunch.com/ryleigh/1b1011b1/Unity_2019-10-10_21-03-58.png" />

Select **Continue** to see the campaign's levels, or **Manage** to unsubscribe.

<img src="https://files.facepunch.com/ryleigh/1b1011b1/Unity_2019-10-10_21-03-58.png" />


## Sharing Your Content

Your custom campaigns (stored locally in Chippy's `custom` folder) will also show up in the **Workshop** tab.

<img src="https://files.facepunch.com/ryleigh/1b1011b1/Unity_2019-10-10_22-21-55.png" />

Click **Continue** to test your campaign, or **Manage** to see more actions.

<img src="https://files.facepunch.com/ryleigh/1b1011b1/Unity_2019-10-10_22-33-59.png" width="66%"/>

Select **Publish** to upload your campaign to the workshop. <br />
Your campaign scripts will be validated, and you can view the log file if there are any errors that prevent the upload.

<img src="https://files.facepunch.com/ryleigh/1b1011b1/Unity_2019-10-10_22-34-23.png" width="75%"/>

After successfully uploading your plugin, select **Continue** and then **View&nbsp;Page**.

<img src="https://files.facepunch.com/ryleigh/1b1011b1/Unity_2019-10-10_22-39-37.png" width="66%"/>

Your campaign won't be visible to anyone else until you change the visibility setting on your workshop item page.

<img src="https://files.facepunch.com/ryleigh/1b1011b1/chrome_2019-10-10_22-34-45.png" width="100%"/>
<img src="https://files.facepunch.com/ryleigh/1b1011b1/chrome_2019-10-10_22-43-36.png" />

### Preview Image

Save a `.jpg` or `.png` image in your plugin's folder. 

<img src="https://files.facepunch.com/ryleigh/1b1211b1/explorer_2019-10-12_15-20-33.png" />

Using an aspect ratio of `4:3` (such as `1440x1080px`) will look best in the grid of workshop icons.

<img src="https://files.facepunch.com/ryleigh/1b1211b1/chrome_2019-10-12_15-29-06.png" />

In your `plugin.json` file, enter the relative path of your image.

<img src="https://files.facepunch.com/ryleigh/1b1211b1/Code_2019-10-12_15-22-11.png" />

```json
"previewImage": "preview.jpg",
```

In this case, it will look for an image named `preview.jpg` in the root of your plugin folder.

### Updating Content

After making changes to the local version of your campaign, select **Manage** and then **Upload&nbsp;Changes**.

<img src="https://files.facepunch.com/ryleigh/1b1011b1/Unity_2019-10-10_22-39-37.png" width="50%"/>

!!! danger "Wiping leaderboards"
	**Any** gameplay-affecting changes you make to your level will likely break existing replays.
    
    You can wipe the slate clean by incrementing the `leaderboardIndex` property in your `plugin.json` file.<br />
    The default value is `0`, so change it to `1` to create the leaderboard for your newly updated version.

    <img src="https://files.facepunch.com/ryleigh/1b1011b1/Code_2019-10-10_22-49-58.png" />





