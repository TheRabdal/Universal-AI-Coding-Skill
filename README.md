# Universal AI Coding Skill

Skill lintas bahasa dengan standar khusus Flutter/Dart, existing-architecture-first, anti-slop, security review, dan Strict Execution Mode.

## Isi paket
- `SKILL.md`: instruksi utama Agent Skills.
- `references/`: modul aturan tambahan.
- `installers/`: salinan siap ditempatkan untuk beberapa coding agent.
- `templates/packages.dart`: contoh opsional untuk project Flutter; jangan menimpa file project yang sudah ada.

## Instalasi cepat

### Codex
Salin folder `installers/codex/.agents/skills/universal-ai-coding/` ke root project, atau salin folder `universal-ai-coding` ke `~/.agents/skills/` untuk penggunaan personal.

### Claude Code
Salin `installers/claude/.claude/skills/universal-ai-coding/` ke root project, atau ke `~/.claude/skills/` untuk penggunaan personal.

### Cursor
Salin `installers/cursor/.cursor/skills/universal-ai-coding/` ke root project, atau ke `~/.cursor/skills/` untuk penggunaan personal.

### OpenCode
Salin `installers/opencode/.opencode/skills/universal-ai-coding/` ke root project, atau ke `~/.config/opencode/skills/` untuk penggunaan personal.

### Gemini CLI
Salin `installers/gemini/.gemini/skills/universal-ai-coding/` ke root project, atau ke `~/.gemini/skills/` untuk penggunaan personal.

### VS Code / GitHub Copilot
Salin `installers/vscode/.github/skills/universal-ai-coding/` ke root project.

## Instalasi lintas agent

Untuk project yang memakai banyak agent, gunakan folder `.agents/skills/universal-ai-coding/` sebagai lokasi bersama jika agent yang digunakan mendukungnya. Claude Code dan beberapa agent lain memerlukan lokasi khusus masing-masing; gunakan adapter yang disediakan.

## Penting
- Tidak ada script installer yang otomatis menjalankan perintah.
- Instalasi dilakukan dengan menyalin folder skill ke lokasi yang sesuai.
- Jangan menimpa skill atau aturan yang sudah ada tanpa meninjau diff.
- Skill memberi instruksi kepada agent; ia bukan sandbox atau pengunci permission. Untuk Strict Mode yang benar-benar enforced, tetap gunakan permission/approval controls pada coding agent dan sistem operasi.
- Tidak semua AI mendukung Agent Skills. Untuk AI yang hanya menerima system prompt/custom instructions, salin isi `SKILL.md` ke bagian instruksi globalnya.
- Periksa daftar skill yang terdeteksi oleh agent setelah instalasi dan lakukan uji kecil yang tidak memerlukan eksekusi project.

## Penyesuaian
Edit `SKILL.md` dan file di `references/` sebagai sumber utama. Salinan pada folder `installers/` dibuat untuk kemudahan instalasi; jika mengubah sumber utama, salin ulang versi terbaru ke adapter yang digunakan.
