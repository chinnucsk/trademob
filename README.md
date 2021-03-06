# Game Closure DevKit Plugin: TradeMob

This plugin allows you to collect analytics using the [TradeMob](https://trademob.atlassian.net/wiki/display/public/Trademob+Wiki+Homepage) toolkit.  Both iOS and Android targets are supported.

## Usage

Install the addon with `basil install trademob`.

Include it in the `manifest.json` file under the "addons" section for your game:

~~~
"addons": [
	"trademob"
],
~~~

To use TradeMob tracking in your game, import the trademob object:

~~~
import plugins.trademob.tradeMob as tradeMob;
~~~

Then send individual track events like this:

~~~
tradeMob.track("myEvent", {
	"score": 999,
	"coins": 11,
	"isRandomParameter": true
});
~~~

Your events will be tracked as "always" events with action = event name, and a JSON string of the event data in the subId.

You can test for successful integration via the [TradeMob](https://trademob.atlassian.net/wiki/display/public/Trademob+Wiki+Homepage) website after successfully building and running your game on a network-connected device.  Also check the console for helpful debug messages.

You should see console logs like this on iOS:

~~~
2013-07-11 19:14:43.593 mmp[1597:907] TrademobUniversalSDK: Successfully tracked custom event.
~~~

On Android you should see:

~~~
 $ adb logcat | grep -i trademob
E/JS      (14494): {tradeMob} track - success: UpgradePriceGroup subId= {"priceGroup":"B_CHEAPER"}
I/TMUniversalSDK(14494): Sending appstart event to Trademob System.
I/TMUniversalSDK(14494): Sending custom event to Trademob System.
~~~
