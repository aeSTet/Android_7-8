# Android_7-8

MainActivity.java

    package com.example.guessthenumber;

    import androidx.appcompat.app.AppCompatActivity;

    import android.annotation.SuppressLint;
    import android.os.Bundle;
    import android.view.View;
    import android.widget.Button;
    import android.widget.EditText;
    import android.widget.TextView;

    import java.lang.Math;


    public class MainActivity extends AppCompatActivity {
        TextView tvInfo;
        EditText etInput;
        Button bControl, bExit, easyButton, hardButton;
        int number = (int) (Math.random() * 100);
        int max = 100;


        @Override
        protected void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
            setContentView(R.layout.activity_main);
            tvInfo = findViewById(R.id.text_view);
            etInput = findViewById(R.id.edit_text);
            bControl = findViewById(R.id.button);
            bExit = findViewById(R.id.exit);
            easyButton = findViewById(R.id.easy);
            hardButton = findViewById(R.id.hard);
        }

        @SuppressLint("SetTextI18n")
        public void onClick(View view) {
            String input = etInput.getText().toString();
            if (!input.matches("\\d+")) {
                tvInfo.setText(getResources().getString(R.string.error));
            } else {
                int inputNumber = Integer.parseInt(input);
                if (inputNumber > number && inputNumber <= max) {
                    tvInfo.setText(getResources().getString(R.string.ahead));
                } else {
                    if (inputNumber < number && inputNumber >= 0) {
                        tvInfo.setText(getResources().getString(R.string.behind));
                    } else {
                        if (inputNumber == number) {
                            tvInfo.setText(getResources().getString(R.string.hit));
                        } else {
                            tvInfo.setText(getResources().getString(R.string.range_error));
                        }
                    }
                }
            }
        }

        public void difficultyEasy(View view) {
            number = (int) (Math.random() * 100);
            tvInfo.setText(getResources().getString(R.string.difficulty_easy));
            etInput.setText(R.string.empty_text);
            max = 100;
        }

        public void difficultyHard(View view) {
            number = (int) (Math.random() * 10000);
            tvInfo.setText(R.string.difficulty_hard);
            etInput.setText(R.string.empty_text);
            max = 10000;
        }

        public void exit(View view) {
            System.exit(0);
        }
    }
 

activity_main.xml

    <?xml version="1.0" encoding="utf-8"?>
    <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:tools="http://schemas.android.com/tools"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:background="#ACACAC"
        android:gravity="center"
        android:orientation="vertical"
        tools:context=".MainActivity">

        <LinearLayout
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:orientation="horizontal">

            <Button
                android:id="@+id/easy"
                style="?android:attr/buttonBarButtonStyle"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_margin="20sp"
                android:onClick="difficultyEasy"
                android:text="@string/easy"
                android:textColor="#576834"
                tools:ignore="UsingOnClickInXml" />

            <Button
                android:id="@+id/hard"
                style="?android:attr/buttonBarButtonStyle"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_margin="20sp"
                android:onClick="difficultyHard"
                android:text="@string/hard"
                android:textColor="#703838"
                tools:ignore="UsingOnClickInXml" />

        </LinearLayout>

        <TextView
            android:id="@+id/text_view"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_margin="20sp"
            android:text="@string/try_to_guess"
            android:textColor="#4D4D4D" />

        <EditText
            android:id="@+id/edit_text"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:autofillHints="Input your number from 1 to 100"
            android:inputType="number"
            android:textColor="@color/white"
            tools:ignore="LabelFor" />

        <Button

            android:id="@+id/button"
            android:layout_width="150sp"
            android:layout_height="80sp"
            android:background="@drawable/edited_button"
            android:onClick="onClick"
            android:text="@string/input_value"
            android:textColor="#75A1A1"
            tools:ignore="UsingOnClickInXml" />


        <Button
            android:id="@+id/exit"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginTop="20sp"
            android:background="@drawable/edited_button"
            android:onClick="exit"
            android:text="@string/exit"
            android:textColor="#75A1A1"
            tools:ignore="UsingOnClickInXml" />


    </LinearLayout>

Результат работы программы:

![image](https://user-images.githubusercontent.com/76133815/141492401-6c4b48d4-06c8-4e1d-923a-d814a446a6fe.png)

![image](https://user-images.githubusercontent.com/76133815/141492421-21204929-5f60-48be-a265-bee2e52c93df.png)

![image](https://user-images.githubusercontent.com/76133815/141492453-ba13ae3b-d3c9-46a8-b951-61065c76b865.png)

![image](https://user-images.githubusercontent.com/76133815/141492473-cec95145-9943-403c-98ba-1469fb1a575a.png)

 
 

 
 
 
 
