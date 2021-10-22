# Adding content to Signage Playlist

Adding content to a Signage Playlist installation is easy and very flexible. You can configure playlists exactly how you want them to play. 

Triggers can even enhance this further as you can use external factors to influence what should play on the screen.

?> To read more about the available triggers and how to use them, head over to [Using Triggers](/apps/signage/using-triggers.md) documentation.
## Add media items
You can add media to a Signage Playlist by clicking on the `Content` tab inside your installation

To add media items to a playlist you need to press the `+ Add` button next to *any* `items` section in the playlist. Either inside a trigger item or in the generic items playlist.

By pressing the `+ Add` button a small form will show up.

![](/assets/empty-item.png ":size=500")

For `item type` you should select `MEDIA` and the item will expand to show more options

![](/assets/media-item.png ":size=500")

From here you click the `Pick an asset` icon, this will open the media library. The media library will show all content you've uploaded to your organization, but you can also upload new content from here.

![](/assets/media-library.png ":size=500")

Choose the item you want to add to your library, in this case, we're going to select a static image. This will add an extra required field to the form to input the time you want this image displayed, in ms, or milliseconds (1 second is 1000ms). Once you've filled it out, the item is complete

![](/assets/filled-item.png ":size=500")

Now you press the `Save all changes` button on the right of the screen. 

?> If you add a video you don't need to enter the time it will play, by default the video will play exactly once, and then move on to the next item.

## Adding Screen Apps
Next to media you can also add Screen Apps to the playlist, which you can configure in-line in the playlist. 

?> To learn more about Screen Apps, check the [Building your first screen app](/app-development/building-your-first-screen-app.md) guide.

To add a screen app, select `GRIDAPP` from `Item type` on the content page. 

Then the first field is `Application`, which can be any Screen App available in your organization. So this can be either a pre-built marketplace app or one you've deployed yourself.

The configuration of the app depends fully on what application you choose, so check the related documentation for any marketplace app. However, there's one field that needs filling for any application, and that is the duration you want the Screen App to be on screen. This needs to be filled in ms, or milliseconds (1 second is 1000ms).

## Adding an Installation (Nested Installations)
A powerful feature of the Ombori Signage Playlist is that you can also add another installation as a playlist item.

To add an installation, select `Installation` from the `Item type` on the content page. 

The first field is `Installation`, which can be any installation available in your organization. Be it a signage playlist or a different application type, you have the option to select any existing installation.

Additionally, we need to specify the `Next Item Trigger`, which is the trigger to play the next item. For Signage Playlist installations, select `Installation Trigger`, it has built-in logic to detect the end of playback. For other installations, select `Duration`, and specify the length of time in milliseconds you want to show the specified installation on the signage.

The Signage Playlist handles caching, and auto-updates itself when at least one of its nested installations has a new deployed build.

After you've configured your Screen Application, you can press the `Save all changes` button on the right of the screen.

## Publishing to device
Now that you have content in your playlist you can publish the playlist to your Signage Playlist device. If you don't have a device attached to your installation, do so now. 

?> To learn more about how to add a device to the Ombori grid, visit the [Add a device](/general/adding-device.md) documentation.

After you've pressed `Save all changes` a new button appears, this is the `Publish` button.

![](/assets/publish-button.png ":size=400 :no-zoom")

Once you press this button, the signage application will start building, and then will be automatically downloaded to any device added to the installation. 

You will notice on the screen of your device a progress bar will display notifying you of it downloading the assets, and then it will start showing the content you've configured.