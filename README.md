# Tugas Pertemuan 9

Nama            : Nadya Khairunnisa

NIM             : 312210133

Kelas           : TI.22.A.1

Mata Kuliah     : Pemrograman Mobile 1

Dosen Pengampu  : Donny Maulana, S.Kom., M.M.S.I

# Perintah Tugas

![tugas 9](https://github.com/nadyakhorun/Intent-App/assets/115801823/e2501efe-6f2e-4817-b417-1d74941b802f)

# 1. Launcher Splash Logo

Pertama kita membuat Launcher Splash Logo terlebih dahulu, atau menampilkan logo saat pertama kali membuka aplikasi. Berikut langkah-langkahnya:

- Membuat sebuah Drawable Resource File baru, untuk background logo launcher kita nanti. Buat file baru pada directory res/drawable.

- Jika berhasil dibuat, kita tambahkan terlebih dahulu logo yang kita miliki ke dalam project kita, dengan cara hanya mengcopy logonya kemudian dipaste difolder drawable.

- Lalu buka backgroundlauncher.xml yang sudah dibuat sebelumnya dan masukkan code ini

      <?xml version="1.0" encoding="utf-8"?>
      <layer-list xmlns:android="http://schemas.android.com/apk/res/android">
          <item android:drawable="@color/grey"/>
          <item>
              <bitmap
                  android:src="@drawable/logo"
                  android:gravity="center" />
          </item>
      </layer-list>

*warna dapat disesuaikan dengan keinginan, lalu masukkan logo yang sudah ditambahkan tadi.

- Lalu, buka themes.xml yang letaknya ada di res/values/themes, kemudian tambahkan code ini didalam resourcesnya:

        <style name="SplashScreen" parent="Theme.MaterialComponents.DayNight.NoActionBar">
              <item name="android:windowBackground">@drawable/backgroundlauncher</item>
              <item name="android:statusBarColor">?attr/colorOnPrimary</item>
        </style>  

- Kemudian kita buat java classnya agar splashscreen bisa berjalan, lalu didalam SplashScreen.java kita masukkan codenya seperti berikut

        package com.example.tugassembilan;
        
        import android.content.Intent;
        import android.os.Bundle;
        import android.os.Handler;
        
        import androidx.appcompat.app.AppCompatActivity;
        
        public class SplashScreen extends AppCompatActivity {
            @Override
            protected void onCreate(Bundle savedInstanceState) {
                super.onCreate(savedInstanceState);
        
                new Handler().postDelayed(new Runnable() {
                    @Override
                    public void run() {
                        startActivity(new Intent(SplashScreen.this, MainActivity.class));
                        finish();
                    }
                }, 2500);
            }
        }

*code ini berguna untuk menampilkan splashscreen, ketika splashscreen selesai dalam 2.5 detik nanti akan langsung pindah ke MainActivity.java

- Kemudian, buka AndroidManifest.xml lalu tambahkan code berikut didalam application

          <activity
            android:name=".SplashScreen"
            android:exported="true"
            android:theme="@style/SplashScreen">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
          </activity>

Dengan ini perintah membuat Launcher Splash Logo sudah selesai, kemudian kita akan lanjut ketahap berikutnya yaitu membuat menu untuk menampilkan semua project yang sudah dibuat pada pertemuan sebelumnya.

# 2. Menu Utama

Kedua disini kita akan membuat menu utamanya yang akan berjalan setelah SplashScreen Logo sebelumnya. Berikut langkah-langkahnya :

- Jika diawal pembuatan project kita memilih template empty views activity, maka pada layout otomatis terbuat file activity_main.xml dan pada java akan terbuat MainActivity.java. Kemudian langsung saja kita buka activity_main.xml lalu masukkan code seperti berikut :

        <?xml version="1.0" encoding="utf-8"?>
        <RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
            xmlns:tools="http://schemas.android.com/tools"
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            tools:context=".MainActivity">
        
            <ImageView
                android:id="@+id/background"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:adjustViewBounds="true"
                android:scaleType="centerCrop"
                android:src="@drawable/background" />
        
            <Button
                android:id="@+id/btnHelloWorld"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:onClick="btnHelloWorld"
                android:layout_centerHorizontal="true"
                android:layout_marginTop="200dp"
                android:text="@string/project_hello"
                tools:ignore="UsingOnClickInXml" />
        
            <Button
                android:id="@+id/btnProjectCount"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:onClick="btnCount"
                android:layout_below="@+id/btnHelloWorld"
                android:layout_centerHorizontal="true"
                android:layout_marginTop="20dp"
                android:text="@string/project_count"
                tools:ignore="UsingOnClickInXml" />
        
            <Button
                android:id="@+id/btnProjectSianida"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:onClick="btnSianida"
                android:layout_below="@+id/btnProjectCount"
                android:layout_centerHorizontal="true"
                android:layout_marginTop="20dp"
                android:text="@string/project_sianida"
                tools:ignore="UsingOnClickInXml" />
        
            <Button
                android:id="@+id/btnTwoActivity"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:onClick="btnTwoActivity"
                android:layout_below="@+id/btnProjectSianida"
                android:layout_centerHorizontal="true"
                android:layout_marginTop="20dp"
                android:text="@string/project_twoactivity"
                tools:ignore="UsingOnClickInXml" />
        
            <Button
                android:id="@+id/btnSetAlarm"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:onClick="btnSetAlarm"
                android:layout_below="@+id/btnTwoActivity"
                android:layout_centerHorizontal="true"
                android:layout_marginTop="20dp"
                android:text="@string/project_set_alarm"
                tools:ignore="UsingOnClickInXml" />
        
        </RelativeLayout>

*background disini sesuai dengan keinginan, kemudian tambahkan gambar kedalam folder drawable seperti memasukkan logo pada cara sebelumnya.

# Tampilan Design

![tampilan desain](https://github.com/nadyakhorun/Intent-App/assets/115801823/c86a2350-492c-4859-a1ef-ce01313ad4be)

- Selanjutnya kita buka MainActivity.java untuk menambahkan code intent untuk masing-masing tombol.

        package com.example.tugassembilan;
        
        import androidx.appcompat.app.AppCompatActivity;
        
        import android.content.Intent;
        import android.os.Bundle;
        import android.view.View;
        
        public class MainActivity extends AppCompatActivity {
        
            @Override
            protected void onCreate(Bundle savedInstanceState) {
                super.onCreate(savedInstanceState);
                setContentView(R.layout.activity_main);
        
                findViewById(R.id.btnSetAlarm).setOnClickListener(new View.OnClickListener() {
                    @Override
                    public void onClick(View v) {
                        // Panggil metode untuk mengatur alarm
                        setAlarm();
                    }
                });
            }
            private void setAlarm() {
                Intent alarm = new Intent(android.provider.AlarmClock.ACTION_SET_ALARM);
                startActivity(alarm);
            }
        
            public void btnHelloWorld(View view) {
                Intent helloworld = new Intent(MainActivity.this, HelloActivity.class);
                startActivity(helloworld);
            }
        
            public void btnCount(View view) {
                Intent count = new Intent(MainActivity.this, CountActivity.class);
                startActivity(count);
            }
        
            public void btnSianida(View view) {
                Intent sianida = new Intent(MainActivity.this, SianidaActivity.class);
                startActivity(sianida);
            }
        
            public void btnTwoActivity(View view) {
                Intent twoact = new Intent(MainActivity.this, TwoactActivity.class);
                startActivity(twoact);
            }
        }

*Semua button dari a-d menggunakan explicit intent dan button e. Project Set Alarm menggunakan implicit intent.

Dengan ini menu halaman utama dengan tombol-tombol sudah berhasil dibuat. Kemudian kita hanya tinggal menambahkan beberapa coding ke dalam AndroidManifest.xml agar aplikasi dapat berjalan.

# 3. AndroidManifest.xml

Didalam AndroidManifest.xml ini kita akan menambahkan semua .java dari semua project yang dibuat sebelumnya. Berikut nama .java dari berbagai project yang telah dibuat.

a. Project Hello World = HelloActivity.java

b. Project Count = CountActivity.java

c. Project Sianida = SianidaActivity.java

d. Project TwoActivity = TwoactActivity.java dan Twoact2Activity.java

e. Project Set Alarm = MainActivity.java (karena implicit intent jadi code untuk set alarm dibuat langsung disini)

          <?xml version="1.0" encoding="utf-8"?>
          <manifest xmlns:android="http://schemas.android.com/apk/res/android"
              xmlns:tools="http://schemas.android.com/tools">
          
              <uses-permission
                  android:name="com.android.alarm.permission.SET_ALARM" />
              <application
                  android:allowBackup="true"
                  android:dataExtractionRules="@xml/data_extraction_rules"
                  android:fullBackupContent="@xml/backup_rules"
                  android:icon="@mipmap/ic_launcher"
                  android:label="@string/app_name"
                  android:roundIcon="@mipmap/ic_launcher_round"
                  android:supportsRtl="true"
                  android:theme="@style/Theme.TugasSembilan"
                  tools:targetApi="31">
          
                  <activity
                      android:name=".MainActivity"
                      android:exported="true">
                      <intent-filter>
                          <action android:name="android.intent.action.SET_ALARM" />
                          <category android:name="android.intent.category.DEFAULT" />
                      </intent-filter>
                  </activity>
          
                  <activity
                      android:name=".HelloActivity"
                      android:exported="true" />
          
                  <activity
                      android:name=".TwoactActivity"
                      android:exported="true" />
          
                  <activity
                      android:name=".Twoact2Activity"
                      android:exported="true" />
          
                  <activity
                      android:name=".CountActivity"
                      android:exported="true" />
          
                  <activity
                      android:name=".SianidaActivity"
                      android:exported="true" />
          
                  <activity
                      android:name=".SplashScreen"
                      android:exported="true"
                      android:theme="@style/SplashScreen">
                      <intent-filter>
                          <action android:name="android.intent.action.MAIN" />
                          <category android:name="android.intent.category.LAUNCHER" />
                      </intent-filter>
                  </activity>
              </application>
          
          </manifest>

# Code Dari Semua Project

# Strings, Colors, dan Dimens

1. Strings

   Berisi semua string dari project

          <resources>
            <string name="app_name">Tugas Sembilan</string>
          
            <string name="project_hello">Project Hello World</string>
            <string name="project_count">Project Count</string>
            <string name="project_sianida">Project Sianida</string>
            <string name="project_twoactivity">Project TwoActivity</string>
            <string name="project_set_alarm">Project Set Alarm</string>
          
            <string name="hello_text">>_Hello World!</string>
          
            <string name="button_label_toast">Desk</string>
            <string name="button_label_count">Count</string>
            <string name="count_initial_value">0</string>
            <string name="toast_message">Project Count</string>
          
            <string name="button_main">Send</string>
            <string name="text_header_reply">Message Received</string>
            <string name="editText_main">Enter Your Message Here</string>
            <string name="text_header">Reply Received</string>
            <string name="button_second">Reply</string>
            <string name="editText_second">Enter Your Reply Here</string>
          
            <string name="article_title">Kasus Sianida</string>
            <string name="article_subtitle">ICE COLD!</string>
          
            <string name="article_teks">Kasus kopi sianida berawal dari pertemuan Jessica Wongso, Mirna, dan Hanie Boon Juwita di Kafe Olivier Grand Indonesia (GI) pada 6 Januari 2016. Jessica datang lebih dahulu dan memesan tempat dilayani resepsionis Cindy yang menawarkan meja nomor 54.</string>
          </resources>

2. Colors

   Berisi semua colors dari project

          <?xml version="1.0" encoding="utf-8"?>
          <resources>
            <color name="black">#FF000000</color>
            <color name="white">#FFFFFFFF</color>
            <color name="grey">#323232</color>
            <color name="blue">#0004FF</color>
            <color name="green">#08BD02</color>
            <color name="colorPrimary">#3F51B5</color>
            <color name="colorPrimaryDark">#303F9F</color>
            <color name="colorAccent">#FF4081</color>
          </resources>

3. Dimens

   Berisi code dimens untuk project sianida

          <?xml version="1.0" encoding="utf-8"?>
          <resources>
            <dimen name="padding_regular">10dp</dimen>
            <dimen name="line_spacing">5sp</dimen>
          </resources>

# A. Project Hello World

- activity_hello.xml

            <?xml version="1.0" encoding="utf-8"?>
            <androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
              xmlns:app="http://schemas.android.com/apk/res-auto"
              xmlns:tools="http://schemas.android.com/tools"
              android:layout_width="match_parent"
              android:layout_height="match_parent"
              tools:context=".HelloActivity">
            
              <ImageView
                  android:id="@+id/background"
                  android:layout_width="match_parent"
                  android:layout_height="match_parent"
                  android:background="@drawable/bg_hello"
                  android:adjustViewBounds="true"
                  android:scaleType="centerCrop"/>
            
              <TextView
                  android:id="@+id/Texthello"
                  android:layout_width="wrap_content"
                  android:layout_height="wrap_content"
                  android:fontFamily="courier"
                  android:gravity="center"
                  android:text="@string/hello_text"
                  android:textColor="@color/green"
                  android:textSize="11pt"
                  android:textStyle="bold"
                  app:layout_constraintBottom_toBottomOf="parent"
                  app:layout_constraintEnd_toEndOf="parent"
                  app:layout_constraintStart_toStartOf="parent"
                  app:layout_constraintTop_toTopOf="parent"
                  tools:ignore="TextSizeCheck" />
            
            </androidx.constraintlayout.widget.ConstraintLayout>


- HelloActivity.java

              package com.example.tugassembilan;
              
              import android.os.Bundle;
              import androidx.appcompat.app.AppCompatActivity;
              
              public class HelloActivity extends AppCompatActivity {
              
              @Override
              protected void onCreate(Bundle savedInstanceState) {
                  super.onCreate(savedInstanceState);
                  setContentView(R.layout.activity_hello);
                  }
              }

# B. Project Count

- activity_count.xml

            <?xml version="1.0" encoding="utf-8"?>
            <androidx.constraintlayout.widget.ConstraintLayout
              xmlns:android="http://schemas.android.com/apk/res/android"
              xmlns:app="http://schemas.android.com/apk/res-auto"
              xmlns:tools="http://schemas.android.com/tools"
              android:layout_width="match_parent"
              android:layout_height="match_parent"
              tools:context=".CountActivity">
            
              <ImageView
                  android:id="@+id/background"
                  android:layout_width="match_parent"
                  android:layout_height="match_parent"
                  android:background="@drawable/bg_count"
                  android:adjustViewBounds="true"
                  android:scaleType="centerCrop" />
            
              <Button
                  android:id="@+id/button_toast"
                  android:layout_width="0dp"
                  android:layout_height="wrap_content"
                  android:layout_marginEnd="8dp"
                  android:layout_marginStart="8dp"
                  android:layout_marginTop="8dp"
                  android:background="@color/colorPrimary"
                  android:onClick="showToast"
                  android:text="@string/button_label_toast"
                  android:textColor="@android:color/white"
                  app:layout_constraintEnd_toEndOf="parent"
                  app:layout_constraintStart_toStartOf="parent"
                  app:layout_constraintTop_toTopOf="parent"
                  tools:ignore="UsingOnClickInXml"/>
            
              <Button
                  android:id="@+id/button_count"
                  android:layout_width="0dp"
                  android:layout_height="wrap_content"
                  android:layout_marginEnd="8dp"
                  android:layout_marginStart="8dp"
                  android:layout_marginBottom="8dp"
                  android:background="@color/colorPrimary"
                  android:onClick="countUp"
                  android:text="@string/button_label_count"
                  android:textColor="@android:color/white"
                  app:layout_constraintEnd_toEndOf="parent"
                  app:layout_constraintStart_toStartOf="parent"
                  app:layout_constraintBottom_toBottomOf="parent"
                  tools:ignore="UsingOnClickInXml" />
            
              <TextView
                  android:id="@+id/show_count"
                  android:layout_width="0dp"
                  android:layout_height="wrap_content"
                  android:layout_marginStart="8dp"
                  android:layout_marginEnd="8dp"
                  android:text="@string/count_initial_value"
                  android:textAlignment="center"
                  android:textColor="@color/colorPrimary"
                  android:textSize="160sp"
                  android:textStyle="bold"
                  app:layout_constraintBottom_toTopOf="@+id/button_count"
                  app:layout_constraintEnd_toEndOf="parent"
                  app:layout_constraintStart_toStartOf="parent"
                  app:layout_constraintTop_toBottomOf="@+id/button_toast"
                  tools:ignore="RtlCompat" />
            
            </androidx.constraintlayout.widget.ConstraintLayout>

- CountActivity.java

              package com.example.tugassembilan;
              
              import android.annotation.SuppressLint;
              import android.os.Bundle;
              import android.view.View;
              import android.widget.TextView;
              import android.widget.Toast;
              
              import androidx.appcompat.app.AppCompatActivity;
              
              public class CountActivity extends AppCompatActivity {
              private int nCount = 0;
              
              private TextView nShowCount;
              
              @SuppressLint("MissingInflatedId")
              @Override
              protected void onCreate(Bundle savedInstanceState) {
                  super.onCreate(savedInstanceState);
                  setContentView(R.layout.activity_count);
                  nShowCount = findViewById(R.id.show_count);
                  }
              
                  public void showToast(View view){
                  Toast toast = Toast.makeText(this, "Menghitung Bilangan",
                      Toast.LENGTH_SHORT);
                      toast.show();
                  }
              
                  @SuppressLint("SetTextI18n")
                  public void countUp(View view){
                      nCount++;
                  if (nShowCount != null)
                      nShowCount.setText(Integer.toString(nCount));
                  }
              }

  # C. Project Sianida

  - activity_sianida.xml
 
          <?xml version="1.0" encoding="utf-8"?>
          <RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
              android:layout_width="match_parent"
              android:layout_height="match_parent"
              xmlns:tools="http://schemas.android.com/tools"
              tools:context=".SianidaActivity">
          
              <TextView
                  android:id="@+id/article_heading"
                  android:layout_width="match_parent"
                  android:layout_height="wrap_content"
                  android:background="@color/colorPrimary"
                  android:padding="@dimen/padding_regular"
                  android:text="@string/article_title"
                  android:textAppearance="@android:style/TextAppearance.DeviceDefault.Large"
                  android:textColor="@android:color/white"
                  android:textStyle="bold" />
          
                <ScrollView
                  android:layout_width="wrap_content"
                  android:layout_height="wrap_content"
                  android:layout_below="@id/article_heading">
          
                  <LinearLayout
                      android:layout_width="match_parent"
                      android:layout_height="wrap_content"
                      android:orientation="vertical">
          
                      <TextView
                          android:id="@+id/article_subheading"
                          android:layout_width="match_parent"
                          android:layout_height="wrap_content"
                          android:padding="@dimen/padding_regular"
                          android:text="@string/article_subtitle"
                          android:textAlignment="center"
                          android:textAppearance="@android:style/TextAppearance.DeviceDefault"
                          android:textColor="#8D6E63" />
          
                      <TextView
                          android:id="@+id/article"
                          android:layout_width="wrap_content"
                          android:layout_height="wrap_content"
                          android:autoLink="web"
                          android:lineSpacingExtra="@dimen/line_spacing"
                          android:padding="@dimen/padding_regular"
                          android:text="@string/article_teks"
                          tools:ignore="VisualLintLongText" />
                  </LinearLayout>
              </ScrollView>
          </RelativeLayout>

- SianidaActivity.java

            package com.example.tugassembilan;
            
            import android.os.Bundle;
            
            import androidx.appcompat.app.AppCompatActivity;
            
            public class SianidaActivity extends AppCompatActivity {
                @Override
                protected void onCreate(Bundle savedInstanceState){
                    super.onCreate(savedInstanceState);
                    setContentView(R.layout.activity_sianida);
                }
            }

# D. Project TwoActivity

- activity_twoact.xml

          <?xml version="1.0" encoding="utf-8"?>
          <androidx.constraintlayout.widget.ConstraintLayout
              xmlns:android="http://schemas.android.com/apk/res/android"
              android:layout_width="match_parent"
              android:layout_height="match_parent"
              xmlns:tools="http://schemas.android.com/tools"
              xmlns:app="http://schemas.android.com/apk/res-auto"
              tools:context=".TwoactActivity">
          
              <ImageView
                  android:id="@+id/background"
                  android:layout_width="match_parent"
                  android:layout_height="match_parent"
                  android:adjustViewBounds="true"
                  android:scaleType="centerCrop"
                  android:src="@drawable/bg_twoact" />
          
              <TextView
                  android:id="@+id/text_header_reply"
                  android:layout_width="wrap_content"
                  android:layout_height="wrap_content"
                  android:layout_marginStart="8dp"
                  android:layout_marginLeft="8dp"
                  android:layout_marginTop="16dp"
                  android:text="@string/text_header_reply"
                  android:textAppearance="@style/TextAppearance.AppCompat.Medium"
                  android:textStyle="bold"
                  android:visibility="invisible"
                  app:layout_constraintStart_toStartOf="parent"
                  app:layout_constraintTop_toTopOf="parent"/>
          
              <TextView
                  android:id="@+id/text_message_reply"
                  android:layout_width="wrap_content"
                  android:layout_height="wrap_content"
                  android:layout_marginStart="8dp"
                  android:layout_marginLeft="8dp"
                  android:layout_marginTop="8dp"
                  android:visibility="invisible"
                  app:layout_constraintStart_toStartOf="parent"
                  app:layout_constraintTop_toBottomOf="@+id/text_header_reply" />
          
              <Button
                  android:id="@+id/button_main"
                  android:layout_width="wrap_content"
                  android:layout_height="wrap_content"
                  android:layout_marginBottom="16dp"
                  android:layout_marginRight="16dp"
                  android:text="@string/button_main"
                  android:onClick="LaunchSecondActivity"
                  app:layout_constraintBottom_toBottomOf="parent"
                  app:layout_constraintRight_toRightOf="parent"
                  tools:ignore="UsingOnClickInXml"/>
          
              <EditText
                  android:id="@+id/editText_main"
                  android:layout_width="0dp"
                  android:layout_height="wrap_content"
                  android:layout_marginStart="8dp"
                  android:layout_marginEnd="8dp"
                  android:layout_marginBottom="16dp"
                  android:ems="10"
                  android:hint="@string/editText_main"
                  android:inputType="textLongMessage"
                  android:minHeight="48dp"
                  app:layout_constraintBottom_toBottomOf="parent"
                  app:layout_constraintEnd_toStartOf="@+id/button_main"
                  app:layout_constraintStart_toStartOf="parent" />
          </androidx.constraintlayout.widget.ConstraintLayout>

- activity_twoact2.xml

          <?xml version="1.0" encoding="utf-8"?>
          <androidx.constraintlayout.widget.ConstraintLayout
              xmlns:android="http://schemas.android.com/apk/res/android"
              android:layout_width="match_parent"
              android:layout_height="match_parent"
              xmlns:tools="http://schemas.android.com/tools"
              xmlns:app="http://schemas.android.com/apk/res-auto"
              tools:context=".Twoact2Activity">
          
              <ImageView
                  android:id="@+id/background"
                  android:layout_width="match_parent"
                  android:layout_height="match_parent"
                  android:adjustViewBounds="true"
                  android:scaleType="centerCrop"
                  android:src="@drawable/bg_twoact" />
          
              <TextView
                  android:id="@+id/text_header"
                  android:layout_width="wrap_content"
                  android:layout_height="wrap_content"
                  android:layout_marginStart="8dp"
                  android:layout_marginLeft="8dp"
                  android:layout_marginTop="16dp"
                  android:text="@string/text_header"
                  android:textAppearance="@style/TextAppearance.AppCompat.Medium"
                  android:textStyle="bold"
                  app:layout_constraintStart_toStartOf="parent"
                  app:layout_constraintTop_toTopOf="parent" />
          
              <TextView
                  android:id="@+id/text_message"
                  android:layout_width="wrap_content"
                  android:layout_height="wrap_content"
                  android:layout_marginStart="8dp"
                  android:layout_marginLeft="8dp"
                  android:layout_marginTop="8dp"
                  app:layout_constraintStart_toStartOf="parent"
                  app:layout_constraintTop_toBottomOf="@+id/text_header" />
          
              <Button
                  android:id="@+id/button_second"
                  android:layout_width="wrap_content"
                  android:layout_height="wrap_content"
                  android:layout_marginBottom="16dp"
                  android:layout_marginRight="16dp"
                  android:text="@string/button_second"
                  android:onClick="returnReply"
                  app:layout_constraintBottom_toBottomOf="parent"
                  app:layout_constraintRight_toRightOf="parent"
                  tools:ignore="UsingOnClickInXml" />
          
              <EditText
                  android:id="@+id/editText_second"
                  android:layout_width="0dp"
                  android:layout_height="wrap_content"
                  android:layout_marginStart="8dp"
                  android:layout_marginEnd="8dp"
                  android:layout_marginBottom="16dp"
                  android:ems="10"
                  android:hint="@string/editText_second"
                  android:inputType="textLongMessage"
                  android:minHeight="48dp"
                  app:layout_constraintBottom_toBottomOf="parent"
                  app:layout_constraintEnd_toStartOf="@+id/button_second"
                  app:layout_constraintStart_toStartOf="parent" />
          </androidx.constraintlayout.widget.ConstraintLayout>

- TwoactActivity.java

              package com.example.tugassembilan;
              
              import androidx.appcompat.app.AppCompatActivity;
              
              import android.content.Intent;
              import android.os.Bundle;
              import android.util.Log;
              import android.view.View;
              import android.widget.EditText;
              import android.widget.TextView;
              
              public class TwoactActivity extends AppCompatActivity {
              
                  private static final String LOG_TAG = TwoactActivity.class.getSimpleName();
              
                  public static final String EXTRA_MESSAGE = "com.example.android.Twoact2Activity.extra.MESSAGE";
              
                  public static final int TEXT_REQUEST = 1;
              
                  private EditText mMessageEditText;
              
                  private TextView mReplyHeadTextView;
              
                  private TextView mReplyTextView;
              
                  @Override
                  protected void onCreate(Bundle savedInstanceState) {
                      super.onCreate(savedInstanceState);
                      setContentView(R.layout.activity_twoact);
              
                      mMessageEditText = findViewById(R.id.editText_main);
                      mReplyHeadTextView = findViewById(R.id.text_header_reply);
                      mReplyTextView = findViewById(R.id.text_message_reply);
                  }
              
                  public void LaunchSecondActivity(View view) {
                      Log.d(LOG_TAG, "Button clicked!");
                      Intent intent = new Intent(this, Twoact2Activity.class);
                      String message = mMessageEditText.getText().toString();
                      intent.putExtra(EXTRA_MESSAGE, message);
                      startActivityForResult(intent, TEXT_REQUEST);
                  }
              
                  @Override
                  public void onActivityResult(int requestCode, int resultCode, Intent data) {
                      super.onActivityResult(requestCode, resultCode, data);
              
                      if (resultCode == TEXT_REQUEST) {
                          if (resultCode == RESULT_OK) {
                          String reply = data.getStringExtra(Twoact2Activity.EXTRA_REPLY);
              
                          mReplyHeadTextView.setVisibility(View.VISIBLE);
              
                          mReplyHeadTextView.setText(reply);
                          mReplyHeadTextView.setVisibility(View.VISIBLE);
                          }
                      }
                  }
              }

- Twoact2Activity.java

              package com.example.tugassembilan;
              
              import android.content.Intent;
              import android.os.Bundle;
              import android.view.View;
              import android.widget.EditText;
              import android.widget.TextView;
              
              import androidx.appcompat.app.AppCompatActivity;
              
              public class Twoact2Activity extends AppCompatActivity {
              
                  public static final String EXTRA_REPLY ="com.example.android.Twoact2Activity.extra.REPLY";
              
                  private EditText mReply;
              
                  @Override
                  protected void onCreate(Bundle savedInstanceState){
                      super.onCreate(savedInstanceState);
                      setContentView(R.layout.activity_twoact2);
              
                      mReply = findViewById(R.id.editText_second);
              
                      Intent intent = getIntent();
                      String message = intent.getStringExtra(TwoactActivity.EXTRA_MESSAGE);
              
                      TextView textView = findViewById(R.id.text_message);
                      textView.setText(message);
                  }
                  public void returnReply(View view){
                      String reply = mReply.getText().toString();
                      Intent replyIntent = new Intent();
                      setResult(RESULT_OK, replyIntent);
                      finish();
                  }
              }

# E. Project Set Alarm

- Kita buat terlebih dahulu buttonnya didalam sebuah activity.xml, disini kita buatnya di activity_main.xml bersama dengan tombol lainnya.

          <Button
              android:id="@+id/btnSetAlarm"
              android:layout_width="wrap_content"
              android:layout_height="wrap_content"
              android:onClick="btnSetAlarm"
              android:layout_below="@+id/btnTwoActivity"
              android:layout_centerHorizontal="true"
              android:layout_marginTop="20dp"
              android:text="@string/project_set_alarm"
              tools:ignore="UsingOnClickInXml" />

- Kemudian kita tambahkan code implicit intent pada .java nya.

                    findViewById(R.id.btnSetAlarm).setOnClickListener(new View.OnClickListener() {
                  @Override
                  public void onClick(View v) {
                      // Panggil metode untuk mengatur alarm
                      setAlarm();
                  }
              });
          }
          private void setAlarm() {
          Intent alarm = new Intent(android.provider.AlarmClock.ACTION_SET_ALARM);
          startActivity(alarm);
      }

- Selanjutnya kita buka AndroidManifest.xml, lalu tambahkan code untuk izin membuka Alarm

          <uses-permission android:name="com.android.alarm.permission.SET_ALARM" />

  Kemudian tambahkan code berikut didalam application agar set alarm dapat berjalan

            <activity
              android:name=".MainActivity"
              android:exported="true">
              <intent-filter>
                  <action android:name="android.intent.action.SET_ALARM" />
                  <category android:name="android.intent.category.DEFAULT" />
              </intent-filter>
          </activity>

# Hasil RUN

Berikut ini adalah video hasil RUN dari aplikasi yang sudah dibuat.

https://github.com/nadyakhorun/Intent-App/assets/115801823/1ea6253f-21a1-49a8-a158-68873134218c

# SELESAI, TERIMA KASIH

# NOTE

Semua project diatas terdapat code untuk background, kalian dapat menggunakannya atau tidak. Jika kalian ingin menggunakannya jangan lupa untuk menambahkan gambar background di folder drawable.
