# Dual Load Cell Monitoring System (Standaritation Production)

Proyek ini adalah sistem monitoring berat menggunakan dua buah sensor **Load Cell** yang terhubung ke modul **HX711**. Sistem ini dirancang untuk memantau dua target berat yang berbeda secara bersamaan dengan indikator LED sebagai status standarisasi berat.



## 🚀 Fitur Utama
- **Dual Sensor Monitoring**: Membaca data dari dua Load Cell (Sensor A & Sensor B) secara independen.
- **Noise Gate Filter**: Mengabaikan pembacaan di bawah 0.4kg untuk stabilitas data (mencegah *drift* angka kecil).
- **Indikator LED Visual**:
    - **LED Biru**: Menyala jika berat Sensor A masuk rentang target (1.0kg - 2.0kg).
    - **LED Hijau**: Menyala jika berat Sensor B masuk rentang target (3.0kg - 4.0kg).
    - **LED Merah**: Indikator standby atau peringatan jika berat tidak sesuai standar.
- **Auto-Tare**: Melakukan kalibrasi nol otomatis selama 5 detik saat perangkat dinyalakan.

---

## 🛠️ Konfigurasi Pin (Hardware)

Sistem ini dikonfigurasi menggunakan pin berikut (berdasarkan NodeMCU/ESP8266):

| Komponen | Pin | Fungsi |
| :--- | :--- | :--- |
| **Sensor A (DT)** | D2 | Data Pin (Target 2kg) |
| **Sensor A (SCK)** | D1 | Clock Pin |
| **Sensor B (DT)** | D4 | Data Pin (Target 5kg) |
| **Sensor B (SCK)** | D3 | Clock Pin |
| **LED Merah** | D5 | Standby / Invalid Weight |
| **LED Biru** | D6 | Sensor A OK (1.0 - 2.0kg) |
| **LED Hijau** | D7 | Sensor B OK (3.0 - 4.0kg) |

---

## 💻 Cara Penggunaan

1. **Instalasi Library**: Pastikan Anda telah menginstal library `HX711` oleh Bogdan Necula di Arduino IDE.
2. **Kalibrasi**: Sesuaikan nilai `faktorA` dan `faktorB` pada kode program sesuai dengan hasil kalibrasi fisik sensor Anda.
3. **Upload**: Masukkan kode ke dalam Microcontroller.
4. **Monitoring**: Buka Serial Monitor dengan baud rate **115200**.

### Logika Indikator LED
- **Standby**: LED Merah menyala saat kedua sensor kosong.
- **Stabil**: Saat berat sesuai target, LED Biru (A) atau Hijau (B) akan menyala, dan LED Merah akan mati.
- **Invalid**: Jika ada benda namun beratnya tidak masuk kategori target, LED Merah akan tetap menyala sebagai peringatan.

---

## 📜 Lisensi
Proyek ini dilisensikan di bawah **MIT License**.
