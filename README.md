# AndroidPluginForUnity
Using android studio creating android plugin for Unity. 

## SoftWare

Unity version : 5.4.0p4


## Steps
**1**, Create an empty Android Project.
![unity icon](./image/project1.png)
![unity icon](./image/project2.png)
![unity icon](./image/project3.png)
![unity icon](./image/project4.png)

**2**, Create an empty Android Project.
![unity icon](./image/plugin1.png)
![unity icon](./image/plugin2.png)
![unity icon](./image/plugin3.png)

**3**, Copy the unity classes.jar 
![unity icon](./image/setup1.png)
to
![unity icon](./image/setup2.png)
dictory.

**4**, include the classes.jar 
![unity icon](./image/setup3.png)
![unity icon](./image/setup4.png)
![unity icon](./image/setup5.png)

**5**, editor the android class 
![unity icon](./image/unityplugin1.png)
![unity icon](./image/unityplugin2.png)
![unity icon](./image/unityplugin3.png)

```
package com.simplesdk.onelei.unityplugin;

import com.unity3d.player.UnityPlayer;
import com.unity3d.player.UnityPlayerActivity; //引入头文件

public class UnityPlugin extends UnityPlayerActivity{
    public static int add(int x, int y)
    {
        return  x+y;
    }

    public int Multiply(int x, int y) { return x*y; }

    public static void sendToUnity(){
        String msg = "send successful ~~";
        UnityPlayer.UnitySendMessage("SDKManager","androidMessgae",msg);
    }
}

```
**6**, compile the android project 
![unity icon](./image/build1.png)

Terminal execute 

```
./gradlew buildJar
```
![unity icon](./image/build2.png)
now you can find "onelei_simpleSdk.jar" under the "unityplugin\build\libs".

![unity icon](./image/build3.png)

**7**, editor the unity project, create floder "Plugins/Android" under the "Assets". 
And create "AndroidManifest.xml" under "Plugins/Android".

![unity icon](./image/build1.png)

**8**, editor the "AndroidManifest.xml",in the unity project. 

```
<manifest xmlns:android="http://schemas.android.com/apk/res/android" >
    <application
        android:allowBackup="true"
        android:icon="@drawable/app_icon"
        android:label="@string/app_name"
        android:supportsRtl="true">
        
        <activity 
            android:name="com.simplesdk.onelei.unityplugin.UnityPlugin"  
            android:configChanges="locale|keyboardHidden|orientation|screenSize"
            android:screenOrientation="landscape"
            android:theme="@android:style/Theme.NoTitleBar.Fullscreen" >
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>  
        
    </application>

</manifest>

``` 
 
## How to use

Here are the simple sdk unity project ![simpleSdk](https://github.com/onelei/simpleSdk).

