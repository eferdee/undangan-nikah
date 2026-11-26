UNDANGAN PERNIKAHAN DIGITAL - AYU & ARYA (Luxury Editorial Motion)

Cara pakai: buka index.html di browser. Folder assets/ harus ikut (berisi GSAP & ScrollTrigger lokal).
Butuh internet hanya untuk Google Fonts & peta Google Maps.

Redesain bagian tengah (Acara & Lokasi dirombak: medali tanggal, kartu acara, peta berbingkai + kartu info) (setelah hero, sebelum footer): Pembuka, Mempelai, Kisah Kami, Acara, Lokasi,
Galeri, RSVP & Ucapan. Hero, amplop pembuka, dan footer tidak diubah.
Arah: editorial mewah. Tipografi besar, garis halus sebagai pemisah, tanpa bayangan/bingkai/gradasi,
satu motif songket (pita di atas bagian Acara) dan satu garis Jembatan Ampera (placeholder foto Kisah Kami).

Yang mudah diubah (di dalam index.html):
1. Nama, tanggal, jam, lokasi, orang tua, URL musik -> objek "const C" di awal <script> terakhir.
2. Warna -> variabel di :root (--ivory, --champagne, --wine, --gold, --rose).
3. Foto mempelai & galeri -> C.foto (wanita, pria; rasio 4:5; kisah rasio 16:9) dan C.galeri (src, cap).
   Bila src kosong, tampil bidang warna senada (inisial/nomor) sebagai placeholder; foto asli otomatis menggantikannya. Disarankan WebP/JPG sisi panjang maks. 1600px (< 300 KB).
4. Nama tamu di amplop pembuka -> index.html?to=Nama%20Tamu
5. RSVP & ucapan tersimpan di localStorage browser tamu. Untuk ucapan yang terlihat semua tamu, sambungkan backend.

Sistem gerak:
- GSAP 3.12.5 + ScrollTrigger (assets/). Tanpa Lenis: scroll tetap native agar anchor, nav, dan restorasi scroll aman.
- Opening amplop 3D (CSS 3D + GSAP) -> tombol "Buka Undangan" -> transisi dua panel clip-path turun ke bawah.
- Bila GSAP gagal dimuat, undangan tetap berfungsi dengan animasi CSS sederhana.
- prefers-reduced-motion: seluruh gerak dimatikan, konten langsung tampil.

Bagian tengah (gerak):
- Foto dibuka dengan mask (clip-path) lalu skala turun; foto asli mendapat paralaks tipis. Placeholder dibiarkan diam.
- Judul bagian muncul kata demi kata lewat mask; garis pemisah digambar; bagian gelap (Acara, Galeri) melebar penuh saat masuk.
- Tahun di rel Kisah Kami menempel dan berganti sesuai bab yang dibaca (desktop).
- Tanpa GSAP / reduced-motion: semua konten tampil langsung (cadangan IntersectionObserver).

Performa & stabilitas HP:
- Tekstur kertas kini assets/paper.png (sebelumnya SVG feTurbulence yang berat saat scroll). Folder assets/ wajib ikut.
- Hero dibungkus .hero-clip agar zoom saat buka undangan tidak melebarkan halaman (penyebab scroll ke kanan).
- Mode ringan (layar sentuh / <900px): efek paralaks & pelebaran bagian gelap saat scroll dimatikan.
