# Standar Flutter dan Dart

Berlaku wajib untuk project Flutter/Dart. Baca aturan project seperti `rules coding by TheRabdal.txt` sebelum perubahan; jika ada aturan project yang lebih ketat, ikuti aturan tersebut. Jangan melemahkan larangan di bawah berdasarkan preferensi pribadi.

## Konteks dan state

- Sebelum coding, tentukan apakah project/tugas termasuk tugas biasa atau enterprise. Jika tidak jelas dan pilihan memengaruhi implementasi, tanyakan kepada pengguna.
- Semua widget wajib `StatelessWidget`. `StatefulWidget` dan `setState()` dilarang.
- Pindahkan state dan lifecycle ke Provider untuk tugas, atau BLoC untuk enterprise/bahan belajar. Jangan mencampur Provider dan BLoC pada domain state yang sama.
- Provider adalah satu-satunya state management untuk tugas biasa. Jangan menambah state management lain ke domain yang sudah dikelola.
- Widget hanya menampilkan state dan meneruskan aksi; jangan letakkan business logic atau lifecycle widget di dalam widget.
- State harus private dan diakses lewat getter. Perubahan state dilakukan lewat method yang jelas dan `notifyListeners()` atau `emit`.
- Provider/BLoC tidak boleh menyimpan `BuildContext` atau menjalankan navigasi, dialog, dan SnackBar.
- Jangan panggil `notifyListeners()` saat state tidak berubah, di `build()`, atau di getter.

## Provider

- Satu class Provider mengelola satu domain state dan wajib `extends ChangeNotifier`. Letakkan di folder `provider`; gunakan penamaan file `snake_case` serta class `PascalCase`.
- Method perubahan state bersifat public dan bernama jelas; helper bersifat private. Satu method memiliki satu tanggung jawab.
- Method async wajib memakai `try/catch`, memetakan error, dan mengelola state loading/error/success dengan jelas.
- UI menggunakan `context.watch<T>()` untuk membaca state dan `context.read<T>()` untuk aksi. Gunakan `read` di callback; jangan gunakan `watch` di callback.
- Daftarkan Provider di atas widget yang memakainya, bukan di subtree yang terus di-rebuild. Jangan buat instance Provider baru di `build()`.
- Jangan menyimpan data sensitif tanpa pengamanan.
- Setiap Provider wajib memiliki unit test untuk method utama.

## BLoC

- BLoC hanya untuk project enterprise atau bahan belajar; bukan pilihan untuk tugas biasa.
- Gunakan `BlocBuilder` untuk UI state, `BlocListener` untuk aksi sekali jalan, dan `BlocConsumer` hanya jika keduanya diperlukan. Gunakan `buildWhen`/`listenWhen` bila tepat.
- Jangan letakkan `add()` atau business logic di builder/listener dan jangan simpan `BuildContext` di BLoC.
- UI harus menangani loading, success, error, dan empty state.
- Test BLoC dan perilaku builder/listener/consumer yang digunakan.

## Arsitektur, DI, dan animasi

- Ikuti arsitektur wajib pada `architecture.md`: presentation, domain, data; alur UI -> state -> usecase -> repository -> datasource.
- Gunakan `get_it` untuk service, repository, dan usecase; daftarkan di satu service locator.
- Prioritaskan animasi implisit. Jika `AnimationController` dibutuhkan, jangan tempatkan di widget; kelola di Provider/BLoC dengan mekanisme `vsync_provider` atau yang setara dan dispose dengan benar.
- Package animasi pihak ketiga hanya boleh digunakan setelah evaluasi keamanan dan pemeliharaan.
- Animasi tidak boleh menyebabkan rebuild berlebihan.

## UI dan kualitas

- Prioritaskan `Container` bila sesuai. Gunakan `Expanded` saat diperlukan agar flex layout benar; jangan menggantinya jika mengakibatkan overflow atau ukuran tidak terkontrol.
- Gunakan `const` bila valid.
- Layout harus responsif untuk web dan mobile. Sediakan loading, success, error, dan empty state untuk alur data yang relevan.
- Penuhi aksesibilitas: semantics, ukuran tap minimum, dan kontras warna. Siapkan internasionalisasi dengan `intl` sejak awal.
- Ikuti `dart format` dan `dart analyze` tanpa warning melalui pipeline yang ditetapkan. Pemeriksaan lokal hanya boleh dilakukan jika tidak menjalankan aplikasi/project.
- Hindari komentar untuk hal obvious. Tambahkan komentar untuk alasan bisnis dan dokumentasikan API publik sesuai kebutuhan.
- Bug yang ditemukan wajib mendapat regression test.

## Testing dan ketahanan

- Wajib unit test untuk Provider, BLoC, usecase, repository, dan datasource.
- Wajib widget test untuk layar kritis dan integration test untuk alur utama end-to-end. Golden test untuk komponen UI stabil dan contract test untuk API jika kontraknya tersedia.
- CI wajib menerapkan coverage gate 70-80% untuk modul inti. Test harus deterministik dan tidak bergantung pada waktu/jaringan nyata.
- Semua operasi async wajib menggunakan `try/catch` dan memetakan error dengan jelas; operasi jaringan wajib memiliki timeout. Retry dengan backoff hanya untuk operasi yang aman diulang.
- Terapkan caching untuk data yang relevan, offline mode, dan fallback UI sesuai kebutuhan fitur. Jangan biarkan exception yang tidak tertangani sampai ke UI.

## Logger, observability, dan proses rilis

- Jika floating logger digunakan, aktif hanya di debug/staging, nonaktif di production, satu instance di atas `MaterialApp`, dan tidak dibuat di widget yang di-rebuild. Test harus memastikan logger nonaktif di production dan tidak mencatat data sensitif.
- Logger harus memakai level yang jelas dan tidak mencatat token, password, atau data pribadi. Floating logger bukan crash reporting.
- Project wajib memiliki structured logging, crash reporting, analytics fitur utama sesuai kebijakan privasi, tracing alur kritis, dan alerting error/performa.
- Pipeline wajib menjalankan format, analyze, unit/widget/integration test, coverage gate, SAST, dan DAST sesuai konfigurasi project. Jangan commit, merge, atau rilis kode yang gagal analyze atau test. Build otomatis untuk dev/staging/production.
- Gunakan semantic versioning, changelog setiap rilis, dan rollback plan. AI tidak menjalankan aplikasi/project atau build/run lokal; lihat `strict-execution.md`.

## Keamanan dan perubahan visual

- Terapkan ketentuan keamanan serta privasi di `security-audit.md`.
- Saat diminta hanya merapikan kode, pertahankan render UI: jangan mengubah ukuran, warna, spacing, teks, ikon, urutan, maupun struktur yang memengaruhi tampilan.
- Jika refactor mungkin mengubah visual, berhenti dan minta konfirmasi. Jangan melakukan Extract Widget otomatis; lihat `refactoring.md`.
