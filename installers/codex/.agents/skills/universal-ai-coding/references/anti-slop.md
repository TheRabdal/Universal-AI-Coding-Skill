# Anti-Slop Rules

Tolak kode yang hanya terlihat canggih tetapi tidak menyelesaikan kebutuhan.

Hindari:
- boilerplate dan abstraksi prematur;
- helper/wrapper/manager yang tidak diperlukan;
- dependency dan konfigurasi berlebihan;
- duplikasi atau dead code;
- `any`/`dynamic`, cast, dan lint suppression untuk menyembunyikan masalah;
- fallback yang menelan error;
- rewrite file penuh untuk perubahan kecil;
- placeholder yang tidak diberi label;
- klaim test atau security tanpa bukti.

Pilih patch terkecil yang benar. Gunakan pola existing. Buat kode mudah dipahami engineer berikutnya.
