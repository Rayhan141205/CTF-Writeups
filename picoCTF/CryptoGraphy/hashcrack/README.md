# hashcrack - picoCTF

## Informasi Tantangan
- **Kategori:** Cryptography
- **Tingkat Kesulitan:** Easy
- **Platform:** picoCTF

## Deskripsi
Sebuah perusahaan menyimpan pesan rahasia di server yang berhasil diretas karena admin menggunakan *password* dengan algoritma *hashing* yang lemah. Tugas kita adalah mendapatkan akses ke pesan rahasia tersebut dengan cara melakukan *cracking* pada *hash* yang diberikan oleh server.

## Langkah Penyelesaian

1. **Menghubungkan ke Server:**
   Saya menggunakan `nc` (Netcat) untuk terhubung ke *instance* server yang diberikan:
   `nc verbal-sleep.picoctf.net 59703`
   Server kemudian memberikan *hash* pertama untuk dipecahkan.

2. **Proses Cracking dengan John the Ripper:**
   Saya menggunakan alat `john` beserta *wordlist* populer `rockyou.txt` untuk memecahkan *hash* melalui metode *Dictionary Attack*. Proses ini dilakukan secara bertahap untuk tiga jenis algoritma *hash* yang berbeda:

   * **Hash 1 (MD5):** `482c811da5d5b4bc6d497ffa98491e38`
     `john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hash.txt`
     *Hasil:* `password123`

   * **Hash 2 (SHA-1):** `b7a875fc1ea228b9061041b7cec4bd3c52ab3ce3`
     `john --format=raw-sha1 --wordlist=/usr/share/wordlists/rockyou.txt hash.txt`
     *Hasil:* `letmein`

   * **Hash 3 (SHA-256):** `916e8c4f79b25028c9e467f1eb8eee6d6bbdff965f9928310ad30a8d88697745`
     `john --format=raw-sha256 --wordlist=/usr/share/wordlists/rockyou.txt hash.txt`
     *Hasil:* `qwerty098`

   <img width="751" height="189" alt="hash_MD5" src="https://github.com/user-attachments/assets/42211c43-b8cb-4894-85eb-e76a6c7ac245" />
   <img width="738" height="170" alt="hash_sha1" src="https://github.com/user-attachments/assets/f3b863e1-10ca-47e0-ba23-c18ccd8206a1" />
    <img width="768" height="177" alt="image" src="https://github.com/user-attachments/assets/0b37a022-346a-4692-a145-9a88a52d3297" />


3. **Mendapatkan Flag:**
   Setelah semua *password* berhasil di-*crack*, saya memasukkannya satu per satu kembali ke dalam sesi Netcat. Setelah *password* ketiga (`qwerty098`) diterima, server membuka akses dan memberikan *flag* rahasia.

   <img width="460" height="22" alt="Screenshot 2026-03-09 230742" src="https://github.com/user-attachments/assets/feff5a13-c892-4f56-bb45-ebc097163b97" />


## Flag
`picoCTF{UseStr0nG_h@shEs_&PaSswDs!_ccc21957}`
