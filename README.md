# DDoS-Attack-Simulation-DVWA

## Identitas 

- Nama: Fathya Shabira A.T
- NIM: 105841111923
- Kelas: 5 JK A

## Deskripsi Proyek

Repository ini berisi dokumentasi dan laporan praktikum/tugas mata kuliah Ethical Hacking yang berfokus pada:
- Simulasi serangan Denial of Service (DoS/DDoS)
- Konfigurasi dan hardening web server
- Analisis dampak serangan terhadap ketersediaan layanan

Tujuan utama proyek ini adalah memahami mekanisme serangan DDoS pada aplikasi web dan pentingnya penerapan mitigasi untuk menjaga availability sistem.

## Target Pengujian

| Komponen | Deskripsi |
|----------|-----------|
| Target Server | Ubuntu Server 24.04 LTS - IP: 192.168.132.136 |
| Aplikasi Web | DVWA (Damn Vulnerable Web Application) |
| Attacker Machine | Kali Linux - IP: 192.168.132.132 |
| Network Device | Cisco 2960-24TT Switch |

## Topologi Jaringan

                2960-24TT
                 Switch0
                /        \
               /          \
     Laptop-PT              Laptop-PT
ATTACKER (KALI)         TARGET (UBUNTU)


## Tools yang Digunakan

| Tools | Fungsi |
|-------|--------|
| Kali Linux | Sistem operasi untuk penetration testing |
| Ubuntu Server 24.04 | Sistem operasi target server |
| VMware Workstation | Virtualisasi lingkungan lab |
| Slowloris | Application-layer DoS attack tool |
| hping3 | Network-layer SYN-flood attack tool |
| Apache2 | Web server yang menjadi target |
| MariaDB | Database server untuk DVWA |
| DVWA | Aplikasi web rentan untuk pengujian |
| Wireshark | Analisis trafik jaringan (opsional) |

## Jenis Serangan yang Diuji

1. **Slowloris Attack**
   - Serangan application-layer yang menghabiskan slot koneksi Apache
   - Mengirim HTTP header secara lambat untuk mempertahankan koneksi
   
2. **SYN-Flood Attack**
   - Serangan network-layer yang membanjiri TCP handshake
   - Menggunakan spoofed source IP untuk menghindari connection completion

## Konfigurasi Weakening (Lab Purpose)

Untuk memperjelas dampak serangan, server sengaja dilemahkan:


## Hasil Pengujian

| Kondisi | Akses DVWA | Ping ke Target | Status Layanan |
|---------|------------|----------------|----------------|
| Sebelum serangan | ✅ Normal | ✅ 0% loss | 🟢 Available |
| Saat serangan | ❌ 500 Error / Timeout | ✅ 0% loss | 🔴 Denial of Service |
| Setelah serangan | ✅ Normal | ✅ 0% loss | 🟢 Available |

**Kesimpulan:**
- Host tetap hidup (ping sukses) namun layanan web tidak dapat diakses
- Serangan berhasil menyebabkan Denial of Service pada port 80/HTTP
- Pemulihan terjadi setelah traffic serangan dihentikan

## Catatan Etis

⚠️ **PENTING:**
Semua pengujian dilakukan pada lingkungan **laboratorium virtual pribadi** yang sepenuhnya terisolasi. Tidak ada serangan yang dilakukan terhadap sistem nyata atau infrastruktur publik. Penggunaan teknik ini terhadap sistem tanpa izin adalah **ilegal** dan melanggar hukum siber.

## Referensi

- DVWA Official: https://github.com/digininja/DVWA
- Slowloris Documentation
- hping3 Manual
- Apache2 MPM Configuration
- Linux Kernel TCP/IP Tuning

---
© 2025 - Ethical Hacking Lab Project
