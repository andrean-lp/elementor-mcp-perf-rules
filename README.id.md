# Elementor MCP Performance Rules (Bahasa Indonesia)

> Panduan aturan performa dan Core Web Vitals untuk membangun halaman WordPress berkecepatan 95-100 PageSpeed menggunakan Elementor Model Context Protocol (MCP) dan AI Agent.

[English Version](README.md)

---

## Gambaran Umum

Fitur **Elementor MCP** memungkinkan AI Agent (Claude Code, Cursor, Antigravity, Codex) untuk langsung mendesain dan mengedit struktur asli Elementor di website WordPress kamu.

Namun jika AI tidak diberi batasan yang ketat, AI cenderung membuat struktur yang membuat website lambat:
- Menumpuk container bertingkat-tingkat (DOM bloat melebihi 1.500 elemen)
- Memasang slider berat atau video autoplay di bagian atas layar (merusak skor LCP)
- Menaruh gambar tanpa ukuran pasti sehingga tampilan bergeser saat loading (merusak skor CLS)
- Memanggil banyak jenis Google Font yang memperlambat render halaman

Repositori ini menyediakan **Sistem Aturan Otomatis (Guardrails)** yang memaksa AI untuk selalu menghasilkan struktur Elementor yang ramping, modern, dan lolos uji Core Web Vitals sejak perintah pertama.

---

## 5 Pilar Utama Performa

1. **Struktur DOM Ramping:** Wajib menggunakan Flexbox Container dan CSS Grid (Elementor V4). Kedalaman container dibatasi maksimal 2 tingkat. Dilarang menggunakan widget Spacer kosong.
2. **Hero Section Super Cepat (LCP < 1.2 detik):** Dilarang memasang slider atau video latar belakang di bagian atas layar. Wajib menggunakan 1 gambar statis WebP/AVIF berukuran ringan (< 120 KB).
3. **Nol Pergeseran Tata Letak (CLS = 0):** Setiap gambar dan elemen embed wajib memiliki aspect ratio atau ukuran lebar dan tinggi yang pasti. Tipografi wajib menggunakan `font-display: swap`.
4. **Pembatasan Font & Aset:** Maksimal 2 keluarga font dengan maksimal 2 tingkat ketebalan. Mengutamakan icon inline SVG dibanding font icon pihak ketiga yang berat.
5. **Standar Aksesibilitas & SEO:** Hierarki judul berurutan secara ketat (tepat satu H1 per halaman, lalu H2 dan H3), serta kontras warna sesuai standar WCAG AA (minimal 4.5:1).

---

## Cara Penggunaan

### Pilihan 1: Menggunakan Cursor AI
1. Unduh atau salin file `.cursorrules`.
2. Letakkan file `.cursorrules` di folder root proyek kamu.
3. Cursor akan otomatis membaca aturan ini setiap kali kamu memberikan perintah desain via Elementor MCP.

### Pilihan 2: Menggunakan Antigravity / Gemini CLI
1. Salin file `.gemini/rules/elementor-perf.md` ke folder `.gemini/rules/` lokal kamu.
2. Antigravity akan otomatis menerapkan aturan performa ini setiap kali berinteraksi dengan WordPress.

### Pilihan 3: Menggunakan Claude Desktop / Tool AI Lainnya
1. Buka file [`prompts/system-prompt.md`](prompts/system-prompt.md).
2. Salin teks prompt tersebut ke pengaturan System Prompt proyek kamu.

---

## Lisensi

Dirilis di bawah lisensi [MIT License](LICENSE).
