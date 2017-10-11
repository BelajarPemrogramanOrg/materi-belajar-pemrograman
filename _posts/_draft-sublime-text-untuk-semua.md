---
post_title: "Sublime Text untuk Semua"
layout: post
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
	"bold_folder_labels": true,
	"caret_extra_bottom": 2,
	"caret_extra_top": 2,
	"caret_style": "phase",
	"default_line_ending": "unix",
	"detect_indentation": false,
	"ensure_newline_at_eof_on_save": true,
	"findreplace_small": true,
	"highlight_line": true,
	"highlight_modified_tabs": true,
	"line_padding_bottom": 4,
	"line_padding_top": 4,
	"show_encoding": true,
	"show_line_endings": true,
	"show_panel_on_build": false,
	"tabs_medium": true,
	"trim_trailing_white_space_on_save": true
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Loh, settingan di atas dimasukkannya ke mana? Buka **Preferences** > **Settings**. Pada jendela Sublime yang dibuka, di sisi kiri berisikan pengaturan default Sublime, sedangkan di sisi kanan kita bisa memasukkan pengaturan kita sendiri. Pengaturan yang kita masukkan memiliki prioritas yang lebih tinggi daripada pengaturan default yang sudah ada. Jadi, kita bisa meng-*override* pengaturan default.