# Arsitektur dan Modul

## Flutter/Dart

Untuk project Flutter/Dart, gunakan layer wajib:

- **Presentation:** screen/page, widget, dan Provider/BLoC.
- **Domain:** entity/model, usecase, dan interface repository.
- **Data:** implementasi repository, datasource remote/local, DTO, dan mapper.

Alur wajib adalah **UI -> state -> usecase -> repository interface -> datasource**. UI dan state tidak boleh mengakses datasource langsung. Setiap layer bergantung pada layer di bawahnya melalui interface.

- Gunakan `get_it` untuk service, repository, dan usecase. Registrasikan dependency di satu service locator, bukan tersebar.
- Setiap fitur adalah modul mandiri dengan batas yang jelas. Komunikasi antar-modul melalui interface; hindari import langsung implementasi modul lain.
- Interface repository berada di domain; implementasinya di data agar dapat diganti tanpa mengubah domain.
- Satu domain state dimiliki satu Provider atau satu BLoC, tidak keduanya.
- Terapkan lifecycle sesuai aturan Flutter di `flutter-standards.md`.

Sebelum perubahan, petakan arsitektur existing. Terapkan aturan wajib ini pada kode baru dan perubahan yang diminta. Jangan melakukan migrasi besar atau memindahkan kode yang tidak terkait secara diam-diam; jelaskan bukti/dampak dan minta persetujuan untuk perubahan luas.

## Project non-Flutter

Jangan memaksakan struktur Flutter, Provider/BLoC, `get_it`, atau Clean Architecture ke bahasa/framework lain. Ikuti arsitektur yang ada dan gunakan batas modul/interface jika memang menjadi kebutuhan project.

## Keputusan arsitektur

Catat keputusan arsitektur dalam ADR dan dokumentasikan API internal. Setiap modul wajib memiliki README yang menjelaskan tujuan dan cara pakai. Jangan membuat abstraksi atau modul tanpa batas/tanggung jawab yang jelas. Jangan menambah folder di luar struktur wajib tanpa persetujuan pengguna.

## Kolaborasi dan Definition of Done

- Wajib code review sebelum merge. Gunakan branch strategy `feature`, `develop`, dan `main` sesuai alur project.
- Setiap modul memiliki owner yang bertanggung jawab.
- Definition of Done mencakup kode, test, dokumentasi, review, serta pipeline yang lulus.
