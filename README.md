# 🛰️ AgriScan NDVI Simulator

**AgriScan NDVI Simulator** adalah sebuah aplikasi web interaktif satu halaman (Single Page Application) yang dirancang untuk mengedukasi pengguna tentang **Pertanian Presisi (Precision Agriculture)**. 

Aplikasi ini mensimulasikan bagaimana drone dan satelit menggunakan **Cahaya Tampak (RGB)** dan **Inframerah Dekat (Near-Infrared / NIR)** untuk memetakan dan memantau kesehatan tanaman di suatu lahan pertanian secara *real-time*.

![AgriScan Preview](<img width="1920" height="1426" alt="screencapture-agrisanndvi-plant-healthy-simulatio-vercel-app-2026-11-04-23_14_28" src="https://github.com/user-attachments/assets/b857d766-07bd-48db-b87c-8416daf6d7f1" />
) *(Ganti link ini dengan screenshot website kamu nantinya)*

---

## 🎯 Tujuan Proyek
Proyek ini dibuat untuk tujuan edukasi dan presentasi guna mempermudah pemahaman konsep gelombang cahaya dan biologi tanaman. Melalui simulasi visual dan interaktif, pengguna dapat melihat hal-hal yang tidak kasatmata (seperti cahaya inframerah) dan memahami bagaimana data tersebut diolah menjadi informasi yang menyelamatkan hasil panen petani.

---

## 📖 Pengetahuan Umum & Teori Dasar

### 1. Keterbatasan Mata Manusia vs "Mata Super" Drone
Mata manusia (dan kamera standar) hanya mampu melihat spektrum cahaya tampak, yaitu **Merah, Hijau, dan Biru (RGB)**. Namun, sinar matahari mengandung spektrum yang jauh lebih luas, termasuk **Inframerah Dekat (NIR - Near Infrared)** yang tidak bisa kita lihat. Sensor multispektral pada drone pertanian bertindak sebagai "mata super" yang menangkap pantulan cahaya NIR ini.

### 2. Klorofil & Struktur Daun (Kenapa Tanaman Hijau?)
*   **Cahaya Merah (Fotosintesis):** Tanaman yang sehat memiliki banyak klorofil. Klorofil sangat aktif menyerap gelombang cahaya merah dan biru untuk dijadikan energi (fotosintesis), dan memantulkan sisa cahaya hijau ke mata kita.
*   **Cahaya Inframerah (Sistem Pendingin):** Struktur sel internal daun (jaringan mesofil) bertindak seperti spons yang memantulkan cahaya Inframerah (NIR) secara masif. Tujuannya agar daun tidak menyerap terlalu banyak panas dari matahari.

### 3. Deteksi Penyakit Lebih Awal
Ketika tanaman mulai stres (kekurangan air, hama, atau penyakit), klorofil akan rusak (sehingga kurang menyerap cahaya merah) dan struktur sel daun kolaps (sehingga pantulan NIR menurun). Perubahan ini terdeteksi oleh sensor inframerah jauh sebelum daun tersebut terlihat layu atau menguning di mata manusia.

---

## 🧮 Rumus Sains: Apa itu NDVI?

**NDVI (Normalized Difference Vegetation Index)** adalah indeks kalkulasi matematika standar yang digunakan di seluruh dunia untuk mengukur seberapa hijau atau sehat suatu area vegetasi.

**Rumus NDVI:**
```text
NDVI = (NIR - Merah) / (NIR + Merah)
```
*   **NIR** = Persentase pantulan cahaya Inframerah Dekat
*   **Merah** = Persentase pantulan cahaya Merah kasatmata

**Cara Membaca Skor NDVI (Skala -1.0 hingga +1.0):**
*   🟢 **0.6 s/d 1.0** : Vegetasi sangat sehat, lebat, dan aktif berfotosintesis.
*   🟡 **0.2 s/d 0.5** : Vegetasi stres (kurang air/nutrisi) atau semak belukar jarang.
*   🟤 **-0.1 s/d 0.1** : Tidak ada vegetasi (tanah kosong, batu, aspal, atau tanaman mati).
*   🔴 **-1.0 s/d 0.0** : Air, genangan, lumpur, atau awan (Air menyerap hampir semua gelombang inframerah).

---

## ✨ Fitur Utama Simulator

1. **Peta Lahan Interaktif (10x10 Grid):** Simulasi kebun dari sudut pandang udara. Pengguna dapat mengklik setiap petak untuk melakukan "scanning" data lahan.
2. **Slider Before/After (RGB vs NDVI):** Fitur geser interaktif untuk membandingkan pandangan mata telanjang (RGB) di mana semua tanaman terlihat hijau, dengan pandangan sensor (NDVI) di mana masalah lahan langsung menyala berwarna kuning/merah.
3. **Dashboard Analitik Dinamis:** Menampilkan metrik setiap kali area diklik:
   - Skor NDVI secara *real-time* (dengan indikator *Gauge* warna).
   - Data persentase pantulan cahaya Merah vs NIR.
   - Grafik batang interaktif membandingkan penyerapan cahaya.
   - Diagnosis masalah (Stres air, hama, pipa bocor).
   - Rekomendasi tindakan langsung untuk petani.
4. **Modal "Cara Kerjanya":** Jendela *pop-up* yang berisi penjelasan teori edukatif menggunakan gaya bahasa analogi yang santai dan mudah dipahami.

---

## 📊 Data Simulasi (Zona Lahan)
Simulator ini menggunakan *mock data* (data buatan) yang didasarkan pada kurva spektrum ilmiah nyata. Lahan dibagi menjadi 4 zona kasus:
*   **Zona A (Sehat):** Pantulan NIR tinggi (85%), Merah rendah (8%). Skor NDVI tinggi.
*   **Zona B (Stres Kurang Air):** Pantulan NIR turun (40%), Merah naik (30%). Skor NDVI merosot.
*   **Zona C (Hama/Tanah Kosong):** Pantulan NIR dan Merah nyaris sama (20% vs 25%). NDVI mendekati angka 0.
*   **Zona D (Genangan/Pipa Bocor):** Pantulan NIR sangat rendah karena diserap air (10%). NDVI menjadi negatif.

---

## 💻 Tech Stack yang Digunakan

Aplikasi ini dibangun menggunakan arsitektur *Front-End* yang ringan tanpa memerlukan *backend* atau *database*:
*   **HTML5** (Semantik struktur UI)
*   **Tailwind CSS (via CDN)** (Styling yang responsif, *dark-mode dashboard UI*)
*   **Vanilla JavaScript (ES6)** (Logika simulasi, manipulasi DOM, matematika NDVI)
*   **Chart.js** (Visualisasi grafik pantulan cahaya)

---

## 🚀 Cara Menjalankan Secara Lokal (Local Setup)

Karena proyek ini adalah *Single Page Application* yang statis, cara menjalankannya sangat mudah:
1. *Clone* repositori ini: `git clone https://github.com/username-kamu/agriscan-ndvi.git`
2. Buka folder proyek.
3. *Double-click* file `agriscan_ndvi_simulator.html` (atau buka langsung menggunakan browser modern seperti Chrome, Firefox, Edge, atau Safari).
4. Tidak butuh *Node.js* atau *build tools* apapun!
*   **Asisten AI:** Powered by Google Antigravity
*   **Status Proyek:** Prototipe Edukasi

> *Catatan: Data yang disajikan dalam simulasi ini adalah data contoh yang dibuat secara matematis berdasarkan tren pantulan cahaya tanaman pada umumnya, bukan berasal dari input sensor kamera asli.*
