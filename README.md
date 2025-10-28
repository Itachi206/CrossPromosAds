Steps

1\) Only Import the Package and 

2\) update androidmanifest to give permission

&nbsp;	<!-- Needed to download ads (videos/json) from Firebase or any online server -->

<uses-permission android:name="android.permission.INTERNET" />



<!-- Needed to check if device is online/offline while the game is running.

&nbsp;    This helps when player turns internet ON after launch so ads can download. -->

<uses-permission android:name="android.permission.ACCESS\_NETWORK\_STATE" />





Videos



Update adsInfo.json files when adding new videos and place them in the videos folder 

use handbrake add to convert videos 





🔹 Steps to Update Videos on Firebase Hosting



Go to your project folder (where you already ran firebase init hosting).

Example:



**cd C:\\Users\\prana\\Desktop\\New Project\\Ads**





Put your new ad videos inside the public/videos/ (or public/ if you didn’t make a subfolder).



Example:



public/videos/ads1.mp4

public/videos/ads2.mp4

public/videos/ads3.mp4





⚠️ Important: If you keep the same filename (e.g., ads1.mp4), the new version will overwrite the old one.

If you want versioning (ads1\_v2.mp4), then update your Unity link as well.



Deploy to Firebase Hosting:



**firebase deploy --only hosting**





This will upload the new videos and update the live URLs.



Verify deployment:

Open your browser and check:



https://your-project-id.web.app/videos/ads1.mp4



🔹 Extra Tips



If you want to clear browser cache (so Unity always fetches the latest ads), you can update your hosting config in firebase.json:



{

&nbsp; "hosting": {

&nbsp;   "public": "public",

&nbsp;   "ignore": \["firebase.json", "\*\*/.\*", "\*\*/node\_modules/\*\*"],

&nbsp;   "headers": \[

&nbsp;     {

&nbsp;       "source": "/videos/\*\*",

&nbsp;       "headers": \[

&nbsp;         {

&nbsp;           "key": "Cache-Control",

&nbsp;           "value": "no-cache, no-store, must-revalidate"

&nbsp;         }

&nbsp;       ]

&nbsp;     }

&nbsp;   ]

&nbsp; }

}





Then redeploy with:



**firebase deploy --only hosting**



