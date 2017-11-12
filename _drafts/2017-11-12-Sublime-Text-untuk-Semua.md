---
ID: 952
post_title: Sublime Text untuk Semua
author: Muhammad Ikhsan
post_excerpt: ""
layout: post
permalink: http://belajarpemrograman.org/?p=952
published: false
---
## Pendahuluan

[Sublime Text](https://www.sublimetext.com/) merupakan salah satu text editor yang populer di kalangan programmer. Materi belajar ini akan membahas bagaimana memaksimalkan penggunaan Sublime Text untuk ngoding. Diharapkan, kita bisa lebih produktif dan juga nyaman dalam bekerja. Bisa jadi kita menghabiskan separuh hari kita di hadapan text editor untuk bekerja. Nah, dengan memiliki kuasa penuh terhadap text editor yang digunakan, tentunya pekerjaan dapan dijalani dengan lebih nyaman.

### Kenapa Memakai Sublime? {.no-mar-top}

- Ringan, gak sampai 10mb *installer*-nya. Pas dipakainya juga ringan, karena ditulis menggunakan C++ (mungkin Notepad++ juga iya). Berbeda dengan VS Code, Atom dan Brackets yang gak *native* desktop.
- Banyak pilihan tema dan *package-package* tambahan lainnya
- Gak sulit belajarnya, beda dengan kalau mau belajar Vim atau malah Emacs

## Keyboard Shortcut

| Fungsi                                       | Keyboard Shortcut
| -------------------------------------------- | ---------------------
| Toggle sidebar                               | `Ctrl + K` `Ctrl + B`

## Package Control

[Package Control](https://packagecontrol.io/) merupakan *package manager* untuk Sublime Text. *Package* yang dimaksud di sini dapat berupa *color scheme*, tema, snippet, atau segala macamnya lah yang memberikan fungsi tambahan pada Sublime Text. Dengan menggunakan Package Control, Anda dapat menginstal, mengupgrade, menghapus, menonaktifkan, bahkan membuat package Anda sendiri.

Untuk dapat menggunakan Package Control, Anda harus menginstalnya terlebih dahulu. Petunjuk penginstalannya dapat Anda lihat di [https://packagecontrol.io/installation](https://packagecontrol.io/installation).

## Settingan Saya

Di bawah ini merupakan pengaturan dasar level user yang saya pakai:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ {.language-json .line-numbers}
{
	&quot;bold_folder_labels&quot;: true,
	&quot;caret_extra_bottom&quot;: 2,
	&quot;caret_extra_top&quot;: 2,
	&quot;caret_style&quot;: &quot;phase&quot;,
	&quot;default_line_ending&quot;: &quot;unix&quot;,
	&quot;detect_indentation&quot;: false,
	&quot;ensure_newline_at_eof_on_save&quot;: true,
	&quot;findreplace_small&quot;: true,
	&quot;highlight_line&quot;: true,
	&quot;highlight_modified_tabs&quot;: true,
	&quot;line_padding_bottom&quot;: 4,
	&quot;line_padding_top&quot;: 4,
	&quot;show_encoding&quot;: true,
	&quot;show_line_endings&quot;: true,
	&quot;show_panel_on_build&quot;: false,
	&quot;tabs_medium&quot;: true,
	&quot;trim_trailing_white_space_on_save&quot;: true
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Loh, settingan di atas dimasukkannya ke mana? Buka **Preferences** > **Settings**. Pada jendela Sublime yang dibuka, di sisi kiri berisikan pengaturan default Sublime, sedangkan di sisi kanan kita bisa memasukkan pengaturan kita sendiri. Pengaturan yang kita masukkan memiliki prioritas yang lebih tinggi daripada pengaturan default yang sudah ada. Jadi, kita bisa meng-*override* pengaturan default.