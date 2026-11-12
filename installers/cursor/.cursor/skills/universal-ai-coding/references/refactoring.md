# Refactoring Rules

- Refactoring wajib mempertahankan perilaku yang ada kecuali perubahan perilaku diminta.
- Baca caller, dependency, kontrak, dan perubahan manual sebelum mengubah signature atau implementasi.
- Periksa status/diff secara read-only. Jangan menimpa atau menyentuh perubahan manual tanpa konfirmasi.
- Gunakan patch terkecil; ubah hanya file yang diperlukan. Hindari rewrite file penuh atau perubahan format massal.
- Jangan menghapus validasi, permission, fallback, logging keamanan, atau test agar perubahan tampak lulus.
- Jangan melakukan Extract Widget otomatis. Extract Widget hanya dilakukan manual oleh pemilik modul.
- Jangan tinggalkan TODO tanpa tiket.
- Jangan menambah folder di luar struktur wajib tanpa persetujuan.

## Perlindungan visual

Jika permintaan hanya merapikan/refactor tanpa mengubah tampilan, hasil render UI wajib tetap sama:

- Jangan mengubah ukuran, warna, padding, margin, radius, font, ikon, posisi, urutan, teks, label, placeholder, atau nilai default yang terlihat.
- Jangan mengganti jenis widget atau struktur layout (misalnya Row/Column/Stack) jika berpotensi mengubah hasil render. Penggantian hanya boleh bila hasil visual identik.
- Perubahan dibatasi pada bagian yang tidak terlihat seperti penamaan, import/export, pemisahan logic, format, struktur file, atau penghapusan duplikasi yang aman.
- Jika berpotensi mengubah visual atau ada keraguan, berhenti dan minta konfirmasi.
- Laporkan daftar perubahan dan nyatakan apakah ada perubahan visual. Jangan menyatakan tidak ada perubahan visual tanpa memeriksa diff dengan cermat.

Laporkan risiko, ketidakpastian, dan verifikasi yang belum dilakukan.
