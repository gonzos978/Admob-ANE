admob ane
------
how to add admob native ad in flash air application run on ios and android ?<br/>
this adobe native extention(https://github.com/lilili87222/admob-for-flash/) make it easy,<br/>
and I will show how to use it .<br/>
Make sure you have had admob account(www.admob.com) and created a application before continue.<br/>
download:https://github.com/lilili87222/admob-for-flash/archive/master.zip and get the lib file admob6.11.1.ane<br/>

admob ane 6.12.2 for air mobile ad ,support Interstitial and Banner<br/>
support  landscape and portrait  and autoOrient<br/>
support ios and android<br/>
support all native event<br/>
builed on admob ios sdk 6.12.2 and admob android sdk(Google Play services 4.5) 4.5<br/>


if you want to use it ,you need update  air sdk to  15.0 or higher <br/>

1. Import the API Classes
```
import so.cuo.platform.admob.*;
```
2.we create a simple admob banner ad .Get the Admob instance and set the admob ID <br/>
if want to set admob interstitial with a separate ID ,set the second parameter of setKeys.<br/>
then show the admob banner at bottom center of screen.<br/>
```

var admob:Admob=Admob.getInstance();
admob.setKeys("your banner id");
admob.showBanner(Admob.SMART_BANNER,AdmobPosition.BOTTOM_CENTER);
```

3.create and show interstitial.<br/>
Get the admob instance and set the admob ID,the first ID is the banner ID <br/>
and the second ID is interstitial ID. then call cacheInterstitial to load ad,<br/>
if load success isInterstitialReady return will true,call showInterstitial  to show full screen ad<br/>
```
var admob:Admob=Admob.getInstance();
admob.setKeys("your admob banner","your admob institial");////replace this fake ID with your really ID
if (admob.isInterstitialReady())// check ad has cached ,if true show it
{
     admob.showInterstitial();
}
else
{
    admob.cacheInterstitial();
}
```

if want to add admob in  android application.you need change the application-app.xml file .<br/>
add uses permission and activity
```
<android>
        <manifestAdditions><![CDATA[
			<manifest android:installLocation="auto">
			    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
			    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
			     <application>
 <meta-data android:name="com.google.android.gms.version"
        android:value="@integer/google_play_services_version" />
			  	   <activity android:name="com.google.android.gms.ads.AdActivity" android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize"/>
			     </application>
			</manifest>
		]]></manifestAdditions>
    </android>
```

**more function**
- 1. handler  ad event  like this.
```
admob.addEventListener(AdmobEvent.onBannerReceive,onAdReceived);
```
- 2. get ad size info
```
protected function onAdReceived(event:AdmobEvent):void
{
    if(event.type==AdmobEvent.onBannerReceive){
	trace(event.data.width,event.data.height);
    }
}
```
- 3.get screen size info,old version function
```
admob.getScreenSize()
```


contact:wohaosea@gmail.com
