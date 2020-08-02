# balena-grandpa 

>  Managing remotely your grandpa's TV enabling him to watch album photos, youtube and initiate telcos (Jitsi meet) without him ever pressing any buttons! 

- Managed through balena.io
- Multiple URLs/webpages to load
- Custom timeout values for each URL
- Support for remote screen control/support/viewing (NoVNC)
- Fast load/runtime due to multi-threaded creation of browser windows ( as a side effect, youtube music can play in background as a google photos slideshow is displayed) 


### Prerequisites

Things you need to deploy this code to your device:

- Sign up for a free account with balenaCloud [here](https://dashboard.balena-cloud.com/signup?utm_source=efp&utm_campaign=balenadash)
- Create an application
- Add your device and download the OS.  Make sure to specify the wifi information needed to connect your device
- Flash your SD card ([balenaEtcher](https://www.balena.io/etcher) is recommended) and boot the device
- Ensure the device shows up in your application dashboard
- Download the code for this project from GitHub, and push to your application, using the [balena-cli tool](https://www.balena.io/docs/reference/cli/)

## Configuration

The following `Enviroment Variables` must be set within Application > Device under *D(x) - Device Variables*:

| Name             | Value                                                        |
| ---------------- | ------------------------------------------------------------ |
| `URL_ONE`        | `https://www.google.com` _[fully qualified URL to load]_            |
| `TIME_ONE`         | `60` _[integer which represents number of seconds to show URL]_  |
| `URL_TWO`        |            |
| `TIME_TWO`       |            |
| `URL_[...]`    | `infinte URLs to load`  |
| `TIME_[...]`    | `corresponding time values for each URL`  |
| `NOVNC_PASSWORD` | `defaultpassword` *[obviously change this to something different]* |
| `TZ` | `America/New_York` *[obviously change this to your timezone, see [Wikipedia](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) for your TZ* |
| | photos configuration |
|ENV VAR	|Description	Options	Default|
|GALLERY_URL	|Gallery URL for google photos, dropbox images, or apple photos		|
|GALLERY_SLIDESHOW_DELAY	|Slideshow delay in milliseconds		10000|
|GALLERY_IMAGE_STYLE	|Contain shows the entire image on the screen. Cover zooms the image filling the entire screen.	contain, cover	cover|
|GALLERY_EFFECT	|Transition effects	fade, horizontal, vertical, kenburns, false	fade|
|CRON_SCHEDULE	|Cron scheduler to reload images to get changes		0 */12 * * *|
|RESIZE_WIDTH	* |Resize image width or height (larger side) in pixels		1000px|
|COMPRESS_QUALITY	* |Image compression	0 - 100	90|


In order to view the device remotely from within your browser, enable the public device URL within the device summary page.  Then, you can simply click the link and login using the password set above.

## Built With

- [ElectronJS](https://electronjs.org) - The web framework used
- [balenaCloud](https://balena.io/) - IoT device management
- [noVNC](https://github.com/novnc/noVNC) - Used to provide remote viewing/support through public device URL (enable in device settings)
- [BalenaDash](https://github.com/balenalabs/balena-dash) - Smart photo slideshow (Google, Dropbox, Apple) 
