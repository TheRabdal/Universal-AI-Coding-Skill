# Security, Privacy, and Observability

Lakukan review keamanan proporsional pada semua perubahan; lakukan threat model untuk fitur baru yang menyentuh data sensitif. Security audit wajib sebelum rilis. Jangan menyebut aplikasi sepenuhnya aman tanpa bukti yang memadai.

## Checklist keamanan

- **Secrets:** jangan hardcode secret, API key, token, atau password. Simpan di secret manager/CI secret, bukan repository.
- **Storage:** simpan token menggunakan secure storage (Flutter: `flutter_secure_storage`), bukan `SharedPreferences` biasa. Lindungi data sensitif pada state/cache/log.
- **Transport:** wajib HTTPS/TLS; certificate pinning wajib untuk endpoint kritis.
- **Input/API:** validasi dan sanitasi input pengguna dan respons API. Validasi tipe, panjang, format, rentang, business rules, content type, ukuran payload, dan HTTP method sesuai konteks.
- **Access control:** least privilege, server-side authorization, default-deny, ownership/tenant checks, dan permission pada setiap operasi sensitif.
- **Release:** obfuscate build release Flutter dengan `--obfuscate --split-debug-info`; obfuscation bukan pengganti keamanan backend.
- **Dependencies:** audit dependency berkala dan pin versi dependency kritis. Evaluasi sumber, versi, pemeliharaan, lockfile, dan lifecycle scripts.
- **Pipeline:** gunakan SAST dan DAST dalam pipeline. Jangan menjalankan scanner aktif, fuzzing, atau penetration test tanpa otorisasi dan scope eksplisit.
- **Threat modeling:** lakukan untuk fitur baru yang memproses data sensitif.

## Review teknis sesuai permukaan serangan

- Authentication: bypass, session fixation/expiry, token leakage, password handling, reset flow, dan MFA jika relevan.
- Authorization: IDOR/BOLA, privilege escalation, tenant isolation, ownership, dan pemeriksaan server-side.
- Injection: SQL/NoSQL/ORM, command, template, XSS, LDAP, path traversal, header injection, dan unsafe deserialization. Gunakan parameterized query serta encoder sesuai konteks.
- Web/API: CSRF, CORS, CSP, clickjacking, SSRF, open redirect, request smuggling, rate limits, mass assignment, dan kebocoran detail internal.
- File: validasi ekstensi, MIME, ukuran, isi, nama dan lokasi; cegah traversal, overwrite, executable upload, dan akses publik tak sengaja.
- Data/ops: periksa `.env`, config, storage, backup, cache, telemetry, retention, debug mode, default credentials, error leakage, admin routes, serta cloud permissions.
- Flutter/mobile: deep link/intent, WebView, backup, screenshot, clipboard, logging, certificate validation, dan asumsi client-side tentang role/harga/transaksi.

## Privasi dan observability

- Klasifikasikan data sebagai publik, internal, atau sensitif. Minimalkan pengumpulan data pribadi dan jelaskan dasar kebutuhannya.
- Batasi retensi log/analytics. Analytics opt-in jika diwajibkan regulasi; jangan kirim data pribadi ke pihak ketiga tanpa persetujuan.
- Structured logging wajib memuat level dan konteks tanpa secret atau data pribadi.
- Project wajib memiliki crash reporting (Sentry/Firebase Crashlytics), analytics untuk fitur utama sesuai kebijakan privasi, tracing alur kritis, dan alerting error rate/performa.
- Floating logger hanya untuk debug/staging, tidak aktif di production, tidak memuat data sensitif, dan bukan pengganti crash reporting. Terapkan detail Flutter di `flutter-standards.md`.

## Pelaporan temuan

Setiap temuan mencantumkan ID, nama/kategori, severity (Critical/High/Medium/Low/Informational), file/lokasi bila diketahui, bukti teknis aman, dampak, prasyarat, rekomendasi, dan status Confirmed/Suspected/Not Reproduced. Bedakan bukti dari dugaan. Jangan mengakses data nyata atau membuat exploit untuk pembuktian tanpa izin.
