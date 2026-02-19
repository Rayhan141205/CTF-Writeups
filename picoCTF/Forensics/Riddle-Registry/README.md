# Riddle Registry - picoCTF

## Informasi Tantangan
- **Kategori:** Forensics
- **Tingkat Kesulitan:** Easy
- **Platform:** picoCTF

## Deskripsi
Diberikan sebuah file PDF bernama `confidential.pdf`. File tersebut berisi teks pengecoh, namun instruksi menyebutkan bahwa *flag* tersembunyi di dalam *metadata* dokumen tersebut.

## Langkah Penyelesaian
1. **Mengunduh File:**
   Pertama, saya mengunduh file tantangan melalui terminal menggunakan `wget`:
   `wget https://artifacts.picoctf.net/c/530/confidential.pdf`
<img width="934" height="995" alt="image" src="https://github.com/user-attachments/assets/bdabcc9e-4f12-4750-b18a-43cbfed297ab" />

2. **Analisis Metadata:**
   Karena petunjuk mengarah pada metadata, saya menggunakan `exiftool` untuk memeriksa informasi tersembunyi di balik file PDF tersebut:
   `exiftool confidential.pdf`

3. **Menemukan dan Mendekode Flag:**
   Pada *output* terminal, saya menemukan sebuah teks mencurigakan di bagian `Author` yang terlihat seperti format Base64:
   `cGljb0NURntwdXp6bDNkXz0zdGFkYXRhaX2YwdW5kIV84N2JlNjBjMH0=`
   
   Saya kemudian mendekode teks tersebut menggunakan perintah bawaan Linux:
   `echo "cGljb0NURntwdXp6bDNkXz0zdGFkYXRhaX2YwdW5kIV84N2JlNjBjMH0=" | base64 -d`
<img width="1880" height="507" alt="image" src="https://github.com/user-attachments/assets/f0583db2-7e15-4c19-982b-e958886ad0c6" />

## Flag
`picoCTF{puzzl3d_m3tadata_f0und!_87be60c0}`
