#                 UTS PEMROGRAMAN MOBILE 1

Nama   : Zidna Soleda Zulfa

NIM    : 312210031

Kelas  : TI.22.B1


Buatlah Method program Java Toast Number, dengan mennghasilkan bilangan Fibonacci

Berikut link video : https://youtu.be/unDMRGU9-Pc?si=sUEZu--AoRpS8LlE

1. Source Code


    toast_activity.xml (dibuat dengan design pada android studio

      <?xml version="1.0" encoding="utf-8"?>
      <RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
        android:layout_width="match_parent"
        android:layout_height="match_parent">
            <LinearLayout
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:gravity="center"
                android:background="#eeeeee"
                android:orientation="vertical"
                android:paddingLeft="40dp"
                android:paddingRight="40dp">
    
                <TextView
                    android:id="@+id/textview2"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:layout_marginTop="10dp"
                    android:text="Increment"
                    android:textAlignment="center"
                    android:textSize="24sp"/>
    
                <TextView
                    android:id="@+id/textViewNumber"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:layout_marginTop="10dp"
                    android:text="0"
                    android:textAlignment="center"
                    android:textSize="24sp"/>
    
                <TextView
                    android:id="@+id/textView"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:layout_marginTop="10dp"
                    android:text="Fibonnaci"
                    android:textAlignment="center"
                    android:textSize="24sp"/>
    
                <TextView
                    android:id="@+id/textViewNumberFibo"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:layout_marginTop="10dp"
                    android:text="0"
                    android:textFontWeight="600"
                    android:textColor="@color/black"
                    android:textAlignment="center"
                    android:textSize="24sp"/>
            </LinearLayout>
    
            <Button
                android:id="@+id/button_toast"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_alignParentBottom="true"
                android:layout_alignParentLeft="true"
                style="@style/Widget.AppCompat.Button"
                android:text="Toast"/>
            <Button
                android:id="@+id/button_reset"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_marginStart="10dp"
                android:layout_marginTop="10dp"
                android:layout_marginEnd="10dp"
                android:layout_marginBottom="10dp"
                android:backgroundTint="@color/red"
                android:text="Reset"
                android:textAlignment="center"
                android:textColor="@color/white" />
            <Button
                android:id="@+id/button_hitung"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_alignParentBottom="true"
                android:layout_alignParentRight="true"
                android:backgroundTint="@color/teal_700"
                android:layout_marginRight="10dp"
                android:textColor="@color/white"
                android:text="Hitung"/>
    
    </RelativeLayout>

  Penjelasan: Isi relative layout dengan linear layout kemudian linear layout diisi dengan 4 textview kemudian setelahnya membuat 3tombol button

2. MainActivity.Java :

           package com.example.belajar_ti22b1;
          
          import androidx.appcompat.app.AppCompatActivity;
          
          import android.os.Bundle;
          import android.view.View;
          import android.widget.Button;
          import android.widget.TextView;
          import android.widget.Toast;
          
          public class MainActivity extends AppCompatActivity {
              private int mCount = 0;
              private int mCountFibo = 0;
              private TextView mShowCount;
              private TextView mShowCountFibo;
              private Button buttonToast;
              private Button buttonHitung;
              private Button buttonReset;
          
              @Override
              protected void onCreate(Bundle savedInstanceState) {
                  super.onCreate(savedInstanceState);
                  setContentView(R.layout.toast_activity);
                  mShowCount = (TextView) findViewById(R.id.textViewNumber);
                  mShowCountFibo = (TextView) findViewById(R.id.textViewNumberFibo);
                  buttonToast = (Button) findViewById(R.id.button_toast);
                  buttonHitung = (Button) findViewById(R.id.button_hitung);
                  buttonReset = (Button) findViewById(R.id.button_reset);
          
                  buttonHitung.setOnClickListener(new View.OnClickListener() {
                      @Override
                      public void onClick(View view) {hitungIncrement(view);}
                  });
                  buttonToast.setOnClickListener(new View.OnClickListener(){
                      @Override
                      public void onClick(View view) {showToast(view);}
                  });
                  buttonReset.setOnClickListener(new View.OnClickListener() {
                      @Override
                      public void onClick(View view) {resetCountDanFibbo(view);}
                  });
              }
          
              public void showToast(View view){
                  Toast toast = Toast.makeText(this, "Berhasil diklik", Toast.LENGTH_SHORT);
                  toast.show();
              }
          
              public void hitungIncrement(View view) {
                  mCount++;
                  int fibo = hitungFibonacci(mCount);
                  mCountFibo = fibo;
                  if (mShowCount != null && mShowCountFibo != null) {
                      mShowCount.setText(Integer.toString(mCount));
                      mShowCountFibo.setText(Integer.toString(mCountFibo));
                  }
              }
          
              public int hitungFibonacci(int n){
                  if(n <= 1){
                      return n;
                  }
                  int prev = 0;
                  int current = 1;
                  for(int i = 2; i <= n; i++){
                      int next = prev + current;
                      prev = current;
                      current = next;
                  }
                  return current;
              }
          
              public void resetCountDanFibbo(View view){
                  mCount = 0;
                  mCountFibo = 0;
                  mShowCount.setText(Integer.toString(mCount));
                  mShowCountFibo.setText(Integer.toString(mCountFibo));
              }
          }

MainActivity.java biasanya digunakan untuk menginisialisasi elemen antarmuka pengguna (UI) aplikasi Anda. Ini mengacu pada berkas XML layout, seperti activity_main.xml, untuk menemukan elemen UI seperti tombol, teks, gambar, dan lainnya, dan kemudian mengatur tampilan

3. strings.xml :

         <resources>
              <string name="app_name">BelajarTI22B1</string>
              <string name="button_label_toast">Toast</string>
              <string name="button_label_hitung">Hitung</string>
              <string name="hitung_initial_value">0</string>
              <string name="toast_pesan">Berhasil diklik</string>
         </resources>

   Fungsi utama dari string.xml adalah untuk mengelola dan menyediakan teks dan string yang digunakan dalam aplikasi Anda agar mudah dikelola dan diterjemahkan, serta untuk memisahkan tampilan dan logika aplikasi dari teks dan string tersebut

4. color.xml :
   
       <?xml version="1.0" encoding="utf-8"?>
        <resources>
            <color name="black">#FF000000</color>
            <color name="white">#FFFFFFFF</color>
            <color name="purple_200">#FFBB86FC</color>
            <color name="purple_500">#FF6200EE</color>
            <color name="purple_700">#FF3700B3</color>
            <color name="teal_200">#FF03DAC5</color>
            <color name="teal_700">#FF018786</color>
            <color name="red">#D10000</color>
        </resources>

   Fungsi utama dari colors.xml adalah untuk menyimpan definisi warna dalam aplikasi Anda dalam satu tempat yang terpusat.

                        Sekian dan Terimakasih...
