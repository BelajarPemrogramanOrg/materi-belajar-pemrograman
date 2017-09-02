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
Dalam materi belajar ini, kita akan membuat dua buah program sederhana untuk menerapkan komunikasi client - server menggunakan socket. Aplikasi client yg akan kita buat berupa sebuah aplikasi Android, sedangkan aplikasi server berupa program yg ditulis dalam bahasa pemrograman Java yg dijalankan di komputer. Anda dapat mendownload source code aplikasi yg akan kita buat <a href="http://belajarpemrograman.org/belajar-pemrograman-socket-client-server-menggunakan-android-dan-java/#download-source-code">pada bagian akhir dari tulisan ini</a>.

<h2 id="detail-aplikasi">Detail Aplikasi</h2>

Berikut merupakan detail dari aplikasi yg akan kita buat:

<ul>
<li>Sebuah aplikasi Android akan dibuat sebagai client. Aplikasi diberi nama <strong>Panggil Saya</strong>. <em>(Gak usah protes soal nama.. Silahkan kalo mau ganti. hehe)</em></li>
<li>Sebuah aplikasi yg ditulis dengan Java akan dijalankan sebagai server dalam sebuah komputer.</li>
<li>Untuk menjalankannya, perangkat Android dan komputer harus berada dalam satu jaringan, misalnya keduanya terkoneksi pada jaringan wireless yg sama. Dapat menggunakan <em>tether</em>.</li>
<li>Aplikasi client (aplikasi Android) akan mengirimkan <code>{nama orang}</code>, dan server akan memberikan balasan berupa <code>Halo, {nama orang}!</code>.
Contoh: client mengirimkan <code>Ikhsan</code>, kemudian server akan membalasnya dengan <code>Halo, Ikhsan!</code>.</li>
<li>Antarmuka aplikasi Android terdiri dari:

<ul>
<li>Sebuah <code>EditText</code> untuk mengisikan IP server</li>
<li>Sebuah <code>EditText</code> untuk mengisikan port yg digunakan oleh server untuk menerima request</li>
<li>Sebuah <code>EditText</code> untuk mengisikan nama orang yg akan dikirimkan ke server</li>
<li>Sebuah <code>Button</code> untuk mengirimkan request ke server</li>
<li>Sebuah <code>TextView</code> untuk menampilkan respon dari server</li>
</ul></li>
</ul>

Berikut merupakan <em>screenshot</em> yang dapat membantu menggambarkan jalannya aplikasi yg akan kita buat. Klik gambar untuk memperbesar.
[gallery type="rectangular" link="file" size="medium" ids="176,180,182"]

<h2 id="mengenal-socket">Mengenal Socket</h2>

<strong><em>Wait</em>,</strong> sebelum kita lanjutkan, pastikan kita sudah mengerti apa yg dimaksud dengan <em>socket</em> yg dari tadi disebut-sebut. Kalau kelihatan ribet, setidaknya dibaca saja. Semoga nanti setelah praktik membuat aplikasinya dan berhasil menjalankannya, jadi lebih ngerti.

Mengenai pemrograman socket menggunakan bahasa pemrograman Java yang tidak dibahas secara mendetail dalam tulisan ini, Anda dapat membacanya pada tulisan lain di website ini yg berjudul <a href="http://belajarpemrograman.app/pemrograman-jaringan/belajar-pemrograman-socket-menggunakan-java/">Belajar Pemrograman Socket Menggunakan Java</a>.

<h3 id="pengertian-socket">Pengertian Socket</h3>

<ul>
<li>Socket merupakan sebuah titik akhir dalam komunikasi dua arah antara dua program pada suatu jaringan.</li>
<li>Sebuah socket terdiri dari alamat IP dan port. Contoh: <code>172.20.10.5:8888</code>. <code>172.20.10.5</code> merupakan alamat IP dan <code>8888</code> merupakan port.</li>
</ul>

Dalam komunikasi antara 2 program (client dan server), masing-masing memiliki socket sebagai titik akhir dalam komunikasi. Jika client ingin meminta request kepada server, maka client akan menghubungi socket milik server. Begitu pula sebaliknya, ketika server akan memberikan balasan kepada client, maka server akan mengirimkan balasan tersebut ke socket milik client.

<h3 id="contoh-skenario-penggunaan-socket">Contoh Skenario Penggunaan Socket</h3>

Sebagai contoh, Anda mengakses sebuah website melalui browser, misalnya <a href="http://example.com">example.com</a>. Browser di komputer Anda merupakan sebuah aplikasi client yg meminta request ke <em>web server</em> yg meng-<em>host</em> <a href="http://example.com">example.com</a>. Browser Anda akan meminta agar sistem operasi Anda menyiapkan socket untuk komunikasi ke server dengan <em>hostname</em> <a href="http://example.com">example.com</a> dan port <code>80</code> (nomor port yg digunakan untuk <code>http</code>). Dalam paket jaringan yg dikirimkan oleh sistem operasi, akan disertakan beberapa informasi, termasuk alamat IP dan port komputer Anda yg digunakan untuk komunikasi socket, dan alamat IP dan nomor port tujuan (server). Selanjutnya, jika semuanya berjalan dengan baik, server akan menerima request dan dapat memberikan respon yg sesuai kepada client.

Dari contoh yg disebutkan di atas, client harus sudah mengetahui socket (alamat IP dan nomor port) milik server yg dituju. Kemudian, socket milik client secara otomatis dibuat oleh sistem operasi yg akan sebenarnya membuat request. Dalam request yg dikirimkan ke server, disertakan socket asal dan tujuan, sehingga server dapat memeriksa terlebih dahulu apakah request yg diterimanya memang benar-benar ditujukan kepadanya. Selain itu, dengan informasi alamat socket milik client, server akan mengetahui ke manakah server akan memberikan balasan.

<h2 id="kode-program">Kode Program</h2>

<h3 id="aplikasi-server">Aplikasi Server</h3>

Aplikasi server yg kita buat akan menggunakan port <code>8888</code>. Adapun alamat IP yg digunakan server merupakan alamat IP komputer di mana server dijalankan. Anda dapat menjalankan <code>ipconfig</code> di <em>command prompt</em> (jika Anda menggunakan Windows) untuk mengecek IP komputer Anda.

<h4 id="file-panggilsayaserver" class="java">File: <code>PanggilSayaServer.java</code></h4>

<pre><code class="language-java line-numbers">import java.io.DataInputStream;
import java.io.DataOutputStream;
import java.io.IOException;
import java.net.ServerSocket;
import java.net.Socket;
 
class PanggilSayaServer {
 
    public static void main(String[] args) {
        ServerSocket serverSocket = null;
        try {
            System.out.println("PanggilSayaServer sedang berjalan, menunggu request dari client.");
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
                String output = "Halo, " + input + "!";
                dataOutputStream.writeUTF(output);
                dataOutputStream.flush();
                dataOutputStream.close();
                System.out.println("Nama client: " + input);
            }
        } catch (IOException e) {
            e.printStackTrace();
            System.out.println("IOException: " + e.toString());
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
</code></pre>

Mari kita <em>compile</em> dan jalankan kode di atas.

<pre><code>&gt; javac PanggilSayaServer.java
&gt; java PanggilSayaServer
  PanggilSayaServer sedang berjalan, menunggu request dari client.
</code></pre>

Untuk menghentikan server, gunakan <kbd>Ctrl+C</kbd>.

<h3 id="aplikasi-client">Aplikasi Client</h3>

Mari kita buat sebuah project Android baru dengan nama <strong>Panggil Saya</strong>. Saya menggunakan Android Studio 2.2 dan Java 1.8. Untuk nama package aplikasi, saya menggunakan <code>com.mikhsan.practice.panggilsaya</code>. Minimum SDK saya set API 16: Android 4.1 (Jelly Bean). Hal-hal tersebut, seperti nama aplikasi, bukanlah merupakan suatu ketentuan, silahkan dirubah sesuai keinginan Anda. Namun, jika Anda menggunakan nama package yg berbeda, pastikan Anda juga menyesuaikannya pada kode yg akan kita buat. Mari kita buat tampilan antarmukanya terlebih dahulu.

<h4 id="file-activity_main" class="xml">File: <code>activity_main.xml</code></h4>

<pre><code class="language-markup line-numbers">&lt;?xml version="1.0" encoding="utf-8"?&gt;
&lt;LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/activity_main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:paddingBottom="@dimen/activity_vertical_margin"
    android:paddingLeft="@dimen/activity_horizontal_margin"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin"
    android:orientation="vertical"
    tools:context="com.mikhsan.practice.panggilsaya.MainActivity"&gt;
 
    &lt;LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"&gt;
 
        &lt;EditText
            android:id="@+id/textIpAddress"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="5"
            android:inputType="textUri"
            android:hint="Alamat IP Server" /&gt;
 
        &lt;EditText
            android:id="@+id/textPort"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="5"
            android:inputType="number"
            android:hint="Port" /&gt;
    &lt;/LinearLayout&gt;
 
    &lt;EditText
        android:id="@+id/textRequest"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:inputType="textPersonName"
        android:hint="Nama Saya" /&gt;
 
    &lt;Button
        android:id="@+id/buttonSend"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Panggil Saya!" /&gt;
 
    &lt;ScrollView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="20dp"&gt;
 
        &lt;TextView
            android:id="@+id/textResponse"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:hint="Respon dari server"
            android:text="" /&gt;
    &lt;/ScrollView&gt;
&lt;/LinearLayout&gt;
</code></pre>

Untuk menangani masalah pembuatan request ke server dan menerima respon dari server, yg kemudian menampilkan respon tersebut, kita akan membuat sebuah kelas baru dengan nama <code>Communication</code>.

<h4 id="file-communication" class="java">File: <code>Communication.java</code></h4>

<pre><code class="language-java line-numbers">package com.mikhsan.practice.panggilsaya;
 
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
    String message = "";
 
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
            message = "UnknownHostException: " + e.toString() + "\r\n";
        } catch (IOException e) {
            e.printStackTrace();
            message = "IOException: " + e.toString() + "\r\n";
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
        message = existingMessage + message + "\n";
        textViewResponse.setText(message);
        super.onPostExecute(result);
    }
}
</code></pre>

Selanjutnya, kita akan menginisialisasi objek <code>Communication</code> setiap kali tombol <strong>Panggil Saya!</strong> dan memulai komunikasi dengan server. Kode tersebut akan kita tambahkan ke file <code>MainActivity.java</code>.

<h4 id="file-mainactivity" class="java">File: <code>MainActivity.java</code></h4>

<pre><code class="language-java line-numbers">package com.mikhsan.practice.panggilsaya;
 
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
</code></pre>

Dan yang terakhir, karena kita melakukan komunikasi jaringan, maka kita perlu menambahkan sebuah <code>uses-permission</code> tag ke file <code>AndroidManifest.xml</code>.

<h4 id="file-androidmanifest" class="xml"><strong>File: <code>AndroidManifest.xml</code></strong></h4>

<pre><code class="language-markup line-numbers">&lt;?xml version="1.0" encoding="utf-8"?&gt;
&lt;manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.mikhsan.practice.panggilsaya"&gt;
 
    &lt;uses-permission android:name="android.permission.INTERNET" /&gt;
 
    &lt;application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:supportsRtl="true"
        android:theme="@style/AppTheme"&gt;
        &lt;activity android:name=".MainActivity"&gt;
            &lt;intent-filter&gt;
                &lt;action android:name="android.intent.action.MAIN" /&gt;

                &lt;category android:name="android.intent.category.LAUNCHER" /&gt;
            &lt;/intent-filter&gt;
        &lt;/activity&gt;
    &lt;/application&gt;
 
&lt;/manifest&gt;
</code></pre>

<h2 id="download-source-code">Download Source Code</h2>

[su_button url="http://belajarpemrograman.org/wp-content/uploads/2017/02/PanggilSayaServer.zip" background="#909090" icon="icon: cloud-download"]Download Server Source Code[/su_button] [su_button url="http://belajarpemrograman.org/wp-content/uploads/2017/02/AndroidPanggilSaya.zip" background="#909090" icon="icon: cloud-download"]Download Client Source Code[/su_button]