# My Fastfetch Config

Konfigurasi [fastfetch](https://github.com/fastfetch-cli/fastfetch) dengan logo ASCII art buatan sendiri. Mudah diubah dan bisa dipakai di Arch Linux maupun FreeBSD.

<!-- Hapus tanda komentar di bawah kalau sudah ada screenshot bernama preview.png di repo ini -->
<!-- ![preview](preview.png) -->

## Isi repo

| File | Fungsi |
|------|--------|
| `config.jsonc` | Pengaturan utama: logo, warna, dan info yang ditampilkan |
| `ascii.txt` | ASCII art yang dipakai sebagai logo |
| `install.sh` | Script untuk menyalin file di atas ke `~/.config/fastfetch/` |

## Cara install

**1. Install fastfetch**

```bash
# Arch Linux
sudo pacman -S fastfetch

# FreeBSD (jalankan sebagai root)
pkg install fastfetch
```

**2. Clone repo dan jalankan installer**

```bash
git clone https://github.com/Hdumbs/my-fastfetch-config-v1.git
cd my-fastfetch-config-v1
sh install.sh
```

**3. Jalankan**

```bash
fastfetch
```

> Catatan: `install.sh` akan menimpa `~/.config/fastfetch/config.jsonc` yang sudah ada. Kalau mau mengamankan config lama, backup dulu:
> `cp ~/.config/fastfetch/config.jsonc ~/.config/fastfetch/config.jsonc.bak`

## Mengganti ASCII art

Ada dua cara:

**a. Pakai ASCII art sendiri.** Isi file `~/.config/fastfetch/ascii.txt` dengan art-mu (bisa dari website generator ASCII art), simpan, lalu jalankan `fastfetch`.

**b. Ubah foto jadi ASCII dengan `jp2a`** (mendukung JPG dan PNG):

```bash
sudo pacman -S jp2a
jp2a --width=40 ~/Pictures/foto.jpg > ~/.config/fastfetch/ascii.txt
```

Tips:
- Kalau hasilnya terlihat seperti negatif, tambahkan `--invert`.
- Mau berwarna? Tambahkan `--color`.
- Ukuran diatur lewat `--width=` (makin besar angkanya, makin besar art-nya).

Config ini memakai logo tipe `file-raw`, yaitu teks dicetak persis seperti isi filenya. Ini aman untuk art yang berisi karakter `$`.

## Mengatur tampilan

Semua pengaturan ada di `~/.config/fastfetch/config.jsonc`:

- **Logo**: ubah `"type"` dan `"source"` di bagian `logo`.
- **Warna**: ubah `"keys"` dan `"title"` di bagian `display`.
- **Info yang tampil**: edit daftar `modules`. Pindahkan baris untuk mengubah urutan, hapus atau beri `//` di depannya untuk menyembunyikan.
- Lihat semua modul yang tersedia: `fastfetch --list-modules`

Setiap selesai mengubah, simpan file lalu jalankan `fastfetch` lagi.

## Tes tanpa mengubah config

```bash
fastfetch --file-raw ~/.config/fastfetch/ascii.txt
```

## Jalan otomatis setiap buka terminal

Tambahkan `fastfetch` di baris paling bawah `~/.bashrc` (atau `~/.zshrc` kalau pakai zsh).

## Troubleshooting

- **Logo tidak muncul / kembali ke logo bawaan:** jalankan `fastfetch --show-errors` untuk melihat penyebabnya. Pastikan path di `"source"` benar dan file `ascii.txt` ada.
- **`install.sh` bilang file tidak ditemukan:** jalankan script dari dalam folder repo (`cd my-fastfetch-config-v1`).
- **ASCII art terlihat berantakan:** kecilkan ukurannya (`--width=` lebih kecil) atau pakai font monospace di terminalmu.

## Lisensi

Bebas dipakai dan diubah.
