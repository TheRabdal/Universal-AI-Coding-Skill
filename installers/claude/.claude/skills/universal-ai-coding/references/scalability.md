# Skalabilitas, UI, dan Cross-platform

- Untuk Flutter, layout harus scalable/responsif untuk web dan mobile serta memperhatikan constraints, safe area, keyboard, text scaling, touch/pointer, dan ukuran layar.
- Wajib accessibility: semantics yang tepat, ukuran tap minimum, dan kontras warna memadai.
- Wajib menyiapkan internasionalisasi (`intl`) sejak awal.
- Sediakan state loading, success, error, dan empty untuk alur data yang relevan.
- Pisahkan business logic dari UI dan ikuti alur arsitektur yang diwajibkan di `architecture.md`.
- Tetapkan performance budget untuk ukuran build, startup time, dan penggunaan memori.
- Hindari rebuild berlebihan; gunakan `const`, `buildWhen`, atau `listenWhen` sesuai aturan Flutter dan tanpa menurunkan keterbacaan.
- Hindari pekerjaan berat di main thread. Ukur performa sebelum/sesudah perubahan besar melalui pipeline atau tooling yang dijalankan pemilik project, bukan AI.
- Untuk operasi jaringan: gunakan timeout, retry dengan backoff hanya untuk operasi aman diulang, caching jika relevan, dan offline mode/fallback UI.
- Hindari asumsi filesystem, path, permission, dan lifecycle yang hanya berlaku di satu platform. Gunakan platform abstraction hanya bila ada kebutuhan nyata.
- Hindari premature optimization serta arsitektur untuk kebutuhan hipotetis.
