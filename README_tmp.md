
Guide on how to add the mobiScan Phonegap plugin to your project(s)


Install using CLI interface (supposed you have already created the app by using CLI interface and added desired platforms)


1. Add plugin to the project with :

	phonegap local plugin add LOCAL_PATH_TO_THE_FOLDER_WITH_PLUGIN_XML (if you are adding from local folder)

or 
	phonegap local plugin add https://...


2. Add a button to index.html which will call the scanner:

	<form style="width: 100%; text-align: center;">
 Ê Ê Ê		 Ê<input type="button" value="Scan Barcode" onclick="scanner.startScanning()" style="font-size: 40px; width: 300px;Êheight: 50px; margin-top: 100px;"/>
 Ê Ê	</form>

3. Upon license purchase, replace the username/key pairs for the corresponding barcode types in the file 'src/com/manateeworks/BarcodeScannerPlugin.java' (Android), 'Plugins/MWScannerViewController.m' (iOS) or 'Plugins/com.manateeworks.barcodescanner/BarcodeHelper.cs (wp8);



Android Note:

You have to import .R file of your project (import YOUR_APP_PACKAGE_NAME.R;) to the 'src/com/manateeworks/ScannerActivity.java'

WP8 Note:

It's seems there's a bug in Phonegap 3.0 so you have to add '<script type="text/javascript" src="cordova.js"></script>' in index.html (or other html files) manually



Manual Install

Android:


1. Create a Phonegap Android app;

2. Copy the folder 'Android/src/com/manateeworks' to your project's 'src/com/' folder;

3. Copy the file 'Android/res/layout/scanner.xml' to your project's 'res/layout' folder;

4. Copy the file 'Android/res/drawable/overlay.png' to your project's 'res/drawable' folder. Do the same for the file in 'drawable-hdpi' folder;

5. Copy the files 'Android/libs/armeabi/libBarcodeScannerLib.so' and 'Android/libs/armeabi-v7a/libBarcodeScannerLib.so' to your project's 'libs/' folder, all the while preserving the same folder structure 

6. Copy the file 'www/MSBScanner.js' to the 'assets/www/js' folder;
 
7. Insert the Scanner activity definition into AndroidManifest.xml:

 	<activity android:name="com.manateeworks.ScannerActivity"
		android:screenOrientation="landscape" android:configChanges="orientation|keyboardHidden"
		android:theme="@android:style/Theme.NoTitleBar.Fullscreen">
	</activity>


8. Insert the MWBScanner.js script into index.html:

	<script type="text/javascript" src="js/MWBScanner.js"></script> 

9. Add a test button for calling the scanner to index.html:

 	<form style="width: 100%; text-align: center;">
        	    <input type="button" value="Scan Barcode" onclick="startScanning()" style="font-size: 20px; width: 300px; height: 30px; margin-top: 50px;"/>
        </form>




10. Add the plugin to 'res/xml/config.xml':

	**For Phonegap 2.x **

	<plugins>
    
		...
		<plugin name="MWBarcodeScanner" value="com.manateeworks.BarcodeScannerPlugin"/>
    
		...
	</plugins>

	**For Phonegap 3 **

	<feature name="MWBarcodeScanner">
       		 <param name="android-package" value="com.manateeworks.BarcodeScannerPlugin" />
   	</feature>




11. Import .R file of your project (import YOUR_APP_PACKAGE_NAME.R;) to the 'src/com/manateeworks/ScannerActivity.java';

12. Upon license purchase, replace the username/key pairs for the corresponding barcode types in the file 'src/com/manateeworks/BarcodeScannerPlugin.java';

13. Run the app and test the scanner by pressing the previously added button;

14. (Optional): You can also replace our default overlay.png for the camera screen with your own customized image;

15. (**For Phonegap 3 **) If notification plugin is not present in project, add it by following instructions from this url:

	http://docs.phonegap.com/en/3.0.0/cordova_notification_notification.md.html

16. If not present already, add camera permission to the AndroidManifest.xml:

	<uses-permission android:name="android.permission.CAMERA" />

17  (**For Phonegap 2.x **) In BarcodeScannerPlugin.java replace org.apache.cordova reference to org.apache.cordova.api :

	Instead:	

		import org.apache.cordova.CallbackContext;
		import org.apache.cordova.CordovaPlugin;

	Use this:

 		import org.apache.cordova.api.CallbackContext;
		import org.apache.cordova.api.CordovaPlugin;

	
	

iOS:

1. Create a Phonegap iOS app;

2. Copy all files from our 'iOS/src' folder to your project's 'Plugins' folder and add them to the project;

3. Copy the file 'www/MSBScanner.js' to the folder 'www/js' . NOTE: You cannot drag & drop directly into the Xcode project... use Finder instead;

4. Insert MWBScanner.js script into index.html:

	<script type="text/javascript" src="js/MWBScanner.js"></script> 

5. Add a test button for calling the scanner to index.html:

 	<form style="width: 100%; text-align: center;">
        	    <input type="button" value="Scan Barcode" onclick="startScanning()" style="font-size: 20px; width: 300px; height: 30px; margin-top: 50px;"/>
        </form>

6. Add the plugin to config.xml (from project root, not the one from www folder):

	**For Phonegap 2.x **

	<plugins>
    
		...
		<plugin name="MWBarcodeScanner" value="CDVMWBarcodeScanner"/>
    
		...
	</plugins>

	**For Phonegap 3 **

	<feature name="MWBarcodeScanner">
        	<param name="ios-package" value="CDVMWBarcodeScanner" />
	</feature>




7. Confirm you have the following frameworks added to your project: CoreVideo, CoreGraphics;

8. Upon license purchase, replace the username/key pairs for the corresponding barcode types in the file Plugins/MWBarcodeScanner/MWScannerViewController.m;


9. Run the app and test the scanner by pressing the previously added button;


10. (Optional): You can replace our default overlay.png and close_button.png for the camera screen with your own customized image;





Windows Phone 8:

1. Add (drag & drop) MWBarcodeScanner folder into the project folder named 'plugins'. If needed, create Plugins folder in project previously;

2. Copy (this time from Windows Explorer, not by way of drag & drop) to the project BarcodeLib.winmd and BarcodeLib.dll to project root;

3. Add (drag & drop) www/MWBScanner.js to www/js/ project folder;

4. Insert MWBScanner.js script into index.html:

	<script type="text/javascript" src="js/MWBScanner.js"></script> 

5. Add a button for calling the scanner to index.html:

 	<form style="width: 100%; text-align: center;">
 
	 	<input type="button" value="Scan Barcode" onclick="scanner.startScanning()" style="font-size: 40px; width: 300px;height: 50px; margin-top: 100px;"/>
 
	</form>

6. Add BarcodeLib.winmd to project references: right click on 'References', 'Add Reference', 'Browse' and choose the file;

7. Add the plugin to config.xml:

	**For Phonegap 2.x **

	<plugins>
    
		...
		<plugin name="MWBarcodeScanner" value="MWBarcodeScanner"/>
    
		...
	</plugins>

	**For Phonegap 3 **

	<feature name="MWBarcodeScanner">
        	<param name="wp-package" value="MWBarcodeScanner" />
	</feature>


Add a notification plugin (if not already present):

	 <plugin name="Notification" value="Notification"/>
 

8. (**For Phonegap 2.9 **) Sometimes a bug occurs in Phonegap 2.9.0 with notification dialogs, making them crash on closing. It may be necessary to make a change in the Plugins/Notification.cs file:

	inside function: void btnOK_Click

	replace the following block:

		  NotifBoxData notifBoxData = notifBoxParent.Tag as NotifBoxData;
                  notifyBox = notifBoxData.previous as NotificationBox;
                  callbackId = notifBoxData.callbackId as string;

                  if (notifyBox == null)
                  {
                      page.BackKeyPress -= page_BackKeyPress;
                  }

	with the one below:

		NotifBoxData notifBoxData = notifBoxParent.Tag as NotifBoxData;
                if (notifBoxData != null)
                    {
                        notifyBox = notifBoxData.previous as NotificationBox;
                        callbackId = notifBoxData.callbackId as string;
                        if (notifyBox == null)
                        {
                            page.BackKeyPress -= page_BackKeyPress;
                        }
                    }

9. Add ID_CAP_ISV_CAMERA capability into WMAppManifest.xml


10. Upon license purchase, replace the username/key pairs for the corresponding barcode types in file Plugins/com.manateeworks.barcodescanner/BarcodeHelper.cs;


11. Run the app and test the scanner by pressing the previously added button;


12. (Optional): You can replace our default overlay.png for the camera screen with your own customized image;
 

