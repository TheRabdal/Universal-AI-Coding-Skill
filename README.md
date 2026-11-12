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
- Aturan khusus project, termasuk `rules coding by TheRabdal.txt` bila tersedia, tetap menjadi acuan wajib dan dapat lebih ketat daripada skill universal ini.
- Skill memberi instruksi kepada agent; ia bukan sandbox atau pengunci permission. AI tidak menjalankan project atau build/run lokal; build/run dan quality gate wajib melalui pipeline project.
- Tidak semua AI mendukung Agent Skills. Untuk AI yang hanya menerima system prompt/custom instructions, salin isi `SKILL.md` ke bagian instruksi globalnya.
- Periksa daftar skill yang terdeteksi setelah instalasi tanpa menjalankan project. Pemeriksaan statis dan quality checks yang tidak meluncurkan aplikasi mengikuti aturan project.

## Penyesuaian
Edit `SKILL.md` dan file di `references/` sebagai sumber utama. Salinan pada folder `installers/` dibuat untuk kemudahan instalasi; jika mengubah sumber utama, salin ulang versi terbaru ke adapter yang digunakan. Pastikan seluruh salinan SKILL dan referensi tetap identik dengan sumber kanonis.
