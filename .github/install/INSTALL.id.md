# Cara Menginstal

<details>
<summary><strong>Antigravity (<code>agy</code>)</strong></summary>

### Instalasi

```bash
agy plugin install https://github.com/ayghri/mand
```

### Verifikasi

```bash
agy plugin list
```

### Pembaruan

```bash
agy plugin uninstall mand
agy plugin install https://github.com/ayghri/mand
```

### Uninstal

```bash
agy plugin uninstall mand
```

Atau biarkan terinstal tetapi nonaktifkan: `agy plugin disable mand`.

### Selalu Aktif (opsional)

Tambahkan ke `~/.gemini/GEMINI.md`:

```markdown
## Gaya Respons

Jawab dengan ringkas dan langsung ke tindakan. Susun setiap respons agar mudah ditindaklanjuti:

1. Mulailah dengan jawaban atau langkah selanjutnya: perintah, jalur file, atau cuplikan kode terlebih dahulu.
2. Beri nomor pada pekerjaan yang memiliki beberapa langkah; batasi satu tindakan jelas per langkah.
3. Akhiri dengan satu tindakan selanjutnya yang bisa diselesaikan dalam waktu kurang dari dua menit.
4. Selesaikan masalah saat ini sebelum membahas masalah lain.
5. Tegaskan kembali progres di setiap giliran (misalnya, "langkah 3 dari 5 selesai").
6. Berikan estimasi waktu dalam satuan yang konkret, jangan pernah menggunakan kata seperti "sebentar".
7. Setelah ada perubahan, tunjukkan apa yang sekarang berhasil berfungsi.
8. Error: jelaskan lokasi, penyebab, dan solusinya, tanpa basa-basi.
9. Batasi daftar hanya hingga 5 item.
10. Respond in English, whatever the input or code language.
11. Prefer diagrams over text or code when a diagram can carry the meaning.
12. Tanpa pembukaan, ringkasan ulang, atau salam penutup.
13. Lebih sedikit kata: tanpa kalimat pengisi, tanpa keraguan kosong; frasa pendek tidak masalah.

Pengecualian: jelaskan secara lengkap jika diminta. Konfirmasi sebelum melakukan tindakan yang bersifat destruktif. Setelah tiga kali percobaan perbaikan yang gagal, berhentilah dan identifikasi asumsi yang meragukan. Jika permintaan ambigu, ajukan satu pertanyaan singkat.
```

</details>

<details>
<summary><strong>Claude Code</strong></summary>

### Instalasi

```bash
claude plugin marketplace add ayghri/mand
claude plugin install mand@mand
```

Ketik `/mand`.

### Verifikasi

```bash
claude plugin list
```

### Pembaruan

```bash
claude plugin marketplace update mand
claude plugin update mand@mand
```

### Uninstal

```bash
claude plugin uninstall mand
claude plugin marketplace remove mand
```

Atau biarkan terinstal tetapi nonaktifkan: `claude plugin disable mand`.

### Selalu Aktif (opsional)

Hook `SessionStart` akan memuat semua aturan di awal setiap sesi; Anda tidak perlu lagi mengetik `/mand`:

```bash
touch ~/.claude/.mand-always
```

Jika Anda menggunakan direktori konfigurasi kustom untuk Claude, buat file penanda (flag) di dalamnya:

```bash
touch "$CLAUDE_CONFIG_DIR/.mand-always"
```

Untuk kembali ke mode sesuai permintaan (on-demand):

```bash
rm ~/.claude/.mand-always
```

Hook ini hanya berjalan ketika file penanda ada, jadi menginstal plugin saja tidak akan mengubah apa pun. Perintah "stop mand" tetap akan menonaktifkannya di sesi saat ini.

</details>

<details>
<summary><strong>Codex</strong></summary>

### Instalasi

```bash
codex plugin marketplace add ayghri/mand --ref main
codex plugin add mand@mand
```

Aktifkan skill ini secara eksplisit dengan mengetik `$mand`. Codex ga bakalan memanggilnya secara otomatis.

### Verifikasi

```bash
codex plugin list
```

### Pembaruan

```bash
codex plugin marketplace upgrade mand
codex plugin remove mand
codex plugin add mand@mand
```

### Uninstal

```bash
codex plugin remove mand
codex plugin marketplace remove mand
```

### Selalu Aktif (opsional)

Tambahkan ke `~/.codex/AGENTS.md`:

```markdown
## Gaya Respons

Jawab dengan ringkas dan langsung ke tindakan. Susun setiap respons agar mudah ditindaklanjuti:

1. Mulailah dengan jawaban atau langkah selanjutnya: perintah, jalur file, atau cuplikan kode terlebih dahulu.
2. Beri nomor pada pekerjaan yang memiliki beberapa langkah; batasi satu tindakan jelas per langkah.
3. Akhiri dengan satu tindakan selanjutnya yang bisa diselesaikan dalam waktu kurang dari dua menit.
4. Selesaikan masalah saat ini sebelum membahas masalah lain.
5. Tegaskan kembali progres di setiap giliran (misalnya, "langkah 3 dari 5 selesai").
6. Berikan estimasi waktu dalam satuan yang konkret, jangan pernah menggunakan kata seperti "sebentar".
7. Setelah ada perubahan, tunjukkan apa yang sekarang berhasil berfungsi.
8. Error: jelaskan lokasi, penyebab, dan solusinya, tanpa basa-basi.
9. Batasi daftar hanya hingga 5 item.
10. Respond in English, whatever the input or code language.
11. Prefer diagrams over text or code when a diagram can carry the meaning.
12. Tanpa pembukaan, ringkasan ulang, atau salam penutup.
13. Lebih sedikit kata: tanpa kalimat pengisi, tanpa keraguan kosong; frasa pendek tidak masalah.

Pengecualian: jelaskan secara lengkap jika diminta. Konfirmasi sebelum melakukan tindakan yang bersifat destruktif. Setelah tiga kali percobaan perbaikan yang gagal, berhentilah dan identifikasi asumsi yang meragukan. Jika permintaan ambigu, ajukan satu pertanyaan singkat.
```

</details>

<details>
<summary><strong>Gemini CLI</strong></summary>

Gemini CLI tidak memiliki marketplace plugin, jadi ada dua opsi bawaan: perintah kustom (opt-in, nonaktif sampai dipanggil) atau ekstensi (selalu aktif setelah diinstal). Perintah ini sesuai dengan perilaku bawaan skill ini; pilih ini kecuali Anda ingin aturannya berlaku di semua sesi.

### Instalasi (perintah, opt-in)

```bash
mkdir -p ~/.gemini/commands
curl -fsSL https://raw.githubusercontent.com/ayghri/mand/main/skills/mand/agents/gemini.toml \
  -o ~/.gemini/commands/mand.toml
```

Mulai sesi baru dan ketik `/mand`. Skill ini akan tetap aktif selama sesi tersebut.

### Instalasi (ekstensi, always-on)

```bash
gemini extensions install https://github.com/ayghri/mand
```

Ekstensi ini memuat `GEMINI.md`, yang mengimpor skill secara lengkap; dengan demikian, aturannya berlaku sejak pesan pertama. Git harus sudah terinstal.

### Verifikasi

```bash
gemini extensions list          # via ekstensi
ls ~/.gemini/commands           # rute perintah: mand.toml ada
```

Atau ketik `/` di dalam sesi dan pastikan `mand` muncul dalam daftar.

### Pembaruan

```bash
gemini extensions update mand    # via ekstensi
# via perintah: jalankan ulang perintah curl di atas
```

### Uninstal

```bash
gemini extensions uninstall mand    # via ekstensi
rm ~/.gemini/commands/mand.toml     # rute perintah
```

</details>

<details>
<summary><strong>GitHub Copilot (VS Code dan Copilot CLI)</strong></summary>

Copilot membaca Agent Skills secara native: menggunakan file `SKILL.md` yang sama, tanpa konversi. Di dalam proyek, ia memeriksa `.github/skills/`, `.claude/skills/`, dan `.agents/skills/`; secara global, ia memeriksa `~/.copilot/skills/`, `~/.claude/skills/`, dan `~/.agents/skills/`.

### Instalasi

```bash
npx skills add ayghri/mand -a github-copilot        # proyek ini
npx skills add ayghri/mand -a github-copilot -g     # semua proyek
```

Tanpa CLI, salin folder skill ke direktori mana pun yang diperiksa oleh Copilot:

```bash
git clone https://github.com/ayghri/mand
mkdir -p ~/.copilot/skills
cp -R mand/skills/mand ~/.copilot/skills/
```

### Verifikasi

Ketik `/` di kolom obrolan dan pastikan `mand` muncul. Atau:

```bash
npx skills list
npx skills ls -g    # jika diinstal secara global
```

### Pembaruan

```bash
npx skills update mand
```

Atau salin ulang foldernya setelah `git pull`.

### Uninstal

```bash
npx skills remove mand
```

Atau hapus folder `mand` dari direktori skill tempat ia diinstal.

### Catatan tentang aktivasi

Copilot menghormati `disable-model-invocation`: tidak ada yang diterapkan sampai Anda memanggil skill tersebut, sama seperti di Claude Code (telah diuji pada [#60](https://github.com/ayghri/mand/pull/60)).

### Selalu Aktif (opsional)

Tambahkan blok di bawah ini ke `.github/copilot-instructions.md` pada proyek Anda (Copilot akan membacanya di setiap obrolan):

```markdown
## Gaya Respons

Jawab dengan ringkas dan langsung ke tindakan. Susun setiap respons agar mudah ditindaklanjuti:

1. Mulailah dengan jawaban atau langkah selanjutnya: perintah, jalur file, atau cuplikan kode terlebih dahulu.
2. Beri nomor pada pekerjaan yang memiliki beberapa langkah; batasi satu tindakan jelas per langkah.
3. Akhiri dengan satu tindakan selanjutnya yang bisa diselesaikan dalam waktu kurang dari dua menit.
4. Selesaikan masalah saat ini sebelum membahas masalah lain.
5. Tegaskan kembali progres di setiap giliran (misalnya, "langkah 3 dari 5 selesai").
6. Berikan estimasi waktu dalam satuan yang konkret, jangan pernah menggunakan kata seperti "sebentar".
7. Setelah ada perubahan, tunjukkan apa yang sekarang berhasil berfungsi.
8. Error: jelaskan lokasi, penyebab, dan solusinya, tanpa basa-basi.
9. Batasi daftar hanya hingga 5 item.
10. Respond in English, whatever the input or code language.
11. Prefer diagrams over text or code when a diagram can carry the meaning.
12. Tanpa pembukaan, ringkasan ulang, atau salam penutup.
13. Lebih sedikit kata: tanpa kalimat pengisi, tanpa keraguan kosong; frasa pendek tidak masalah.

Pengecualian: jelaskan secara lengkap jika diminta. Konfirmasi sebelum melakukan tindakan yang bersifat destruktif. Setelah tiga kali percobaan perbaikan yang gagal, berhentilah dan identifikasi asumsi yang meragukan. Jika permintaan ambigu, ajukan satu pertanyaan singkat.
```

</details>

<details>
<summary><strong>Hermes</strong></summary>

### Instalasi

```bash
hermes skills install ayghri/mand/skills/mand
```

Ketik `/mand`. Skill ini akan diinstal ke `~/.hermes/skills/` dan tersedia sebagai perintah slash saat sesi berikutnya dimulai.

Lebih suka menjelajah dulu? Tambahkan repositori ini sebagai sumber skill (sebagai "tap"), lalu cari dan instal:

```bash
hermes skills tap add ayghri/mand
hermes skills search mand
hermes skills install ayghri/mand/skills/mand
```

### Verifikasi

```bash
hermes skills list
```

### Pembaruan

```bash
hermes skills update mand
```

### Uninstal

```bash
hermes skills uninstall mand
```

Atau hapus juga tap-nya: `hermes skills tap remove ayghri/mand`.

### Selalu Aktif (opsional)

Tambahkan ke `AGENTS.md` di direktori kerja Anda (Hermes memuatnya per direktori) atau ke `SOUL.md` pada persona Anda untuk semua sesi:

```markdown
## Gaya Respons

Jawab dengan ringkas dan langsung ke tindakan. Susun setiap respons agar mudah ditindaklanjuti:

1. Mulailah dengan jawaban atau langkah selanjutnya: perintah, jalur file, atau cuplikan kode terlebih dahulu.
2. Beri nomor pada pekerjaan yang memiliki beberapa langkah; batasi satu tindakan jelas per langkah.
3. Akhiri dengan satu tindakan selanjutnya yang bisa diselesaikan dalam waktu kurang dari dua menit.
4. Selesaikan masalah saat ini sebelum membahas masalah lain.
5. Tegaskan kembali progres di setiap giliran (misalnya, "langkah 3 dari 5 selesai").
6. Berikan estimasi waktu dalam satuan yang konkret, jangan pernah menggunakan kata seperti "sebentar".
7. Setelah ada perubahan, tunjukkan apa yang sekarang berhasil berfungsi.
8. Error: jelaskan lokasi, penyebab, dan solusinya, tanpa basa-basi.
9. Batasi daftar hanya hingga 5 item.
10. Respond in English, whatever the input or code language.
11. Prefer diagrams over text or code when a diagram can carry the meaning.
12. Tanpa pembukaan, ringkasan ulang, atau salam penutup.
13. Lebih sedikit kata: tanpa kalimat pengisi, tanpa keraguan kosong; frasa pendek tidak masalah.

Pengecualian: jelaskan secara lengkap jika diminta. Konfirmasi sebelum melakukan tindakan yang bersifat destruktif. Setelah tiga kali percobaan perbaikan yang gagal, berhentilah dan identifikasi asumsi yang meragukan. Jika permintaan ambigu, ajukan satu pertanyaan singkat.
```

</details>

<details>
<summary><strong>Kimi Code CLI</strong></summary>

### Instalasi

Mulai sesi Kimi Code dan:

1. Jalankan `/plugins`.
2. Pilih **Custom**.
3. Tempel `https://github.com/ayghri/mand` dan tekan Enter.
4. Pilih **Trust and install**.

Gunakan perintah slash `/skill:mand` untuk memanggil skill ini secara eksplisit.

### Pembaruan

Di dalam sesi Kimi Code, jalankan `/plugins`, arahkan kursor ke **mand**, dan tekan `R`.

### Uninstal

Di dalam sesi Kimi Code, jalankan `/plugins`, arahkan kursor ke **mand**, dan tekan `D`.

</details>

<details>
<summary><strong>OpenCode</strong></summary>

Plugin mendukung OpenCode V1 **1.18.29 atau lebih baru** dan V2. Plugin mendaftarkan skill dan perintah `/mand`, serta menyediakan mode selalu aktif opsional. Versi V1 yang lebih lama perlu diperbarui atau menggunakan plugin dari rilis skill sebelumnya.

### Instalasi

Untuk digunakan di semua proyek:

```bash
git clone https://github.com/ayghri/mand ~/.config/opencode/vendor/mand
mkdir -p ~/.config/opencode/plugins
cat > ~/.config/opencode/plugins/mand.js <<'EOF'
export { default } from '../vendor/mand/.opencode/plugins/mand.mjs';
EOF
```

Untuk instalasi V1 yang sudah ada, pertahankan entri `plugin` di `opencode.json`. Jika beralih ke pemuat di atas, hapus entri tersebut.

Mulai sesi baru dan ketik `/mand`. Aturan berlaku hingga Anda mengatakan `stop mand` atau `normal mode`.

#### Hanya skill dan perintah (tanpa mode selalu aktif)

Sebagai alternatif, salin skill dan perintah dari repositori ke direktori global OpenCode:

```bash
mkdir -p ~/.config/opencode/skills/mand ~/.config/opencode/commands
cp skills/mand/SKILL.md ~/.config/opencode/skills/mand/SKILL.md
cp .opencode/command/mand.md ~/.config/opencode/commands/mand.md
```

### Verifikasi

Jalankan OpenCode, ketik `/`, dan pastikan `mand` muncul dalam daftar perintah.

### Pembaruan

```bash
git -C ~/.config/opencode/vendor/mand pull
```

Untuk instalasi dengan menyalin, perbarui repositori lalu salin kembali kedua file.

### Uninstal

Hapus `~/.config/opencode/plugins/mand.js`. Untuk instalasi dengan menyalin, hapus `~/.config/opencode/skills/mand/` dan `~/.config/opencode/commands/mand.md`. Untuk instalasi V1 dengan konfigurasi yang sudah ada, hapus entri `plugin` terkait.

### Selalu Aktif (opsional)

Memerlukan plugin. Membuat file penanda menambahkan seluruh aturan ke prompt sistem pada setiap giliran:

```bash
touch ~/.config/opencode/.mand-always
```

`stop mand` atau `normal mode` meminta agen kembali ke gaya respons biasa untuk sesi saat ini. Hapus file penanda untuk menghentikan penyisipan otomatis:

```bash
rm ~/.config/opencode/.mand-always
```

Jika `XDG_CONFIG_HOME` diatur, ganti `~/.config` dalam jalur ini dengan direktori tersebut.

</details>

<details>
<summary><strong>Pi</strong></summary>

Pi mengimplementasikan standar Agent Skills, sehingga file `SKILL.md` yang sama dimuat langsung tanpa konversi. Cara pemanggilan di Pi sedikit berbeda: skill dipanggil dengan format `/skill:<nama>`.

### Instalasi

```bash
npx skills add ayghri/mand -a pi -y
```

Lebih suka menggunakan sistem file? Pi menemukan skill di `~/.pi/agent/skills/` dan `~/.agents/skills/` (global), serta di `.pi/skills/` dan `.agents/skills/` (proyek):

```bash
git clone https://github.com/ayghri/mand
mkdir -p ~/.pi/agent/skills
cp -R mand/skills/mand ~/.pi/agent/skills/
```

Aktifkan perintah slash untuk skill di `settings.json` Pi:

```json
{ "enableSkillCommands": true }
```

Mulai sesi baru dan ketik `/skill:mand`.

### Verifikasi

```bash
npx skills list
```

Atau ketik `/skill:` di dalam sesi dan pastikan `mand` muncul dalam daftar.

### Pembaruan

```bash
npx skills update mand
```

Atau salin ulang foldernya setelah `git pull`.

### Uninstal

```bash
npx skills remove mand
```

Atau hapus `~/.pi/agent/skills/mand`.

### Selalu Aktif (opsional)

Tambahkan ke `AGENTS.md` pada proyek Anda:

```markdown
## Gaya Respons

Jawab dengan ringkas dan langsung ke tindakan. Susun setiap respons agar mudah ditindaklanjuti:

1. Mulailah dengan jawaban atau langkah selanjutnya: perintah, jalur file, atau cuplikan kode terlebih dahulu.
2. Beri nomor pada pekerjaan yang memiliki beberapa langkah; batasi satu tindakan jelas per langkah.
3. Akhiri dengan satu tindakan selanjutnya yang bisa diselesaikan dalam waktu kurang dari dua menit.
4. Selesaikan masalah saat ini sebelum membahas masalah lain.
5. Tegaskan kembali progres di setiap giliran (misalnya, "langkah 3 dari 5 selesai").
6. Berikan estimasi waktu dalam satuan yang konkret, jangan pernah menggunakan kata seperti "sebentar".
7. Setelah ada perubahan, tunjukkan apa yang sekarang berhasil berfungsi.
8. Error: jelaskan lokasi, penyebab, dan solusinya, tanpa basa-basi.
9. Batasi daftar hanya hingga 5 item.
10. Respond in English, whatever the input or code language.
11. Prefer diagrams over text or code when a diagram can carry the meaning.
12. Tanpa pembukaan, ringkasan ulang, atau salam penutup.
13. Lebih sedikit kata: tanpa kalimat pengisi, tanpa keraguan kosong; frasa pendek tidak masalah.

Pengecualian: jelaskan secara lengkap jika diminta. Konfirmasi sebelum melakukan tindakan yang bersifat destruktif. Setelah tiga kali percobaan perbaikan yang gagal, berhentilah dan identifikasi asumsi yang meragukan. Jika permintaan ambigu, ajukan satu pertanyaan singkat.
```

</details>

<details>
<summary><strong>Qwen Code</strong></summary>

### Instalasi

```bash
qwen extensions install ayghri/mand
```

Qwen Code menerima format singkat GitHub dan menginstal repositori sebagai ekstensi native. Ekstensi ini akan menemukan skill di dalam `skills/`.

Ketik `/mand` untuk memanggil skill ini secara eksplisit. Menginstal ekstensi gak bakal mengubah keluaran sampai skill tersebut dipanggil.

### Verifikasi

```bash
qwen extensions list
```

Selanjutnya, mulai sesi baru Qwen Code dan jalankan:

```text
/skills
```

Pastikan `mand` muncul dalam daftar.

### Pembaruan

```bash
qwen extensions update mand
```

### Uninstal

```bash
qwen extensions uninstall mand
```

</details>

<details>
<summary><strong>Zed</strong></summary>

Zed Agent membaca Agent Skills secara native: menggunakan file `SKILL.md` yang sama, tanpa konversi. ("Rules" lama di Zed telah digantikan oleh Skills dan instruksi di `AGENTS.md`.)

### Instalasi

Di Agent Panel, buka pengelola Skills, pilih **Create skill from URL** (juga tersedia di palet sebagai `agent: create skill from url`) dan tempel:

```
https://github.com/ayghri/mand/blob/main/skills/mand/SKILL.md
```

Simpan dengan cakupan **User** untuk semua proyek, atau **Project** untuk satu proyek tertentu. Setelah itu, ketik `/mand` di Agent Panel.

Lebih suka menggunakan sistem file? Klon repositori dan letakkan folder skill di direktori skill pengguna:

```bash
git clone https://github.com/ayghri/mand
mkdir -p ~/.agents/skills
cp -R mand/skills/mand ~/.agents/skills/
```

### Verifikasi

Buka pengelola Skills di Agent Panel dan pastikan `mand` muncul. Atau ketik `/` dan periksa.

### Pembaruan

Impor ulang menggunakan URL yang sama (akan menimpa) atau salin ulang foldernya setelah `git pull`.

### Uninstal

Hapus `mand` dari pengelola Skills atau hapus folder `~/.agents/skills/mand`.

### Selalu Aktif (opsional)

Tambahkan ke file `~/.config/zed/AGENTS.md` pribadi Anda:

```markdown
## Gaya Respons

Jawab dengan ringkas dan langsung ke tindakan. Susun setiap respons agar mudah ditindaklanjuti:

1. Mulailah dengan jawaban atau langkah selanjutnya: perintah, jalur file, atau cuplikan kode terlebih dahulu.
2. Beri nomor pada pekerjaan yang memiliki beberapa langkah; batasi satu tindakan jelas per langkah.
3. Akhiri dengan satu tindakan selanjutnya yang bisa diselesaikan dalam waktu kurang dari dua menit.
4. Selesaikan masalah saat ini sebelum membahas masalah lain.
5. Tegaskan kembali progres di setiap giliran (misalnya, "langkah 3 dari 5 selesai").
6. Berikan estimasi waktu dalam satuan yang konkret, jangan pernah menggunakan kata seperti "sebentar".
7. Setelah ada perubahan, tunjukkan apa yang sekarang berhasil berfungsi.
8. Error: jelaskan lokasi, penyebab, dan solusinya, tanpa basa-basi.
9. Batasi daftar hanya hingga 5 item.
10. Respond in English, whatever the input or code language.
11. Prefer diagrams over text or code when a diagram can carry the meaning.
12. Tanpa pembukaan, ringkasan ulang, atau salam penutup.
13. Lebih sedikit kata: tanpa kalimat pengisi, tanpa keraguan kosong; frasa pendek tidak masalah.

Pengecualian: jelaskan secara lengkap jika diminta. Konfirmasi sebelum melakukan tindakan yang bersifat destruktif. Setelah tiga kali percobaan perbaikan yang gagal, berhentilah dan identifikasi asumsi yang meragukan. Jika permintaan ambigu, ajukan satu pertanyaan singkat.
```

</details>

<details>
<summary><strong>Cursor, Amp, dan lingkungan lain yang kompatibel dengan agent-skills</strong></summary>

Berfungsi di lingkungan apa pun yang mendukung pembacaan Agent Skills. Ganti `-a <agent>` dengan agen pilihan Anda.

### Instalasi

```bash
npx skills add ayghri/mand                  # workspace ini
npx skills add ayghri/mand -g               # semua proyek
npx skills add ayghri/mand -a cursor -y     # satu agen saja
npx skills add ayghri/mand -a opencode -y
```

Buka obrolan agen baru dan ketik `/mand`.

Tanpa CLI, salin folder skill ke jalur yang diperiksa oleh agen Anda:

```bash
git clone https://github.com/ayghri/mand
mkdir -p ~/.cursor/skills     # Cursor. Gunakan .agents/skills di OpenCode atau jalur khusus agen Anda
cp -R mand/skills/mand ~/.cursor/skills/
```

### Verifikasi

```bash
npx skills list
npx skills ls -g    # jika diinstal secara global
```

### Pembaruan

```bash
npx skills update mand
npx skills update -g    # jika diinstal secara global
```

### Uninstal

```bash
npx skills remove mand
npx skills remove mand -g    # jika diinstal secara global
```

### Selalu Aktif (opsional)

Tempel ini ke file aturan agen yang persisten. Cursor: **Settings → Rules → User Rules**, atau aturan proyek di `.cursor/rules/` dengan `alwaysApply: true`. OpenCode: `~/.config/opencode/AGENTS.md`.

```markdown
## Gaya Respons

Jawab dengan ringkas dan langsung ke tindakan. Susun setiap respons agar mudah ditindaklanjuti:

1. Mulailah dengan jawaban atau langkah selanjutnya: perintah, jalur file, atau cuplikan kode terlebih dahulu.
2. Beri nomor pada pekerjaan yang memiliki beberapa langkah; batasi satu tindakan jelas per langkah.
3. Akhiri dengan satu tindakan selanjutnya yang bisa diselesaikan dalam waktu kurang dari dua menit.
4. Selesaikan masalah saat ini sebelum membahas masalah lain.
5. Tegaskan kembali progres di setiap giliran (misalnya, "langkah 3 dari 5 selesai").
6. Berikan estimasi waktu dalam satuan yang konkret, jangan pernah menggunakan kata seperti "sebentar".
7. Setelah ada perubahan, tunjukkan apa yang sekarang berhasil berfungsi.
8. Error: jelaskan lokasi, penyebab, dan solusinya, tanpa basa-basi.
9. Batasi daftar hanya hingga 5 item.
10. Respond in English, whatever the input or code language.
11. Prefer diagrams over text or code when a diagram can carry the meaning.
12. Tanpa pembukaan, ringkasan ulang, atau salam penutup.
13. Lebih sedikit kata: tanpa kalimat pengisi, tanpa keraguan kosong; frasa pendek tidak masalah.

Pengecualian: jelaskan secara lengkap jika diminta. Konfirmasi sebelum melakukan tindakan yang bersifat destruktif. Setelah tiga kali percobaan perbaikan yang gagal, berhentilah dan identifikasi asumsi yang meragukan. Jika permintaan ambigu, ajukan satu pertanyaan singkat.
```
</details>


## Cara Kerja Aktivasi

1. **Terinstal, tetapi tidak dipanggil.** Di Claude Code, Qwen Code, dan Codex, tidak ada yang terjadi sampai Anda memanggil skill ini secara eksplisit. Claude Code dan Qwen Code menghormati `disable-model-invocation: true` di `SKILL.md`; Codex menghormati `policy.allow_implicit_invocation: false` di `agents/openai.yaml`. Lingkungan lain mungkin memuat deskripsi setiap skill saat startup dan mengaktifkannya sendiri.
2. **Anda memanggilnya secara eksplisit.** Ketik `/mand` di Claude Code atau Qwen Code, atau `$mand` di Codex. Aturan ini bakalan aktif di sesi tersebut. Perintah "stop mand" atau "normal mode" bakal menonaktifkannya.
3. **Anda membuat `~/.claude/.mand-always`** (Claude Code). Hook `SessionStart` bakalan memuat (load) semua aturan sejak pesan pertama, di setiap sesi.
4. **Anda menambahkan cuplikan "selalu aktif" di atas** (lingkungan lain). Ini akan menjaga aturan utama tetap berada dalam konteks agen yang persisten.

Di Claude Code, Qwen Code, dan Codex gak ada jalan tengah: jikalau Anda tidak mengaktifkannya, maka skill ini nonaktif.

## Pemecahan Masalah (Troubleshooting)

**`/mand` tidak muncul di pelengkapan otomatis (autocomplete).** Mulai ulang agen Anda. Indeks plugin dibaca saat startup.

**Flag selalu aktif tidak berfungsi.** Perbarui plugin (`claude plugin marketplace update mand`, lalu `claude plugin update mand@mand`) dan mulai ulang. Hook dibaca saat startup, dan flag ini memerlukan versi yang menyertakan `hooks/hooks.json`.

**`claude plugin marketplace add` gagal.** Gunakan format `owner/repo`. Jalur lokal harus mengarah ke root repositori, bukan ke `.claude-plugin/`.

**Sudah diinstal, tetapi respons masih memiliki pembukaan (preambulo).** Buka sesi baru. Jika masih terus menyimpang, pertegas teks di `skills/mand/SKILL.md`.

**Ingin peraturan yang berbeda?.** Lakukan fork skill ini, edit `skills/mand/SKILL.md` sesuai keinginan, lalu ganti dengan salinan Anda sendiri:

```bash
claude plugin uninstall mand            # hapus dulu salinan upstream:
claude plugin marketplace remove mand   # fork dan upstream menggunakan nama yang sama
claude plugin marketplace add <username-anda>/mand
claude plugin install mand@mand
```

Mulai ulang dan panggillah `/mand` lagi.

**Skill tidak muncul setelah `npx skills add`.** Buka obrolan agen baru. Skill diindeks di awal sesi. Pastikan folder telah diinstal di lokasi yang dicari oleh agen (`~/.cursor/skills/` di Cursor, `.agents/skills/` di OpenCode) dan bahwa `name` di frontmatter sesuai dengan nama folder.
