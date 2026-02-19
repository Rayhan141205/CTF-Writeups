# Log Hunt - picoCTF

## Informasi Tantangan
- **Kategori:** General Skills
- **Tingkat Kesulitan:** Medium
- **Platform:** picoCTF

## Deskripsi
Diberikan sebuah file log server yang berukuran cukup besar. Terdapat informasi bahwa sebuah *flag* telah bocor dan tersebar di dalam baris-baris log tersebut. Tantangan ini mensimulasikan tugas *defensive* (Blue Team) dalam menginvestigasi log server.

## Langkah Penyelesaian
1. **Mengunduh File Log:**
   Saya menggunakan OS Linux di VirtualBox untuk mengunduh file log melalui terminal:
   `wget https://challenge-files.picoctf.net/c_amiable_citadel/49cec6157142f24a599f4164d5b63322c2494f801390d6f22eb91b3aa592bc66/server.log`

    <img width="468" height="998" alt="image" src="https://github.com/user-attachments/assets/39a6788c-5461-4f3f-8e41-d19468447a2c" />


3. **Investigasi Pola (Pattern Matching):**
   Dengan mengetahui bahwa format *flag* selalu diawali dengan `picoCTF{`, saya menggunakan perintah `grep` untuk mencari baris awal:
   `grep "picoCTF" server.log`
   <img width="406" height="167" alt="image" src="https://github.com/user-attachments/assets/4a6da5c7-54f1-4f2a-8dbc-701ac8daa365" />

   Dari hasil tersebut, saya menemukan bahwa kepingan *flag* ditandai dengan label khusus yaitu `FLAGPART:`.

4. **Memfilter Kepingan Flag:**
   Karena ada baris yang berulang (*duplicate*), saya menggabungkan `grep` dengan `sort -u` untuk menyaring dan mengurutkan log yang mengandung kata kunci `FLAGPART`:
   `grep "FLAGPART" server.log | sort -u`

   <img width="409" height="473" alt="image" src="https://github.com/user-attachments/assets/31f0ef41-c938-4951-a05c-dfe8dd8516de" />


5. **Merangkai Flag:**
   Berdasarkan urutan *timestamp* dari hasil perintah di atas, kepingan *flag* dirangkai menjadi satu kesatuan utuh.

## Flag
`picoCTF{us3_y0urlinux_sk1lls_cedfa5fb}`
