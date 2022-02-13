# Bottom Navigation
Bottom Navigation View is a material component that makes it easy to explore and switch between the top-level destinations in single click or tap.The bar contents can be populated by specifying a menu resource file. Each menu item title, icon and enabled state will be used for displaying bottom navigation bar items


## Interface View


<p align="center">
  <table align="center">
  <tr>
  <td><a href="https://ibb.co/h2CY2Lj"><img src="https://i.ibb.co/P1tD1Fn/Screenshot-2022-02-13-20-24-32-296-com-example-navigation.jpg" alt="Screenshot-2022-02-13-20-24-32-296-com-example-navigation" border="0"></a></td>


  
  <td><a href="https://ibb.co/1GRFwSh"><img src="https://i.ibb.co/whp5xv3/Screenshot-2022-02-13-20-24-34-670-com-example-navigation.jpg" alt="Screenshot-2022-02-13-20-24-34-670-com-example-navigation" border="0"></a><br /><a target='_blank' href='https://fr.imgbb.com/'></a></td>
 <td><a href="https://ibb.co/2khHK6g"><img src="https://i.ibb.co/P6j0CYw/Screenshot-2022-02-13-20-24-37-063-com-example-navigation.jpg" alt="Screenshot-2022-02-13-20-24-37-063-com-example-navigation" border="0"></a><br /><a target='_blank' href='https://fr.imgbb.com/'></a></td>
 </tr>
  </table>

  

  
</p>



## Java Code

``` java

package com.example.navigation;

import androidx.annotation.NonNull;
import androidx.appcompat.app.AppCompatActivity;
import androidx.fragment.app.FragmentContainerView;
import androidx.fragment.app.FragmentController;
import androidx.navigation.NavController;

import android.os.Bundle;
import android.view.MenuItem;
import android.view.View;

import com.google.android.material.bottomnavigation.BottomNavigationView;

public class MainActivity extends AppCompatActivity implements BottomNavigationView.OnNavigationItemSelectedListener {


    BottomNavigationView bottomNavigationView;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);


        bottomNavigationView = findViewById(R.id.bottomNavigationView);

        bottomNavigationView.setOnNavigationItemSelectedListener(this);
        bottomNavigationView.setSelectedItemId(R.id.my_nav);


    }

    FirstFragment firstFragment = new FirstFragment();
    SecondFragment secondFragment = new SecondFragment();
    ThirdFragment thirdFragment = new ThirdFragment();

    @Override
    public boolean onNavigationItemSelected(@NonNull MenuItem item) {

        switch (item.getItemId()) {
            case R.id.firstFragment:
                getSupportFragmentManager().beginTransaction().replace(R.id.flFragment, firstFragment).commit();
                return true;

            case R.id.secondFragment:
                getSupportFragmentManager().beginTransaction().replace(R.id.flFragment, secondFragment).commit();
                return true;

            case R.id.thirdFragment:
                getSupportFragmentManager().beginTransaction().replace(R.id.flFragment, thirdFragment).commit();
                return true;
        }
        return false;
    }
}

```

## XML

```xml

<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">




    <FrameLayout
        android:id="@+id/flFragment"
        android:layout_width="match_parent"
        android:layout_height="0dp"
        app:layout_constraintBottom_toTopOf="@+id/bottomNavigationView"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.5"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <com.google.android.material.bottomnavigation.BottomNavigationView
        android:id="@+id/bottomNavigationView"
        android:layout_width="match_parent"
        android:layout_height="75dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.5"
        app:layout_constraintStart_toStartOf="parent"
        app:menu="@menu/my_menu"/>

</androidx.constraintlayout.widget.ConstraintLayout>
```
