---
layout: post
title: "Android development tips"
---

## Basics

1. **Layout** is typically defined in XML, whereas **activities** are in Java class.

2. Android doesn't run .class or .jar files. Instead, it uses its own optimized formats to run the apps.

3. An APK file is an Android app package, which is basically a JAR of ZIP file for Android apps.

## Layout

1. Example layout: (activity_main.xml)

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

2. Example string.xml:

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

3. String array: `android:entries="@array/foo"`.

    ```xml
    <string-array name="foo">
        <item>bar1</item>
    </string-array>
    ```

4. `<EditText>` is an editable text field:
    * `android:hint="@string/hint"`: normally "Enter a message", telling the user what to type;
    * `android:ems="10"`: 10-M space.

5. `android:layout_weight="number"` makes a view stretch.
    * If a has the weight of 1 and b has 2, a'll have 1/3 and b'll have 2/3 of the screen.
    * We usually have `android:layout_height="0dp"` (for vertical layout)above layout_weight.

6. `android:gravity="top"` moves the CONTENT of a view to the top of the view, whereas `android:layout_gravity="end"` moves the placement of the VIEW itself to the end.

7. `<FrameLayout></FrameLayout>` allows views to overlap. Ues it when we need to replace the fragments and add the changes to the back stack.

8. Surround LinearLayout/FrameLayout with `<ScrollView></ScrollView>` to get a vertical scrollbar. (`HorizontalScrollView` for the horizontal scrollbar.)

9. The layout-large folder is for the large devices.

10. A CoordinatorLayout allows the behavior of one view to affect the behavior of another.

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
            String beerType = String.valueOf(color.getSelectedItem());
            //Display the selected item
            brands.setText(beerType);
        }
    }
    ```

6. Use Intent to call another activity (can be from other apps):
    * Explicit intent:

        ```java
        public void onSendMessage(View view) {
            Intent intent = new Intent(this, FooActivity.class); // explicit intent
            intent.putExtra("message", value); // message is the name of the extra
            startActivity(intent);
        }
        ```

        ```java
        ...
        Intent intent = getIntent();
        String string = intent.getStringExtra("message");
        ```

    * Implicit intent: (with actions to allow users to choose which app to run)

        ```java
        Intent intent = new Intent(Intent.ACTION_SEND); // ACTION_DIAL/ACTION_WEB_SEARCH
        intent.setType("text/plain");
        intent.putExtra(Intent.EXTRA_TEXT, messageText);
        String chooserTitle = getString(R.string.chooser);
        // Ensure that the user always get the chance to choose an activity
        Intent chosenIntent = Intent.createChooser(intent, chooserTitle);
        startActivity(chosenIntent);
        ```

7. Save the instance state:

    ```java
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        if (savedInstanceState != null) {
            seconds = savedInstanceState.getInt("seconds");
            running = savedInstanceState.getBoolean("running");
        }
        runTimer();
    }

    @Override
    public void onSaveInstanceState(Bundle savedInstanceState) {
        super.onSaveInstanceState(savedInstanceState);
        savedInstanceState.putInt("seconds", seconds);
        savedInstanceState.putBoolean("running", running);
    }
    ```

8. Activity lifecycles:
    * When we implement them (`onCreate()`, `onStart()`, `onResume()`, `onPause()`, `onStop()`, `onRestart()`, `onDestroy()`), we must call the super class methods.
    * `onResume()` is called when the activity is started OR resumed; `onPause()` is called when the activity is paused OR stopped.

9. Fragment transactions:

    * Example:

        ```java
        @Override
        public void itemClicked(long id) {
            View fragmentContainer = findViewById(R.id.fragment_container);
            if (fragmentContainer != null) {
                WorkoutDetailFragment details = new WorkoutDetailFragment();
                FragmentTransaction ft = getSupportFragmentManager().beginTransaction();
                details.setWorkout(id);
                ft.replace(R.id.fragment_container, details); // framelayout, fragment
                ft.setTransition(FragmentTransaction.TRANSIT_FRAGMENT_FADE); // what kind of animation
                ft.addToBackStack(null); // optional string label
                ft.commit();
            }
            else {
                Intent intent = new Intent(this, DetailActivity.class);
                intent.putExtra(DetailActivity.EXTRA_WORKOUT_ID, (int)id);
                startActivity(intent);
            }
        }
        ```

    * `getChildFragmentManager` creates nested transactions.

## Miscellaneous

1. For nonstatic data (like storing in a java file), use an adapter to access it.

    ```java
    // Example in a list fragment
    ArrayAdapter<String> adapter = new ArrayAdapter<>(
        // this or getContext()(for fragments, not subclass of context); display in a single text view; the array
        inflater.getContext(), android.R.layout.simple_list_item_1, names
    );
    setListAdapter(adapter);
    ```

2. For a list fragment, we don't need to create a layout nor implement the event listener.

3. Android builds the back stack to keep track of the activity/fragment transactions.

4. The `onClick` attribute calls the methods in the activity, not the fragment. To make it work, change the onClick methods to private and make the fragment class implement View.OnClickListener (overriding the `public void onClick(View v)` method.) Then, attach the onClickListener to the buttons in the onCreateView method.

5. For dynamic fragments, use FrameLayout instead of Fragment and use FragmentTransaction.

## Resources

* [Head First Android Development: A Brain-Friendly Guide 2nd Edition](https://www.amazon.com/Head-First-Android-Development-Brain-Friendly/dp/1491974052/ref=sr_1_1?keywords=head+first+android&qid=1560338899&s=gateway&sr=8-1)
