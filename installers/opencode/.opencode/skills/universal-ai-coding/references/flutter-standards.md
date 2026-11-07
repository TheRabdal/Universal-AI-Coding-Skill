# Standar Flutter dan Dart

Berlaku hanya untuk project Flutter/Dart.

- `StatelessWidget` wajib diprioritaskan; `StatefulWidget` dilarang kecuali pengguna secara eksplisit memberi pengecualian.
- Provider adalah state management utama. Pisahkan state/business logic dari widget.
- Hindari local mutable state yang membutuhkan `StatefulWidget`; gunakan Provider atau pendekatan eksternal yang cocok.
- Prioritaskan `Container` jika cocok. `Expanded` tetap digunakan saat dibutuhkan untuk flex layout yang benar; jangan memaksakan Container hingga overflow.
- Hindari `const` kecuali diperlukan.
- Jangan menambah komentar kode.
- `packages.dart` digunakan sebagai pusat import/export hanya jika sesuai dengan struktur project. Hindari circular dependency dan barrel export yang merugikan.
- `models/`, `provider/`, `widgets/` bukan struktur wajib universal; ikuti existing architecture.
- Perhatikan web/mobile: responsive constraints, keyboard, pointer/touch, safe area, text scaling, accessibility, dan ukuran layar.
- Jangan menjalankan `flutter run`, `flutter build`, `flutter test`, `dart format`, atau analyzer tanpa izin.
