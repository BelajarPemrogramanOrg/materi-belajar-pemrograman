---
ID: 151
post_title: 'Belajar Pemrograman Socket Client &#8211; Server Menggunakan Android dan Java'
author: Muhammad Ikhsan
post_excerpt: 'Dalam materi belajar ini, kita akan membuat dua buah program sederhana untuk menerapkan komunikasi client - server menggunakan socket. Aplikasi client yg akan kita buat berupa sebuah aplikasi Android, sedangkan aplikasi server berupa program yg ditulis dalam bahasa pemrograman Java yg dijalankan di komputer. Anda dapat mendownload source code aplikasi yg akan kita buat <a href="http://belajarpemrograman.org/belajar-pemrograman-socket-client-server-menggunakan-android-dan-java/#download-source-code">pada bagian akhir dari tulisan ini</a>.'
layout: post
permalink: >
  http://belajarpemrograman.org/belajar-pemrograman-socket-client-server-menggunakan-android-dan-java/
published: true
post_date: 2017-01-29 14:48:07
---
Dalam materi belajar ini, kita akan membuat dua buah program sederhana untuk menerapkan komunikasi client - server menggunakan socket. Aplikasi client yg akan kita buat berupa sebuah aplikasi Android, sedangkan aplikasi server berupa program yg ditulis dalam bahasa pemrograman Java yg dijalankan di komputer. Anda dapat mendownload source code aplikasi yg akan kita buat [pada bagian akhir dari tulisan ini].

Detail Aplikasi {#detail-aplikasi}
---------------

Berikut merupakan detail dari aplikasi yg akan kita buat:

-   Sebuah aplikasi Android akan dibuat sebagai client. Aplikasi diberi nama **Panggil Saya**. *(Gak usah protes soal nama.. Silahkan kalo mau ganti. hehe)*
-   Sebuah aplikasi yg ditulis dengan Java akan dijalankan sebagai server dalam sebuah komputer.
-   Untuk menjalankannya, perangkat Android dan komputer harus berada dalam satu jaringan, misalnya keduanya terkoneksi pada jaringan wireless yg sama. Dapat menggunakan *tether*.
-   Aplikasi client (aplikasi Android) akan mengirimkan `{nama orang}`, dan server akan memberikan balasan berupa `Halo, {nama orang}!`.
    Contoh: client mengirimkan `Ikhsan`, kemudian server akan membalasnya dengan `Halo, Ikhsan!`.
-   Antarmuka aplikasi Android terdiri dari:
    -   Sebuah `EditText` untuk mengisikan IP server
    -   Sebuah `EditText` untuk mengisikan port yg digunakan oleh server untuk menerima request
    -   Sebuah `EditText` untuk mengisikan nama orang yg akan dikirimkan ke server
    -   Sebuah `Button` untuk mengirimkan request ke server
    -   Sebuah `TextView` untuk menampilkan respon dari server

Berikut merupakan *screenshot* yang dapat membantu menggambarkan jalannya aplikasi yg akan kita buat. Klik gambar untuk memperbesar.
[gallery type="rectangular" link="file" size="medium" ids="176,180,182"]

Mengenal Socket {#mengenal-socket}
---------------

***Wait*,** sebelum kita lanjutkan, pastikan kita sudah mengerti apa yg dimaksud dengan *socket* yg dari tadi disebut-sebut. Kalau kelihatan ribet, setidaknya dibaca saja. Semoga nanti setelah praktik membuat aplikasinya dan berhasil menjalankannya, jadi lebih ngerti. 

Mengenai pemrograman socket menggunakan bahasa pemrograman Java yang tidak dibahas secara mendetail dalam tulisan ini, Anda dapat membacanya pada tulisan lain di website ini yg berjudul [Belajar Pemrograman Socket Menggunakan Java].

### Pengertian Socket {#pengertian-socket}

-   Socket merupakan sebuah titik akhir dalam komunikasi dua arah antara dua program pada suatu jaringan.
-   Sebuah socket terdiri dari alamat IP dan port. Contoh: `172.20.10.5:8888`. `172.20.10.5` merupakan alamat IP dan `8888` merupakan port.

Dalam komunikasi antara 2 program (client dan server), masing-masing memiliki socket sebagai titik akhir dalam komunikasi. Jika client ingin meminta request kepada server, maka client akan menghubungi socket milik server. Begitu pula sebaliknya, ketika server akan memberikan balasan kepada client, maka server akan mengirimkan balasan tersebut ke socket milik client.

### Contoh Skenario Penggunaan Socket {#contoh-skenario-penggunaan-socket}

Sebagai contoh, Anda mengakses sebuah website melalui browser, misalnya [example.com]. Browser di komputer Anda merupakan sebuah aplikasi client yg meminta request ke *web server* yg meng-*host* [example.com]. Browser Anda akan meminta agar sistem operasi Anda menyiapkan socket untuk komunikasi ke server dengan *hostname* [example.com] dan port `80` (nomor port yg digunakan untuk `http`). Dalam paket jaringan yg dikirimkan oleh sistem operasi, akan disertakan beberapa informasi, termasuk alamat IP dan port komputer Anda yg digunakan untuk komunikasi socket, dan alamat IP dan nomor port tujuan (server). Selanjutnya, jika semuanya berjalan dengan baik, server akan menerima request dan dapat memberikan respon yg sesuai kepada client. 

Dari contoh yg disebutkan di atas, client harus sudah mengetahui socket (alamat IP dan nomor port) milik server yg dituju. Kemudian, socket milik client secara otomatis dibuat oleh sistem operasi yg akan sebenarnya membuat request. Dalam request yg dikirimkan ke server, disertakan socket asal dan tujuan, sehingga server dapat memeriksa terlebih dahulu apakah request yg diterimanya memang benar-benar ditujukan kepadanya. Selain itu, dengan informasi alamat socket milik client, server akan mengetahui ke manakah server akan memberikan balasan.

Kode Program {#kode-program}
------------

### Aplikasi Server {#aplikasi-server}

Aplikasi server yg kita buat akan menggunakan port `8888`. Adapun alamat IP yg digunakan server merupakan alamat IP komputer di mana server dijalankan. Anda dapat menjalankan `ipconfig` di *command prompt* (jika Anda menggunakan Windows) untuk mengecek IP komputer Anda.

#### File: `PanggilSayaServer.java` {#file-panggilsayaserver.java}

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-java .line-numbers}
import java.io.DataInputStream;
import java.io.DataOutputStream;
import java.io.IOException;
import java.net.ServerSocket;
import java.net.Socket;
 
class PanggilSayaServer {
 
    public static void main(String[] args) {
        ServerSocket serverSocket = null;
        try {
            System.out.println(&quot;PanggilSayaServer sedang berjalan, menunggu request dari client.&quot;);
            // Server dijalankan menggunakan port 8888
            serverSocket = new ServerSocket(8888);
            while (true) {
                // Menerima request dari client. Gunakan socket baru untuk menangani request dari client
                Socket socket = serverSocket.accept();
 
                // Membaca stream input dari client
                DataInputStream dataInputStream = new DataInputStream(socket.getInputStream());
                String input = dataInputStream.readUTF();
 
                // Membuat stream output untuk memberikan respon kepada client
                DataOutputStream dataOutputStream = new DataOutputStream(socket.getOutputStream());
                String output = &quot;Halo, &quot; + input + &quot;!&quot;;
                dataOutputStream.writeUTF(output);
                dataOutputStream.flush();
                dataOutputStream.close();
                System.out.println(&quot;Nama client: &quot; + input);
            }
        } catch (IOException e) {
            e.printStackTrace();
            System.out.println(&quot;IOException: &quot; + e.toString());
        } finally {
            // Menghentikan server
            if (serverSocket != null) {
                try {
                    serverSocket.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Mari kita *compile* dan jalankan kode di atas.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
&gt; javac PanggilSayaServer.java
&gt; java PanggilSayaServer
  PanggilSayaServer sedang berjalan, menunggu request dari client.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Untuk menghentikan server, gunakan <kbd>Ctrl+C</kbd>.

### Aplikasi Client {#aplikasi-client}

Mari kita buat sebuah project Android baru dengan nama **Panggil Saya**. Saya menggunakan Android Studio 2.2 dan Java 1.8. Untuk nama package aplikasi, saya menggunakan `com.mikhsan.practice.panggilsaya`. Minimum SDK saya set API 16: Android 4.1 (Jelly Bean). Hal-hal tersebut, seperti nama aplikasi, bukanlah merupakan suatu ketentuan, silahkan dirubah sesuai keinginan Anda. Namun, jika Anda menggunakan nama package yg berbeda, pastikan Anda juga menyesuaikannya pada kode yg akan kita buat. Mari kita buat tampilan antarmukanya terlebih dahulu.

#### File: `activity_main.xml` {#file-activity_main.xml}

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-markup .line-numbers}
&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;
&lt;LinearLayout xmlns:android=&quot;http://schemas.android.com/apk/res/android&quot;
    xmlns:tools=&quot;http://schemas.android.com/tools&quot;
    android:id=&quot;@+id/activity_main&quot;
    android:layout_width=&quot;match_parent&quot;
    android:layout_height=&quot;match_parent&quot;
    android:paddingBottom=&quot;@dimen/activity_vertical_margin&quot;
    android:paddingLeft=&quot;@dimen/activity_horizontal_margin&quot;
    android:paddingRight=&quot;@dimen/activity_horizontal_margin&quot;
    android:paddingTop=&quot;@dimen/activity_vertical_margin&quot;
    android:orientation=&quot;vertical&quot;
    tools:context=&quot;com.mikhsan.practice.panggilsaya.MainActivity&quot;&gt;
 
    &lt;LinearLayout
        android:layout_width=&quot;match_parent&quot;
        android:layout_height=&quot;wrap_content&quot;
        android:orientation=&quot;horizontal&quot;&gt;
 
        &lt;EditText
            android:id=&quot;@+id/textIpAddress&quot;
            android:layout_width=&quot;0dp&quot;
            android:layout_height=&quot;wrap_content&quot;
            android:layout_weight=&quot;5&quot;
            android:inputType=&quot;textUri&quot;
            android:hint=&quot;Alamat IP Server&quot; /&gt;
 
        &lt;EditText
            android:id=&quot;@+id/textPort&quot;
            android:layout_width=&quot;0dp&quot;
            android:layout_height=&quot;wrap_content&quot;
            android:layout_weight=&quot;5&quot;
            android:inputType=&quot;number&quot;
            android:hint=&quot;Port&quot; /&gt;
    &lt;/LinearLayout&gt;
 
    &lt;EditText
        android:id=&quot;@+id/textRequest&quot;
        android:layout_width=&quot;match_parent&quot;
        android:layout_height=&quot;wrap_content&quot;
        android:inputType=&quot;textPersonName&quot;
        android:hint=&quot;Nama Saya&quot; /&gt;
 
    &lt;Button
        android:id=&quot;@+id/buttonSend&quot;
        android:layout_width=&quot;match_parent&quot;
        android:layout_height=&quot;wrap_content&quot;
        android:text=&quot;Panggil Saya!&quot; /&gt;
 
    &lt;ScrollView
        android:layout_width=&quot;match_parent&quot;
        android:layout_height=&quot;wrap_content&quot;
        android:layout_marginTop=&quot;20dp&quot;&gt;
 
        &lt;TextView
            android:id=&quot;@+id/textResponse&quot;
            android:layout_width=&quot;match_parent&quot;
            android:layout_height=&quot;wrap_content&quot;
            android:hint=&quot;Respon dari server&quot;
            android:text=&quot;&quot; /&gt;
    &lt;/ScrollView&gt;
&lt;/LinearLayout&gt;
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Untuk menangani masalah pembuatan request ke server dan menerima respon dari server, yg kemudian menampilkan respon tersebut, kita akan membuat sebuah kelas baru dengan nama `Communication`.

#### File: `Communication.java` {#file-communication.java}

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-java .line-numbers}
package com.mikhsan.practice.panggilsaya;
 
import android.os.AsyncTask;
import android.widget.TextView;
import java.io.DataInputStream;
import java.io.DataOutputStream;
import java.io.IOException;
import java.net.Socket;
import java.net.UnknownHostException;
 
public class Communication extends AsyncTask&lt;Void, Void, Void&gt; {
 
    String destAddress;
    int destPort;
    TextView textViewResponse;
    String textRequest;
    String message = &quot;&quot;;
 
    public Communication(String destAddress, int destPort, String textRequest, TextView textViewResponse) {
        this.destAddress = destAddress;
        this.destPort = destPort;
        this.textRequest = textRequest;
        this.textViewResponse = textViewResponse;
    }
 
    @Override
    protected Void doInBackground(Void... voids) {
        Socket socket = null;
 
        try {
            socket = new Socket(destAddress, destPort);
            DataOutputStream dataOutputStream = new DataOutputStream(socket.getOutputStream());
            dataOutputStream.writeUTF(textRequest);
            dataOutputStream.flush();
 
            DataInputStream dataInputStream = new DataInputStream(socket.getInputStream());
            message = dataInputStream.readUTF();
            dataInputStream.close();
        } catch (UnknownHostException e) {
            e.printStackTrace();
            message = &quot;UnknownHostException: &quot; + e.toString() + &quot;\r\n&quot;;
        } catch (IOException e) {
            e.printStackTrace();
            message = &quot;IOException: &quot; + e.toString() + &quot;\r\n&quot;;
        } finally {
            if (socket != null) {
                try {
                    socket.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
 
        return null;
    }
 
    @Override
    protected void onPostExecute (Void result) {
        String existingMessage = textViewResponse.getText().toString();
        message = existingMessage + message + &quot;\n&quot;;
        textViewResponse.setText(message);
        super.onPostExecute(result);
    }
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Selanjutnya, kita akan menginisialisasi objek `Communication` setiap kali tombol **Panggil Saya!** dan memulai komunikasi dengan server. Kode tersebut akan kita tambahkan ke file `MainActivity.java`.

#### File: `MainActivity.java` {#file-mainactivity.java}

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-java .line-numbers}
package com.mikhsan.practice.panggilsaya;
 
import android.app.Activity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
 
public class MainActivity extends Activity {
 
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
 
        ((Button) findViewById(R.id.buttonSend)).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                String destAddress = ((EditText) findViewById(R.id.textIpAddress)).getText().toString();
                int destPort = Integer.parseInt(((EditText) findViewById(R.id.textPort)).getText().toString());
                String textRequest = ((EditText) findViewById(R.id.textRequest)).getText().toString();
                TextView textViewResponse = (TextView) findViewById(R.id.textResponse);
 
                Communication communication = new Communication(destAddress, destPort, textRequest, textViewResponse);
                communication.execute();
            }
        });
    }
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Dan yang terakhir, karena kita melakukan komunikasi jaringan, maka kita perlu menambahkan sebuah `uses-permission` tag ke file `AndroidManifest.xml`.

#### **File: `AndroidManifest.xml`** {#file-androidmanifest.xml}

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-markup .line-numbers}
&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;
&lt;manifest xmlns:android=&quot;http://schemas.android.com/apk/res/android&quot;
    package=&quot;com.mikhsan.practice.panggilsaya&quot;&gt;
 
    &lt;uses-permission android:name=&quot;android.permission.INTERNET&quot; /&gt;
 
    &lt;application
        android:allowBackup=&quot;true&quot;
        android:icon=&quot;@mipmap/ic_launcher&quot;
        android:label=&quot;@string/app_name&quot;
        android:supportsRtl=&quot;true&quot;
        android:theme=&quot;@style/AppTheme&quot;&gt;
        &lt;activity android:name=&quot;.MainActivity&quot;&gt;
            &lt;intent-filter&gt;
                &lt;action android:name=&quot;android.intent.action.MAIN&quot; /&gt;

                &lt;category android:name=&quot;android.intent.category.LAUNCHER&quot; /&gt;
            &lt;/intent-filter&gt;
        &lt;/activity&gt;
    &lt;/application&gt;
 
&lt;/manifest&gt;
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Download Source Code {#download-source-code}
--------------------

<a class="btn btn-danger" href="http://belajarpemrograman.org/wp-content/uploads/2017/02/PanggilSayaServer.zip">Download Server Source Code</a>

<a class="btn btn-danger" href="http://belajarpemrograman.org/wp-content/uploads/2017/02/AndroidPanggilSaya.zip">Download Client (Android) Source Code</a>

[pada bagian akhir dari tulisan ini]: #download-source-code
[Belajar Pemrograman Socket Menggunakan Java]: http://belajarpemrograman.app/pemrograman-jaringan/belajar-pemrograman-socket-menggunakan-java/
[example.com]: http://example.com