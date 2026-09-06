# Ex.No: 6 Develop a application to add animations to ImageView,Move,blink,fade,clockwise,zoom,slide operations are perform in android studio.


## AIM:

To develop a application to add animation to imageview,move,blink,fade,clockwise,zoom,slide operation using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:
Step 1: Open Android Studio and then click on File -> New -> New project.

Step 2: Then type the Application name as "androidanimation" and click Next.

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Create a anim folder under res and create the xml files for the animation operators.

Step 7: Add animation operations in MainActivity file.

Step 8: Save and run the application.


## PROGRAM:
```
/*
Developed by: JAYASEELAN U
Registeration Number : 212223220039
*/
```
## Activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="20dp"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <ImageView
        android:id="@+id/imageView"
        android:src="@mipmap/ic_launcher"
        android:layout_width="150dp"
        android:layout_height="150dp"
        android:layout_marginBottom="20dp" />

    <Button
        android:id="@+id/blinkBtn"
        android:text="Blink Animation"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />

    <Button
        android:id="@+id/rotateBtn"
        android:text="Rotate Animation"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />

    <Button
        android:id="@+id/fadeBtn"
        android:text="Fade Animation"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />

    <Button
        android:id="@+id/moveBtn"
        android:text="Move Animation"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />

    <Button
        android:id="@+id/zoomBtn"
        android:text="Zoom Animation"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />

    <Button
        android:id="@+id/stopBtn"
        android:text="Stop Animation"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="10dp" />

</LinearLayout>

```
## MainActivity.java
```
package com.example.animation;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.view.animation.Animation;
import android.view.animation.AnimationUtils;
import android.widget.Button;
import android.widget.ImageView;

import com.example.animation.R;

public class MainActivity extends AppCompatActivity {

    ImageView imageView;
    Button blinkBtn, rotateBtn, fadeBtn, moveBtn, zoomBtn, stopBtn;
    Animation animation;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        imageView = findViewById(R.id.imageView);
        blinkBtn = findViewById(R.id.blinkBtn);
        rotateBtn = findViewById(R.id.rotateBtn);
        fadeBtn = findViewById(R.id.fadeBtn);
        moveBtn = findViewById(R.id.moveBtn);
        zoomBtn = findViewById(R.id.zoomBtn);
        stopBtn = findViewById(R.id.stopBtn);

        blinkBtn.setOnClickListener(v -> startAnim(R.anim.blink));
        rotateBtn.setOnClickListener(v -> startAnim(R.anim.rotate));
        fadeBtn.setOnClickListener(v -> startAnim(R.anim.fade));
        moveBtn.setOnClickListener(v -> startAnim(R.anim.move));
        zoomBtn.setOnClickListener(v -> startAnim(R.anim.zoom));

        stopBtn.setOnClickListener(v -> {
            if (animation != null) {
                imageView.clearAnimation(); // Stop animation
            }
        });
    }

    private void startAnim(int animRes) {
        animation = AnimationUtils.loadAnimation(getApplicationContext(), animRes);
        imageView.startAnimation(animation);
    }
}

```
## AndroidManifest.xml
```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android">

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.Animation">

        <!-- Add android:exported="true" -->
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>

```
## Blink.xml
```
<?xml version="1.0" encoding="utf-8"?>
<alpha xmlns:android="http://schemas.android.com/apk/res/android"
    android:fromAlpha="0.0"
    android:toAlpha="1.0"
    android:duration="500"
    android:repeatMode="reverse"
    android:repeatCount="infinite" />

```
## Rotate.xml
```
<?xml version="1.0" encoding="utf-8"?>
<rotate xmlns:android="http://schemas.android.com/apk/res/android"
    android:fromDegrees="0"
    android:toDegrees="360"
    android:pivotX="50%"
    android:pivotY="50%"
    android:duration="1000"
    android:repeatCount="infinite" />

```
## Fade.xml
```
<?xml version="1.0" encoding="utf-8"?>
<alpha xmlns:android="http://schemas.android.com/apk/res/android"
    android:fromAlpha="1.0"
    android:toAlpha="0.0"
    android:duration="2000"
    android:repeatMode="reverse"
    android:repeatCount="infinite" />

```
## Move.xml
```
<?xml version="1.0" encoding="utf-8"?>
<translate xmlns:android="http://schemas.android.com/apk/res/android"
    android:fromXDelta="0"
    android:toXDelta="200"
    android:fromYDelta="0"
    android:toYDelta="200"
    android:duration="1500"
    android:repeatMode="reverse"
    android:repeatCount="infinite" />

```
## Zoom.xml
```
<?xml version="1.0" encoding="utf-8"?>
<scale xmlns:android="http://schemas.android.com/apk/res/android"
    android:fromXScale="1.0"
    android:toXScale="1.5"
    android:fromYScale="1.0"
    android:toYScale="1.5"
    android:pivotX="50%"
    android:pivotY="50%"
    android:duration="1000"
    android:repeatMode="reverse"
    android:repeatCount="infinite" />

```

## OUTPUT
Blink
<img width="1920" height="1080" alt="Screenshot 2025-10-28 143935" src="https://github.com/user-attachments/assets/eb8dde40-2f2c-4b9e-9e43-2a344e68c432" />
Fade
<img width="1920" height="1080" alt="Screenshot 2025-10-28 143947" src="https://github.com/user-attachments/assets/eba5ec3a-755b-48bf-af1e-06bdbec20401" />
Zoom
<img width="1920" height="1080" alt="Screenshot 2025-10-28 144028" src="https://github.com/user-attachments/assets/f4c94da2-265b-40ee-83a4-4bcd65fa6cda" />
Rotate
<img width="1920" height="1080" alt="Screenshot 2025-10-28 144121" src="https://github.com/user-attachments/assets/73abd1f1-3168-49fc-9509-6b6df3129e28" />
Move
![WhatsApp Image 2025-10-28 at 14 43 49_60836d40](https://github.com/user-attachments/assets/54db1fcf-8fb9-4001-a1c8-4be80ae7f40f)
Stop Animation
<img width="1920" height="1080" alt="Screenshot 2025-10-28 143935" src="https://github.com/user-attachments/assets/84065cd9-2637-4c62-9a73-1da3c67659fb" />




## RESULT
Thus,the experiment Implementation of Animation application using android studio executed successfully.
