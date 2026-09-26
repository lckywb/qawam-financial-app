# WORKFLOW PENGEMBANGAN APLIKASI QAWĀM
## KTIQ OASE PTKIN III 2026

Versi: 1.0
Status: Workflow resmi pengembangan prototype

---

# 1. TUJUAN WORKFLOW

Workflow ini digunakan agar pengembangan aplikasi QAWĀM berjalan bertahap, aman, mudah dipantau, dan tidak membuat project rusak karena terlalu banyak perubahan sekaligus.

Prinsip utama:

> Qur'an → Tafsir → Qawām Framework → Data → Decision Engine → UI → Prototype → Testing

Aplikasi bukan sekadar aplikasi pencatatan keuangan. Fungsi pembeda utamanya adalah membantu pengguna mempertimbangkan keputusan pengeluaran berdasarkan kondisi finansialnya.

---

# 2. ATURAN KERJA UTAMA

1. Jangan mengubah banyak file sekaligus tanpa alasan.
2. Satu fitur besar dikerjakan dalam satu fase.
3. Setelah satu fase selesai, aplikasi harus dijalankan dan diuji.
4. Setelah berhasil, lakukan commit ke GitHub.
5. Jangan menghapus file yang sudah berfungsi sebelum ada pengganti yang sudah diuji.
6. Jangan mengubah Qawām Decision Framework hanya karena UI membutuhkan perubahan.
7. Jika ada error, perbaiki error terlebih dahulu sebelum menambah fitur.
8. Setiap perubahan harus dapat dijelaskan hubungannya dengan fungsi aplikasi.
9. Jangan membuat Qawām Score 0–100.
10. Aplikasi bukan mesin fatwa; hasilnya adalah pendamping keputusan.

---

# 3. STRUKTUR GITHUB

Repository:

qawam-financial-app

Struktur target:

qawam-financial-app/
├── app/
├── .github/
│   └── workflows/
│       └── build.yml
├── build.gradle
├── settings.gradle
├── gradle.properties
├── README.md
└── WORKFLOW_QAWAM.md

---

# 4. ARSITEKTUR APLIKASI

Alur besar:

ONBOARDING
    ↓
FINANCIAL PROFILE
    ↓
FINANCIAL INVENTORY
    ↓
DEBT REGISTER
    ↓
HOME DASHBOARD
    ↓
SAYA MAU MEMBELI...
    ↓
NEED + PURPOSE
    ↓
QAWĀM DECISION CHECK
    ↓
CONDITION
    ↓
PROPORTIONALITY
    ↓
FINANCIAL CONTINUITY
    ↓
RISK RECOGNITION
    ↓
DECISION RESULT
    ↓
DECISION HISTORY

---

# 5. MODUL APLIKASI

## Modul 01 — Splash / Welcome

Tujuan:
- memperkenalkan QAWĀM;
- memperkenalkan prinsip utama;
- memberikan akses masuk.

Konten:
- nama QAWĀM;
- tagline;
- QS al-Furqān [25]:67;
- tombol Mulai.

Status:
- Sudah ada pada V2.

---

## Modul 02 — Onboarding

Tujuan:
membangun konteks finansial pengguna.

Data:
- nama;
- pemasukan rata-rata;
- uang tunai;
- rekening;
- e-wallet;
- tabungan;
- kebutuhan rutin.

Output:
- profil finansial awal.

Status:
- Sudah ada pada V2.

Pengembangan berikutnya:
- validasi input;
- format Rupiah;
- edit data tanpa kehilangan data lain.

---

# 6. MODUL 03 — FINANCIAL INVENTORY

Tujuan:

> Mengetahui posisi keuangan pengguna sebelum keputusan dibuat.

Komponen:
- Cash;
- Bank;
- E-wallet;
- Savings.

Fungsi wajib:
- tambah;
- edit;
- hapus;
- total otomatis;
- validasi nominal.

Data utama:

asset_id
name
category
amount
updated_at

---

# 7. MODUL 04 — DEBT REGISTER

Tujuan:

> Menjadikan kewajiban finansial bagian dari konteks keputusan.

Jenis:
- utang pribadi;
- cicilan;
- paylater;
- pinjaman;
- tagihan.

Data:
- nama;
- jenis;
- total kewajiban;
- pembayaran berikutnya;
- jatuh tempo.

Fungsi:
- tambah;
- edit;
- hapus;
- lihat detail;
- total kewajiban;
- kewajiban terdekat.

Catatan metodologis:

Utang bukan definisi langsung Qawām.

Utang memengaruhi kondisi finansial pengguna dan karena itu masuk ke Condition Check.

---

# 8. MODUL 05 — TRANSACTION LEDGER

Tujuan:
mencatat arus uang.

Jenis:
- pemasukan;
- pengeluaran.

Data:
- keterangan;
- nominal;
- kategori;
- tanggal;
- jenis transaksi.

Fungsi:
- tambah;
- edit;
- hapus;
- riwayat;
- total pemasukan;
- total pengeluaran.

---

# 9. MODUL 06 — HOME DASHBOARD

Dashboard harus menjawab:

> "Bagaimana kondisi keuanganku sekarang?"

Komponen:
- uang tersedia;
- kewajiban terdekat;
- pemasukan;
- pengeluaran;
- tombol Saya Mau Membeli;
- transaksi terbaru;
- Qur'anic Guidance.

Prioritas visual:

1. Uang tersedia
2. Kewajiban terdekat
3. Saya Mau Membeli
4. Ringkasan transaksi
5. Qur'anic Guidance

---

# 10. MODUL 07 — SAYA MAU MEMBELI

Ini adalah fitur inti aplikasi.

Input:
- barang/jasa;
- harga;
- tingkat kebutuhan;
- tujuan penggunaan.

Need level:
1. Tidak dibutuhkan
2. Bisa ditunda
3. Dibutuhkan
4. Mendesak

Purpose:
- kuliah;
- pekerjaan;
- kesehatan;
- transportasi;
- keluarga;
- kebutuhan pribadi;
- hiburan;
- gaya hidup;
- lainnya.

Output:
data keputusan untuk Qawām Engine.

---

# 11. MODUL 08 — QAWĀM DECISION CHECK

Framework resmi:

1. Condition
2. Need
3. Purpose / Proper Use
4. Proportionality
5. Financial Continuity

Jangan mengubah lima dimensi ini tanpa keputusan penelitian.

---

# 12. CONDITION CHECK

Pertanyaan utama:

> Bagaimana kondisi finansial pengguna saat ini?

Data:
- uang tersedia;
- kewajiban;
- kebutuhan rutin;
- harga transaksi.

Formula dasar prototype:

available_funds
= cash + bank + ewallet + savings

protected_amount
= near_term_obligations + routine_needs

after_purchase
= available_funds - purchase_price

Condition harus dipahami sebagai konteks, bukan skor moral.

---

# 13. NEED CHECK

Pertanyaan:

> Seberapa dibutuhkan pengeluaran tersebut?

Level:

1 = tidak dibutuhkan
2 = bisa ditunda
3 = dibutuhkan
4 = mendesak

Need tidak otomatis menentukan keputusan.

Contoh:
kebutuhan tinggi tetapi transaksi dapat mengganggu kebutuhan yang lebih mendesak tetap perlu dipertimbangkan.

---

# 14. PURPOSE CHECK

Pertanyaan:

> Untuk apa pengeluaran dilakukan?

Purpose membantu membaca apakah penggunaan harta mempunyai tujuan yang jelas.

Jangan menyimpulkan:

hiburan = salah

atau

barang mahal = salah.

Tujuan harus dibaca bersama kondisi dan proporsionalitas.

---

# 15. PROPORTIONALITY CHECK

Pertanyaan:

> Apakah pengeluaran sepadan dengan kebutuhan dan kondisi pengguna?

Jangan memakai aturan universal seperti:

"pengeluaran > 30% saldo = isrāf"

karena angka tersebut bukan indikator yang ditetapkan oleh tafsir.

Prototype menggunakan contextual rule.

---

# 16. FINANCIAL CONTINUITY CHECK

Pertanyaan:

> Setelah transaksi dilakukan, apakah kebutuhan dan kewajiban terdekat masih dapat dipenuhi?

Data:
- saldo setelah transaksi;
- kewajiban;
- kebutuhan rutin.

Jika ruang finansial menjadi sangat terbatas, keputusan dapat diarahkan ke Tunda atau Pertimbangkan.

---

# 17. RISK RECOGNITION

Risk axis:

## Isrāf
Pengeluaran melampaui batas kewajaran dalam konteks.

Dasar utama:
QS al-Furqān [25]:67
QS al-A'rāf [7]:31

## Iqtār
Menahan pengeluaran secara berlebihan sehingga kebutuhan yang semestinya dapat terganggu.

Dasar:
QS al-Furqān [25]:67

## Tabdhīr
Penggunaan atau pembelanjaan harta secara sia-sia/tidak pada tempatnya.

Dasar:
QS al-Isrā' [17]:26–27

## Maysir
Kategori risiko khusus yang tidak disamakan dengan Qawām.

Dasar:
QS al-Mā'idah [5]:90–91

## Utang
Pencatatan dan konteks kesulitan pembayaran.

Dasar:
QS al-Baqarah [2]:280 dan 2:282

---

# 18. DECISION OUTPUT

Output resmi:

## 🟢 PROPORSIONAL

Pengeluaran relatif sesuai dengan kondisi dan tujuan yang dimasukkan.

## 🟡 PERTIMBANGKAN

Terdapat faktor yang perlu dipertimbangkan kembali.

## 🟠 TUNDA

Pengeluaran berpotensi mengganggu kondisi/kebutuhan/kewajiban.

## ⚪ DATA BELUM CUKUP

Sistem tidak memiliki informasi yang cukup.

Tidak boleh:
- Qawām 87/100;
- ranking pengguna;
- label "orang boros";
- klaim fatwa.

---

# 19. HASIL KEPUTUSAN

Setiap hasil harus menampilkan:

1. hasil;
2. alasan;
3. kondisi;
4. kebutuhan;
5. tujuan;
6. keberlanjutan;
7. catatan risiko bila relevan;
8. ayat terkait;
9. pilihan tindakan.

Pilihan tindakan:
- Tunda;
- Cari Alternatif;
- Tetap Beli.

" tetap beli " tetap tersedia karena keputusan akhir berada pada pengguna.

---

# 20. QUR'ANIC GUIDANCE

Ayat yang digunakan:

### QS al-Furqān [25]:67
وَكَانَ بَيْنَ ذَٰلِكَ قَوَامًا

"Dan pembelanjaan itu berada di tengah-tengah antara yang demikian."

Fungsi:
Qawām.

### QS al-A'rāf [7]:31
وَكُلُوا وَاشْرَبُوا وَلَا تُسْرِفُوا

"Makan dan minumlah, tetapi jangan berlebihan."

Fungsi:
batas Isrāf.

### QS al-Isrā' [17]:26
وَلَا تُبَذِّرْ تَبْذِيرًا

"Janganlah kamu menghambur-hamburkan (hartamu) secara boros."

Fungsi:
Tabdhīr.

### QS al-Baqarah [2]:282
فَاكْتُبُوهُ

"Maka, hendaklah kamu mencatatnya."

Fungsi:
pencatatan utang.

### QS al-Baqarah [2]:280
وَإِنْ كَانَ ذُو عُسْرَةٍ فَنَظِرَةٌ إِلَىٰ مَيْسَرَةٍ

"Jika dia dalam kesulitan, berilah tenggang waktu sampai dia memperoleh kelapangan."

Fungsi:
konteks kesulitan pembayaran.

### QS al-Mā'idah [5]:90
... وَالْمَيْسِرُ ... فَاجْتَنِبُوهُ

"... judi ... maka jauhilah."

Fungsi:
risiko khusus maysir.

Catatan:
Terjemahan pada prototype harus disesuaikan kembali dengan edisi terjemahan yang dipilih untuk naskah final.

---

# 21. MODUL RIWAYAT KEPUTUSAN

Setiap keputusan disimpan:

- item;
- harga;
- hasil;
- alasan;
- tanggal.

Tujuan:
pengguna dapat melihat pola keputusan dari waktu ke waktu.

Jangan mengubahnya menjadi "moral score".

---

# 22. DESAIN VISUAL

Identitas:

Primary:
Hijau emerald.

Background:
Cream / off-white.

Accent:
Gold.

Karakter:
- modern;
- tenang;
- minimalis;
- premium tetapi tidak mewah berlebihan;
- Islamic tanpa terlihat seperti aplikasi kitab.

Komponen:
- rounded card;
- whitespace;
- soft section;
- icon sederhana;
- Arabic verse card;
- visual status.

Hindari:
- terlalu banyak ornamen;
- gradient berlebihan;
- font dekoratif;
- terlalu banyak warna;
- dashboard padat.

---

# 23. SISTEM WARNA HASIL

Proporsional:
green

Pertimbangkan:
yellow/gold

Tunda:
orange

Data belum cukup:
neutral/gray

Warna digunakan sebagai bahasa UI, bukan kategori tafsir.

---

# 24. URUTAN PENGEMBANGAN

## PHASE 0 — BASE

- Project
- Gradle
- Manifest
- Theme
- GitHub Actions

Status:
SELESAI pada V2.

## PHASE 1 — DATA

- AppState
- Local persistence
- Financial Inventory
- Debt Register
- Transaction Ledger

Target:
data stabil.

## PHASE 2 — CORE DECISION

- Saya Mau Membeli
- Need
- Purpose
- Condition
- Proportionality
- Continuity
- Qawām Engine

Target:
decision engine stabil.

## PHASE 3 — RESULT

- Result screen
- Reasoning
- Qur'anic guidance
- Action buttons
- Decision history

## PHASE 4 — CRUD

- Edit asset
- Delete asset
- Edit debt
- Delete debt
- Edit transaction
- Delete transaction

## PHASE 5 — UI POLISH

- spacing;
- typography;
- cards;
- icons;
- colors;
- Arabic typography;
- empty states;
- loading states;
- error states.

## PHASE 6 — TESTING

Test:
- onboarding;
- asset;
- debt;
- transaction;
- decision;
- history;
- reset;
- persistence.

## PHASE 7 — GITHUB

- commit;
- push;
- Actions;
- APK artifact;
- release candidate.

## PHASE 8 — PRESENTATION

- demo flow;
- research narrative;
- 15-minute presentation;
- Q&A simulation.

---

# 25. WORKFLOW SETIAP KALI MEMBUAT FILE

Jika pengguna mengatakan:

> "Create new file"

Assistant harus menjawab dalam format:

FILE:
path/to/FileName.java

ISI FILE:
```java
...
```

Kemudian:

LANGKAH:
1. Create new file
2. Masukkan nama file
3. Paste kode
4. Commit changes
5. Jalankan/test
6. Kirim screenshot

Jangan memberikan banyak file sekaligus kecuali pengguna secara eksplisit meminta batch.

---

# 26. WORKFLOW JIKA ERROR

Jika pengguna mengirim screenshot error:

1. identifikasi file;
2. identifikasi baris/error;
3. jelaskan singkat penyebabnya;
4. berikan file lengkap pengganti bila lebih aman;
5. jangan menambah fitur baru;
6. test ulang;
7. commit setelah berhasil.

Prioritas:

ERROR FIX > FEATURE NEW

---

# 27. WORKFLOW COMMIT

Gunakan commit kecil dan jelas.

Contoh:

feat: add onboarding
feat: add financial inventory
feat: add debt register
feat: add qawam decision engine
feat: add quran guidance
fix: repair decision result
style: improve dashboard UI

---

# 28. CHECKLIST SEBELUM MENGANGGAP APLIKASI SELESAI

## Data
[ ] Semua input tersimpan
[ ] Data tetap ada setelah aplikasi ditutup
[ ] Data dapat diedit
[ ] Data dapat dihapus

## Financial Inventory
[ ] Cash
[ ] Bank
[ ] E-wallet
[ ] Savings
[ ] Total otomatis

## Debt
[ ] Add
[ ] Edit
[ ] Delete
[ ] Due date
[ ] Next payment
[ ] Total

## Transaction
[ ] Income
[ ] Expense
[ ] History
[ ] Total

## Qawām
[ ] Condition
[ ] Need
[ ] Purpose
[ ] Proportionality
[ ] Continuity

## Qur'an
[ ] QS 25:67
[ ] QS 7:31
[ ] QS 17:26–27
[ ] QS 2:280
[ ] QS 2:282
[ ] QS 5:90

## Result
[ ] Proporsional
[ ] Pertimbangkan
[ ] Tunda
[ ] Data Belum Cukup
[ ] Reasoning
[ ] Qur'anic guidance
[ ] User choice

## UI
[ ] Mobile friendly
[ ] No clipped text
[ ] No overflow
[ ] Arabic readable
[ ] Empty states
[ ] Error states
[ ] Consistent colors

## GitHub
[ ] Repository clean
[ ] Commit history clear
[ ] Actions successful
[ ] APK generated

---

# 29. TEST SCENARIO WAJIB

### TEST 01 — Laptop kuliah
Kebutuhan: dibutuhkan
Tujuan: kuliah
Harga: sesuai kemampuan
Expected:
Proporsional atau Pertimbangkan tergantung kondisi.

### TEST 02 — Sepatu karena tren
Kebutuhan: tidak dibutuhkan
Tujuan: gaya hidup
Dana terbatas
Expected:
Tunda/Pertimbangkan.

### TEST 03 — Obat
Kebutuhan: mendesak
Tujuan: kesehatan
Dana cukup
Expected:
Proporsional.

### TEST 04 — Pengeluaran besar dengan kewajiban dekat
Expected:
Tunda.

### TEST 05 — Data tidak lengkap
Expected:
Data Belum Cukup.

### TEST 06 — Utang
Tambah utang.
Tutup aplikasi.
Buka kembali.
Expected:
Data tetap tersimpan.

### TEST 07 — Transaksi
Catat pemasukan.
Catat pengeluaran.
Expected:
Saldo berubah.

### TEST 08 — Reset
Hapus data lokal.
Expected:
Aplikasi kembali ke onboarding.

---

# 30. BATASAN PROTOTYPE

Prototype belum perlu:

- integrasi BRImo;
- integrasi bank;
- open banking;
- sinkronisasi e-wallet;
- AI chatbot;
- automatic bank transaction;
- OCR struk;
- investasi otomatis.

Fitur tersebut dapat menjadi future development.

---

# 31. POSISI ILMIAH

Aplikasi harus selalu dijelaskan dengan rantai:

Qur'an
↓
Tafsir
↓
Konsep Qawām
↓
Operasionalisasi
↓
Decision Framework
↓
Prototype

Bukan:

Aplikasi
↓
cari ayat pembenaran.

---

# 32. KALIMAT KUNCI UNTUK PRESENTASI

> "QAWĀM tidak dibuat untuk mengatakan kepada pengguna apa yang boleh atau tidak boleh dibeli. QAWĀM dirancang untuk membantu pengguna melihat kondisi keuangannya, memahami tujuan pengeluaran, dan mempertimbangkan apakah keputusan tersebut proporsional dan berkelanjutan."

---

# 33. TARGET AKHIR

Produk akhir:

QAWĀM
Personal Financial Decision Assistant

Memiliki:

Financial Inventory
+
Debt Register
+
Transaction Ledger
+
Qawām Decision Check
+
Qur'anic Guidance
+
Decision History

Dengan fondasi:

QS al-Furqān [25]:67

dan ayat pendukung sesuai fungsi masing-masing.

---

# 34. ATURAN VERSI

V2 = prototype full awal

V2.1 = CRUD + validation

V2.2 = UI polish

V2.3 = decision engine refinement

V2.4 = testing

V3 = competition demo/release candidate

Jangan melompat ke V3 sebelum testing selesai.
