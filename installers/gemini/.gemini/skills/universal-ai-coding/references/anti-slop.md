# Anti-Slop Rules

Hindari boilerplate berlebihan, penamaan generik, komentar generik, abstraksi prematur, helper/wrapper/manager yang tidak diperlukan, dependency/configuration berlebihan, duplikasi, dead code, placeholder tidak berlabel, serta fallback yang menelan error.

- Gunakan solusi paling sederhana yang benar, patch sekecil mungkin, dan pola project yang dipahami.
- Jangan gunakan `dynamic`/`any`, cast, atau lint suppression untuk menghindari penyelesaian akar masalah.
- Jangan menghapus validasi atau kontrol keamanan untuk membuat perubahan tampak lulus.
- Jangan membuat file/class/method/test yang tidak dibutuhkan.
- Jangan membuat test yang tidak deterministik atau bergantung pada waktu/jaringan nyata.
- Jangan menambahkan komentar untuk hal obvious; komentar harus menjelaskan alasan bisnis atau keputusan non-obvious.
- Jangan tinggalkan TODO tanpa tiket.
- Jangan lakukan Extract Widget otomatis; perubahan itu harus dilakukan manual oleh pemilik modul.
- Jangan menambah folder di luar struktur wajib tanpa persetujuan.
- Jangan mengklaim test, security, performa, atau kesiapan production tanpa bukti yang sesuai.

Pahami batas tugas; jangan mengubah kode yang telah dimodifikasi manual tanpa konfirmasi. Laporkan trade-off yang relevan saja.
