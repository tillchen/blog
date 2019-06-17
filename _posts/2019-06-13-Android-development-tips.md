---
layout: post
title: "Android development tips"
---

## Basics

1. **Layout** is typically defined in XML, whereas **activities** are in Java class.

2. Android doesn't run .class or .jar files. Instead, it uses its own optimized formats to run the apps.

3. An APK file is an Android app package, which is basically a JAR of ZIP file for Android apps.

## Layout

1. A drop-down list in Android is called a spinner.

2. We should put string values in strings.xml rather than hardcoding them, (easier for global changes and different lanugages.) `<string name="foo">bar</string>` `android:text="@string/foo"`

3. For the spinner, use `android:entries="@array/foo"`.

    ```xml
    <string-array name="foo">
        <item>bar1</item>
    </string-array>
    ```

4. Example layout: (activity_main.xml)

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <LinearLayout
        xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:tools="http://schemas.android.com/tools"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:padding="16dp"
        android:orientation="vertical"
        tools:context="com.tillchen.beeradviser.MainActivity">

        <Spinner
            android:id="@+id/color"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginTop="40dp"
            android:layout_gravity="center"
            android:layout_margin="16dp"
            android:entries="@array/beer_colors" />

        <Button
            android:id="@+id/find_beer"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_gravity="center"
            android:layout_margin="16dp"
            android:text="@string/find_beer"
            android:onClick="onClickFindBeer" />

        <TextView
            android:id="@+id/brands"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_gravity="center"
            android:layout_margin="16dp"
            android:text="@string/brands" />
    </LinearLayout>
    ```

5. Example string.xml:

    ```xml
    <resources>
        <string name="app_name">Beer Advisor</string>
        <string name="find_beer">Find Beer!</string>
        <string name="brands">No beers selected</string>
        <string-array name="beer_colors">
            <item>light</item>
            <item>amber</item>
            <item>brown</item>
            <item>dark</item>
        </string-array>
    </resources>
    ```

## Activities

1. All activities have to extend the Activity class or its subclass.

2. `setContentView(R.layout.activity_main)` tells Android the activity uses the activity_main layout.

3. R is a special Java class that enables you to retrieve references to resources. `TextView foo = findViewById(R.id.foo)`

4. Once we have the view, we can access its methods.

5. Example activity: (MainActivity.java)

    ```java
    package com.tillchen.beeradviser;

    import android.app.Activity;
    import android.os.Bundle;
    import android.view.View;
    import android.widget.Spinner;
    import android.widget.TextView;

    public class MainActivity extends Activity {

        @Override
        protected void onCreate (Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
            setContentView(R.layout.activity_main);
        }

        //Called when the user clicks the button.
        public void onClickFindBeer(View view) {
            //Get a reference to the TextView
            TextView brands = findViewById(R.id.brands);
            //Get a reference to the Spinner
            Spinner color = findViewById(R.id.color);
            //Get the selected item in the Spinner
            String beerType = String.valueOf    (color.getSelectedItem());
            //Display the selected item
            brands.setText(beerType);
        }
    }
    ```

## Resources

[Head First Android Development: A Brain-Friendly Guide 2nd Edition](https://www.amazon.com/Head-First-Android-Development-Brain-Friendly/dp/1491974052/ref=sr_1_1?keywords=head+first+android&qid=1560338899&s=gateway&sr=8-1)