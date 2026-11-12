# Kebijakan Eksekusi

AI tidak menjalankan atau membuka aplikasi/project dan tidak menjalankan server. Build dan run hanya dilakukan melalui pipeline project, bukan secara lokal oleh AI.

## Pemeriksaan kualitas

- Pipeline wajib menjalankan formatter, analyzer, unit/widget/integration test, dan coverage gate sesuai konfigurasi project.
- AI boleh melakukan pemeriksaan format, analyze, dan test yang tidak menjalankan aplikasi/project, mengikuti tooling dan kebiasaan project. Jangan menjalankan pemeriksaan yang diam-diam memulai aplikasi, server, atau build.
- Jangan menjalankan package install/update/remove, migration, seed, deployment, publish/release, atau perubahan remote tanpa permintaan dan otorisasi yang sesuai.
- Security scanner aktif, fuzzing, dan penetration test memerlukan otorisasi serta scope eksplisit.

## Inspeksi dan pelaporan

Inspeksi read-only seperti membaca file, melihat struktur, mencari teks, dan membaca status/diff diperbolehkan jika aman. Jangan menjalankan perintah dengan efek samping yang tidak jelas.

Lakukan review statis pada diff, logika, error handling, edge case, keamanan, kompatibilitas, struktur, serta dampak platform. Laporkan pemeriksaan yang benar-benar dijalankan, pipeline yang belum tersedia, dan risiko tersisa. Jangan mengklaim hasil yang belum dibuktikan.
