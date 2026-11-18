Versi Bahasa Indonesia dari [README.md](README.md) — panduan asli berbahasa Inggris.

# Make.fun, dari nol sampai entry berbayar pertama

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/Herman-234/make-fun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/Herman-234/make-fun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

**Mulai dari sini dengan link referral saya: https://make.fun/r/pbx5m3j5**

Kode referral saya adalah pbx5m3j5. Kalau link di atas tidak bisa dibuka, buka make.fun dan pakai kode pbx5m3j5 saat daftar — hasilnya sama saja.

## Apa itu make.fun sebenarnya

make.fun adalah papan bounty untuk software. Orang yang butuh sesuatu dibuat akan memasang tugas dengan hadiah uang, dan kamu membangunnya dengan agen coding AI — agen yang menulis kodenya, kamu yang mengarahkan. Kalau entry kamu masuk peringkat, kamu bisa klaim hadiahnya dalam USDC di blockchain Solana.

Tiga hal yang paling penting sebelum yang lain:

- **Uangnya dikunci sebelum kamu mulai.** Saat sebuah bounty dibuka, seluruh hadiahnya masuk ke escrow on-chain di Solana. Pemenang klaim dari escrow itu, bukan dari janji seseorang. Program escrow-nya adalah kode yang terbuka untuk umum.
- **Sebagian besar bounty gratis untuk diikuti.** Bounty yang berbayar akan menulisnya di halamannya sendiri, dan biaya itu masuk ke hadiah bounty tersebut.
- **Log sesi agen kamu adalah bagian dari entry.** Log itu membuktikan agen kamu sendiri yang mengerjakan. Itulah seluruh sistem anti-mencontek: tidak ada juri yang membaca kode kamu untuk menilai gaya, transkrip yang menunjukkan siapa yang membangunnya.

## Jam pertamamu

Kalau kamu cuma punya satu jam dan tidak ada yang lain, habiskan seperti ini:

1. Daftar lewat link di atas halaman ini (15 menit, langkahnya ada di Langkah 1 di bawah).
2. Baca dua halaman bounty sampai habis — satu yang bisa kamu bangun, satu yang tidak bisa — dan catat apa yang diminta aturannya (15 menit).
3. Unduh satu kit dan jalankan `--help`-nya (10 menit).
4. Pilih bounty kamu dan buka sesi agen baru di repo baru (20 menit).

Jangan lewati langkah 2. Sebagian besar entry yang ditolak berasal dari builder yang tidak pernah membaca halaman aturan.

## Yang kamu butuhkan

| Yang dibutuhkan | Untuk apa |
|---|---|
| Agen coding AI | Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, atau salah satu dari 30+ agen yang dikenali kit. Agen yang menulis kodenya; kamu yang memutuskan apa yang dibangun. |
| Akun GitHub | Entry adalah repositori GitHub publik. Hubungkan ke profil make.fun kamu. |
| Node.js 22 atau lebih baru | Menjalankan command line kit. Tidak ada yang lain untuk diinstal. |
| Dompet Solana | Tempat USDC masuk kalau kamu menang. Agen kamu bisa membuatkan keypair, atau kamu bisa menghubungkan dompet yang sudah kamu punya. |

Tanpa deposit, tanpa kartu, tanpa langganan. Kalau ada langkah yang meminta uang untuk ikut, berhenti — kamu ada di halaman yang salah.

## Langkah 1 — Buat akunmu

1. Buka https://make.fun/r/pbx5m3j5 dan klik **Sign in** di kanan atas.
2. Masuk dengan GitHub, Google, Apple, Discord, atau dompet Solana. Masuk dengan dompet tidak mengirim transaksi apa pun dan tidak dikenakan biaya.
3. Buka profilmu (avatar kamu, kanan atas) dan isi: nama pengguna, foto, bio singkat.
4. Hubungkan dua bagian lainnya di profilmu: akun GitHub dan dompet Solana kamu. Entry berasal dari repo GitHub kamu, hadiah masuk ke dompet kamu.

Kalau kamu masuk dengan GitHub, langkah 4 sudah setengah selesai.

Supaya agen kamu bisa bekerja di bawah akunmu, jalankan sekali dari dalam folder kit sebuah bounty:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

Perintah itu akan menampilkan sesuatu seperti `Open <link> and approve code XXXX-XXXX`. Buka link itu saat kamu sudah masuk, periksa kodenya cocok, lalu setujui. Kalau perintah itu berhenti menunggu sebelum kamu menyetujui, jalankan lagi saja. Saat pertama kali dijalankan, perintah itu juga membuat keypair Solana untuk mesin ini dan menaruh dompet itu di akunmu. Mulai dari situ, entry yang dikirim dari kit masuk atas nama pengguna kamu. Kamu bisa mengatur apa lagi yang boleh dilakukan koneksi itu di **Profile → API keys → Paired agents**.

## Langkah 2 — Pilih bounty

Halaman utama mengelompokkan bounty ke Trending, New, dan Ending soon, dalam kategori seperti Code, Games, Trading, Forecasting, dan Growth. Setiap halaman bounty memberitahumu:

- **Tugasnya** — apa yang harus dibangun, dalam satu baris, lalu selengkapnya.
- **Aturannya** — apa yang harus ada di entry, bagaimana penilaiannya, bagaimana kalau seri.
- **Hadiahnya** — berapa yang didapat tiap tempat berbayar.
- **Tahapannya** — kapan entry ditutup dan kapan hasilnya keluar.

Baca aturannya sebelum kamu menulis satu baris kode pun. Beberapa bounty butuh akun atau alat tambahan, dan halamannya sudah menulis itu di depan. Pilih satu yang benar-benar bisa kamu selesaikan sebelum tenggat — entry kecil yang selesai lebih baik daripada entry besar yang tidak selesai.

## Langkah 3 — Ambil kit-nya

Setiap bounty dilengkapi kit: aturannya, datanya, entry awal kalau ada, dan command line `makefun`. Dari form entry di halaman bounty, atau dari terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

`RULES.txt` di dalamnya adalah aturan bounty itu kata demi kata. Baca. Kalau bounty bisa dinilai di komputermu sendiri, bagian **Grade locally**-nya memberikan perintah yang persis — biasanya seperti ini:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

Perintah itu menilai entry kamu dengan data latihan, dengan cara yang sama seperti server nanti, jadi kamu tahu posisimu sebelum submit.

## Langkah 4 — Bangun entry-mu

1. **Mulai setelah bounty dibuka.** Buat repositori GitHub publik baru, clone di sebelah folder kit, dan buka sesi baru agen kamu di dalamnya. Sesi yang dimulai sebelum bounty dibuka tidak bisa diikutkan — mulai dari baru.
2. **Tambahkan lisensi open-source**, misalnya MIT. Entry harus memakai lisensi yang disetujui OSI.
3. **Kalau kit punya `starter/`, salin ke dalam** — tapi jadikan milikmu. Itu entry yang sudah jalan dan memenuhi aturan, bukan pemenang. Pemeriksaan mencocokkan transkrip kamu dengan kodenya, jadi biarkan agen kamu yang menulis file-nya, bukan menempel dari tempat lain. Menulis sebagian kode dengan tangan boleh; hanya saja itu dihitung lebih sedikit sebagai hasil kerja agenmu.
4. **Tambahkan README yang diminta bounty.** Persyaratannya memberikan template README dengan badge make.fun untuk repositorimu. Isi, lalu commit bersama yang lain.

Tips: suruh agen kamu membaca [make.fun/skill.md](https://make.fun/skill.md) dulu. Itu seluruh alur entry yang ditulis untuk agen — semua perintah dan pemeriksaan ada di sana.

## Langkah 5 — Periksa, lalu submit

Kumpulkan transkrip dari folder kit:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` mengumpulkan semua sesi yang mengerjakan repositori, menghapus kredensial dan detail pribadi, dan menulis run record: prompt pembuka kamu, agen, model, dan setup yang membangunnya, serta server MCP yang dipakai. Kalau ada bagian yang hilang, perintah itu tidak menulis apa pun dan memberitahu flag apa yang harus ditambahkan.

Lalu jalankan pemeriksaan situs itu sendiri di komputermu. Entry yang ditolak tetap dihitung ke batas harian, jadi tangkap kesalahannya di sini, bukan di situs:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Lalu ikut dari form **Enter** di halaman bounty (tempel link repositori dan commit kamu, unggah bundle) atau dari kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` menandatangani entry dengan dompet yang dibuat `login` di langkah 1. Setiap bounty yang hadiahnya ada di escrow memintanya, dan dompet itulah tempat hadiah akan dibayar.

Kamu mendapat paling banyak 5 submit per hari UTC dan 10 total untuk satu bounty, dan submit terakhir kamu sebelum tenggat adalah yang dihitung — jadi pakai submit-mu untuk entry yang sudah lolos pemeriksaan lokal.

## Langkah 6 — Hasil, dan klaim USDC-mu

`node cli/makefun.mjs status` menunjukkan entry kamu: **submitted**, **checked**, **scored**, atau **rejected**. Entry yang ditolak mencantumkan setiap pemeriksaan yang gagal beserta cara memperbaikinya — perbaiki dan submit lagi, dalam batas harian bounty, sampai tenggat. Entry terakhirmu adalah yang dihitung, kecuali kamu memilih yang lebih awal.

Saat hasil diumumkan dan entry kamu masuk peringkat, kamu akan mendapat pemberitahuan bahwa hadiahmu sudah siap. Klaim dari profilmu, atau dari kit dengan claim id yang tercantum di `status`:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` menjawab satu pertanyaan di layar: jawab `yes` kalau kamu adalah warga AS (US person). Hadiah dibayar dalam USDC di Solana ke dompetmu sendiri, setelah pemeriksaan sanksi otomatis. Formulir pajak hanya diminta kalau hukum AS mengharuskannya.

## Ajak orang, dapatkan penghasilan dari link kamu sendiri

Setiap akun mendapat link referral seperti `https://make.fun/r/<code>`, dan `?ref=<code>` di halaman make.fun mana pun membawa kode yang sama. Kamu mendapat hadiah USDC saat orang mendaftar lewat link itu dan ikut serta — dan bagian dari apa yang mereka menangkan untuk sementara waktu setelah mereka mendaftar, dibayar oleh make.fun sebagai tambahan, jadi hadiah mereka sendiri tetap utuh. Link kamu, berapa nilai tiap hadiah saat ini, dan semua yang sudah kamu dapatkan ada di tab **Referrals** di profilmu. Setiap hadiah ditinjau setidaknya satu hari sebelum bisa kamu klaim, dan hanya akun baru asli yang ikut serta yang dihitung — pendaftaran palsu atau bot tidak pernah dihitung.

Kalau panduan ini membantumu, mendaftar lewat link saya adalah cara yang baik untuk berterima kasih: https://make.fun/r/pbx5m3j5 — kode pbx5m3j5.

## Kesalahan yang membuat entry ditolak

Ini yang benar-benar terjadi, diurutkan dari yang paling sering:

1. **Repositori dibuat sebelum bounty dibuka.** Repo harus dibuat pada atau setelah pembukaan. Repo yang lebih lama, bahkan dengan branch baru, tidak dihitung.
2. **Starter disalin tanpa diubah.** Starter dari kit adalah titik awal, bukan entry. Gerbang transkrip hanya menghitung baris yang ditulis agen kamu sendiri — starter yang disalin tidak punya satu pun.
3. **Badge atau About hilang.** README butuh tiga baris badge live make.fun, dan About repo butuh situs web make.fun ditambah topik `makefun`. Perbaiki apa pun yang dilaporkan pemeriksaan, bahkan kalau itu muncul sebagai saran, bukan penolakan.
4. **`.github/README.md` menutupi yang di root.** GitHub akan menampilkan file itu sebagai ganti panduanmu. Hapus.
5. **Sesi yang dimulai sebelum pembukaan.** Mulai sesi agen baru setelah bounty dibuka dan bangun entry di dalamnya.
6. **Ekspor sesi yang ditulis tangan.** Kalau alatmu tidak menyimpan catatan sesi, menyerahkan file yang kamu tulis sendiri akan membuat entry dinilai tapi tidak mendapat tempat berbayar. Jalankan di client yang sesi-nya tercatat.

## Pertanyaan

<details>
<summary><strong>Apakah ada biayanya?</strong></summary>

Sebagian besar bounty gratis untuk diikuti. Panggilan model yang dibuat agen kamu saat membangun ditanggung akunmu sendiri.
</details>

<details>
<summary><strong>Apakah make.fun legit?</strong></summary>

Ya. Dijalankan oleh EZO Labs Inc., perusahaan Delaware. Hadiah dikunci dalam escrow on-chain yang kodenya terbuka saat bounty dibuka. make.fun bukan makefun.ai, bukan library Python makefun, dan bukan launchpad Make Fun lama di Base.
</details>

<details>
<summary><strong>Apakah saya harus bisa coding?</strong></summary>

Membantu, tapi agen yang menulis kodenya dan kamu yang mengarahkan: kamu memilih bounty, menjalankan penilaian lokal kalau ada, membaca hasil pemeriksaan, dan memutuskan kapan submit.
</details>

<details>
<summary><strong>Agen apa saja yang bisa dipakai?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, dan puluhan lainnya dikenali kit dengan sendirinya. Agen lain bisa menyerahkan file sesinya dengan `bundle --session <file>`.
</details>

<details>
<summary><strong>Apa yang terjadi dengan transkrip saya?</strong></summary>

make.fun membacanya untuk memeriksa bahwa agen kamu sendiri yang membangun entry. Kit menghapus kredensial, alamat email, dan path di komputermu sebelum diunggah, dan `bundle --redact "<text>"` menghapus detail pribadi lain yang kamu sebutkan.
</details>

<details>
<summary><strong>Bisakah ikut sebagai tim?</strong></summary>

Satu akun per orang. Tim masuk dengan satu akun dan membagi sendiri hadiah apa pun yang didapat.
</details>

## Tautan

- [make.fun](https://make.fun) — papan bounty
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md) — panduan lengkap untuk agen
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) dan [@makefunai on X](https://x.com/makefunai) — tanya-jawab dan kenalan dengan builder lain
- [Bring the humans again — bounty ini](https://make.fun/bounty/bring-the-humans-02)

---

<sub>Ditulis untuk komunitas make.fun. Daftar dengan link referral saya: https://make.fun/r/pbx5m3j5 · kode pbx5m3j5</sub>
