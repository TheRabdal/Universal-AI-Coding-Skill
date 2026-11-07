# Refactoring Rules

- Pertahankan perilaku kecuali perubahan perilaku diminta.
- Baca caller, dependency, dan kontrak terkait sebelum mengubah signature.
- Periksa diff dan lindungi perubahan lokal.
- Ubah sesedikit mungkin file.
- Hindari perubahan format massal yang menyamarkan perubahan logika.
- Pertahankan kompatibilitas API/data bila diminta.
- Jangan menghapus validasi, permission, fallback, logging keamanan, atau test untuk membuat perubahan tampak lulus.
- Laporkan risiko dan verifikasi yang belum dilakukan.
