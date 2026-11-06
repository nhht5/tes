GAMEZONE COMMUNITY — PANDUAN SETUP

File:
- index.html: website login/daftar + grup chat realtime
- firestore.rules: aturan keamanan database

PENTING:
Website ini memerlukan Firebase. File tidak akan bisa menyimpan akun/chat sungguhan sampai Firebase dikonfigurasi dan aturan database dipasang.

LANGKAH SETUP FIREBASE:
1. Buka https://console.firebase.google.com/ lalu buat project baru, misalnya "gamezone-community".
2. Di menu Authentication > Get started > Sign-in method, aktifkan "Email/Password".
3. Di Project settings (ikon roda gigi) > General > Your apps, tambahkan aplikasi Web (ikon </>).
4. Salin firebaseConfig yang diberikan Firebase.
5. Buka index.html dan ganti nilai:
   apiKey: "ISI_API_KEY"
   authDomain: "ISI_PROJECT_ID.firebaseapp.com"
   projectId: "ISI_PROJECT_ID"
   storageBucket: "ISI_PROJECT_ID.appspot.com"
   messagingSenderId: "ISI_MESSAGING_SENDER_ID"
   appId: "ISI_APP_ID"
   dengan nilai asli dari Firebase.
6. Buka Firestore Database > Create database.
7. Buka tab Rules, ganti seluruh aturan dengan isi file firestore.rules, lalu klik Publish.
8. Upload index.html ke repository GitHub Pages. Pastikan file bernama index.html berada di root repository.
9. Buka alamat website. Buat dua akun berbeda untuk menguji chat dari dua browser/perangkat.

CARA KERJA:
- Firebase Authentication mengelola email/password; password tidak disimpan di dokumen profil.
- Firestore menyimpan profil dan pesan.
- Semua akun yang berhasil login dapat membaca dan mengirim pesan ke grup umum.
- Login di perangkat lain dengan akun yang sama akan memakai akun yang sama; akun berbeda tetap masuk ke grup umum yang sama.
- Sesi login disimpan oleh browser sampai pengguna logout atau data browser dibersihkan.

KEAMANAN & BATASAN:
- Jangan pernah membagikan password atau file konfigurasi privat. Firebase web config memang berada di frontend; keamanan data bergantung pada Firestore Security Rules.
- Aturan contoh mengizinkan semua pengguna login membaca grup umum. Jangan gunakan untuk menyimpan data pribadi/sensitif.
- Untuk website publik, tambahkan fitur lapor/blokir anggota, moderasi admin, pembatasan spam, dan verifikasi email sebelum komunitas dibuka luas.
- Aktifkan Firebase App Check dan atur batas penggunaan/billing alerts sebelum dipublikasikan secara luas.
