---
name: three-3d
description: Gunakan saat pengguna minta objek, model, denah, atau adegan 3D interaktif di browser — misalnya model organ sederhana, alat medis, denah ruangan, produk, atau visual edukasi yang bisa diputar dan di-zoom.
---
# Adegan 3D dengan Three.js

Selalu mulai dari `template.html` di folder ini, lalu ganti bagian `// === ADEGAN ===`.

## Aturan teknis
1. Satu file HTML mandiri. Three.js dimuat lewat importmap dari CDN (versi dikunci, lihat template). Tanpa build tool.
2. Wajib ada: OrbitControls (putar, zoom, geser; sentuh di HP), resize responsif, `setPixelRatio(Math.min(devicePixelRatio, 2))`.
3. Pencahayaan: HemisphereLight + DirectionalLight dengan bayangan. Lantai menerima bayangan.
4. Bangun objek dari primitif (Box, Cylinder, Sphere, Capsule, Torus, Lathe untuk bentuk berputar seperti botol/lampu). Kelompokkan tiap benda dalam `THREE.Group` dengan nama jelas.
5. Skala nyata dalam meter (meja operasi ±2 m × 0,6 m × 0,9 m). Kamera awal menatap pusat adegan.
6. Material: `MeshStandardMaterial`, palet maksimal 5 warna, roughness 0,4–0,8.
7. Label: pakai fungsi `label()` di template (CSS2DRenderer), teks pendek ≤ 4 kata.
8. Gerakan: lewat `clock.getDelta()` di loop. Hormati `prefers-reduced-motion` (matikan putaran otomatis).
9. Performa: < 200 mesh, geometri dan material dipakai ulang bila sama.
10. Panel info kecil di pojok (judul + petunjuk kontrol), bahasa Indonesia.

## Batasan konten
- Model anatomi/medis bersifat skematis untuk edukasi; tulis "Ilustrasi skematis, bukan ukuran klinis" di panel info.
- Jangan meniru logo, karakter, atau produk bermerek.

## Pemeriksaan sebelum selesai
- Tidak ada error sintaks; semua import ada di importmap.
- Semua label terbaca dari sudut kamera awal.
