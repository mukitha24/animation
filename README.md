# Ex.No: 11 Develop a application to add animations to ImageView,Move,blink,fade,clockwise,zoom,slide operations are perform in android studio.


## AIM:

To develop a application to add animation to imageview,move,blink,fade,clockwise,zoom,slide operation using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:



## PROGRAM:
```
/*
Program to display animation operation”.
Developed by:MUKITHA V M
Registeration Number :212223040119
*/
```
## MainActivity.java
```
package com.example.animation;

import android.os.Bundle;
import android.view.View;
import android.view.animation.Animation;
import android.view.animation.AnimationUtils;
import android.widget.Button;
import android.widget.ImageView;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    // Declare variables for ImageView and Buttons
    private ImageView imageView;
    private Button blink, rotate, fade, move, slide, zoom, stop;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Initialize ImageView and Buttons using their IDs
        imageView = findViewById(R.id.imageview);
        blink = findViewById(R.id.blink);
        rotate = findViewById(R.id.rotate);
        fade = findViewById(R.id.fade);
        move = findViewById(R.id.move);
        slide = findViewById(R.id.slide);
        zoom = findViewById(R.id.zoom);
        stop = findViewById(R.id.stop);

        // Set up click listeners for each button to start corresponding animations
        createAnimation(blink, R.anim.blink);
        createAnimation(rotate, R.anim.rotate);
        createAnimation(fade, R.anim.fade);
        createAnimation(move, R.anim.move);
        createAnimation(slide, R.anim.slide);
        createAnimation(zoom, R.anim.zoom);

        // Set up click listener for stop button to clear any ongoing animation
        stop.setOnClickListener(v -> imageView.clearAnimation());
    }

    // Function to set up an animation for a given view and animation resource ID
    private void createAnimation(View view, int animResId) {
        view.setOnClickListener(v -> {
            // Load the animation from the specified resource ID
            Animation animation = AnimationUtils.loadAnimation(MainActivity.this, animResId);
            // Start the animation on the ImageView
            imageView.startAnimation(animation);
        });
    }
}
```
## activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <!-- Title -->
    <TextView
        android:id="@+id/title"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Animation"
        android:textSize="28sp"
        android:textStyle="bold"
        android:textColor="@color/black"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintBottom_toTopOf="@id/imageview"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent" />

    <!-- Image -->
    <ImageView
        android:id="@+id/imageview"
        android:layout_width="200dp"
        android:layout_height="200dp"
        android:contentDescription="@string/app_name"
        android:src="@drawable/android_logo"
        app:layout_constraintTop_toBottomOf="@id/title"
        app:layout_constraintBottom_toTopOf="@id/blink"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent" />

    <!-- Row 1: Blink | Rotate | Fade -->
    <Button
        android:id="@+id/blink"
        style="@style/TextAppearance.MaterialComponents.Button"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="16dp"
        android:layout_marginEnd="4dp"
        android:text="@string/blink"
        android:textColor="@color/white"
        app:layout_constraintTop_toBottomOf="@id/imageview"
        app:layout_constraintBottom_toTopOf="@id/move"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toStartOf="@id/rotate" />

    <Button
        android:id="@+id/rotate"
        style="@style/TextAppearance.MaterialComponents.Button"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="4dp"
        android:layout_marginEnd="4dp"
        android:text="@string/clockwise"
        android:textColor="@color/white"
        app:layout_constraintTop_toBottomOf="@id/imageview"
        app:layout_constraintBottom_toTopOf="@id/slide"
        app:layout_constraintStart_toEndOf="@id/blink"
        app:layout_constraintEnd_toStartOf="@id/fade" />

    <Button
        android:id="@+id/fade"
        style="@style/TextAppearance.MaterialComponents.Button"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="4dp"
        android:layout_marginEnd="16dp"
        android:text="@string/fade"
        android:textColor="@color/white"
        app:layout_constraintTop_toBottomOf="@id/imageview"
        app:layout_constraintBottom_toTopOf="@id/zoom"
        app:layout_constraintStart_toEndOf="@id/rotate"
        app:layout_constraintEnd_toEndOf="parent" />

    <!-- Row 2: Move | Slide | Zoom -->
    <Button
        android:id="@+id/move"
        style="@style/TextAppearance.MaterialComponents.Button"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="16dp"
        android:layout_marginEnd="4dp"
        android:text="@string/move"
        android:textColor="@color/white"
        app:layout_constraintTop_toBottomOf="@id/blink"
        app:layout_constraintBottom_toTopOf="@id/stop"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toStartOf="@id/slide" />

    <Button
        android:id="@+id/slide"
        style="@style/TextAppearance.MaterialComponents.Button"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="4dp"
        android:layout_marginEnd="4dp"
        android:text="@string/slide"
        android:textColor="@color/white"
        app:layout_constraintTop_toBottomOf="@id/rotate"
        app:layout_constraintBottom_toTopOf="@id/stop"
        app:layout_constraintStart_toEndOf="@id/move"
        app:layout_constraintEnd_toStartOf="@id/zoom" />

    <Button
        android:id="@+id/zoom"
        style="@style/TextAppearance.MaterialComponents.Button"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="4dp"
        android:layout_marginEnd="16dp"
        android:text="@string/zoom"
        android:textColor="@color/white"
        app:layout_constraintTop_toBottomOf="@id/fade"
        app:layout_constraintBottom_toTopOf="@id/stop"
        app:layout_constraintStart_toEndOf="@id/slide"
        app:layout_constraintEnd_toEndOf="parent" />

    <!-- Stop Button -->
    <Button
        android:id="@+id/stop"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="32dp"
        android:layout_marginEnd="32dp"
        android:text="@string/stop_animation"
        app:layout_constraintTop_toBottomOf="@id/move"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
## blink.xml
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
    <alpha android:fromAlpha="0.0"
        android:toAlpha="1.0"
        android:interpolator="@android:anim/accelerate_interpolator"
        android:duration="500"
        android:repeatMode="reverse"
        android:repeatCount="infinite"/>
</set>
```
## fade.xml
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:interpolator="@android:anim/accelerate_interpolator">

    <!-- duration is the time for which animation will work-->
    <alpha
        android:duration="1000"
        android:fromAlpha="0"
        android:toAlpha="1" />

    <alpha
        android:duration="1000"
        android:fromAlpha="1"
        android:startOffset="2000"
        android:toAlpha="0" />

</set>
```
## move.xml
```
<?xml version="1.0" encoding="utf-8"?>
<set
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:interpolator="@android:anim/linear_interpolator"
    android:fillAfter="true">

    <translate
        android:fromXDelta="0%p"
        android:toXDelta="75%p"
        android:duration="700" />
</set>
```
## rotate.xml
```
<?xml version="1.0" encoding="utf-8"?>
<set
    xmlns:android="http://schemas.android.com/apk/res/android">
    <rotate
        android:duration="6000"
        android:fromDegrees="0"
        android:pivotX="50%"
        android:pivotY="50%"
        android:toDegrees="360" />

    <rotate
        android:duration="6000"
        android:fromDegrees="360"
        android:pivotX="50%"
        android:pivotY="50%"
        android:startOffset="5000"
        android:toDegrees="0" />

</set>
```
## slide.xml
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:fillAfter="true" >
    <scale
        android:duration="500"
        android:fromXScale="1.0"
        android:fromYScale="1.0"
        android:interpolator="@android:anim/linear_interpolator"
        android:toXScale="1.0"
        android:toYScale="0.0" />
</set>
```
## zoom.xml
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:fillAfter="true" >

    <scale
        android:interpolator="@android:anim/linear_interpolator"
        android:duration = "1000"
        android:fromXScale = "1"
        android:fromYScale = "1"
        android:pivotX = "50%"
        android:pivotY = "50%"
        android:toXScale = "2"
        android:toYScale = "2"/>
</set>
```

## OUTPUT
<img width="1200" height="2541" alt="image" src="https://github.com/user-attachments/assets/362c3a5b-8ba7-4971-b9a6-28b362de310b" />

## RESULT
Thus, the Android application to add various animations (move, blink, fade, clockwise, zoom, slide) to an ImageView was successfully developed and executed using Android Studio.
