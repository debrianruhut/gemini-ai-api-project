# **Server API Google Gemini AI dengan Node.js**

Proyek ini menyediakan server backend sederhana yang dibuat dengan **Node.js** dan **Express.js** untuk berinteraksi dengan Google Gemini AI API. Server ini mengekspos beberapa endpoint RESTful untuk menangani berbagai jenis input: teks, gambar, dokumen, dan audio, menjadikannya fondasi yang kuat untuk membangun aplikasi AI yang lebih kompleks.

## **✨ Fitur Utama**

* **Generasi Teks**: Menghasilkan konten berdasarkan prompt teks sederhana.  
* **Analisis Gambar**: Memberikan gambar dan prompt untuk mendapatkan wawasan atau deskripsi.  
* **Pemrosesan Dokumen**: Meringkas, menganalisis, atau mengajukan pertanyaan tentang konten dokumen.  
* **Transkripsi Audio**: Mentranskripsikan atau menganalisis file audio.  
* **Multimodal**: Mampu memproses kombinasi teks dan media (gambar, dokumen, audio) dalam satu permintaan.  
* **Mudah Diperluas**: Kode yang terstruktur dengan baik memudahkan penambahan endpoint atau fungsionalitas baru.

## **⚙️ Teknologi yang Digunakan**

* **Node.js**: Lingkungan eksekusi JavaScript sisi server.  
* **Express.js**: Kerangka kerja web minimalis untuk Node.js.  
* **@google/genai**: SDK resmi dari Google untuk berinteraksi dengan Gemini API.  
* **Multer**: Middleware untuk menangani multipart/form-data, digunakan untuk mengunggah file.  
* **dotenv**: Modul untuk memuat variabel lingkungan dari file .env.

## **🚀 Memulai**

Ikuti langkah-langkah ini untuk menjalankan server secara lokal di mesin Anda.

### **Prasyarat**

* [Node.js](https://nodejs.org/) (versi 18.x atau yang lebih baru direkomendasikan).  
* npm atau yarn sebagai manajer paket.  
* Kunci API Google Gemini. Anda bisa mendapatkannya dari [Google AI Studio](https://aistudio.google.com/app/apikey).

### **Instalasi**

1. **Kloning repositori ini:**  
   ```
   git clone https://github.com/debrianruhut/gemini-ai-api-project 
   cd NAMA_REPOSITORI_ANDA
   ```

2. **Instal semua dependensi:**  
   ```
   npm install
   ```

   atau jika Anda menggunakan yarn:  
   ```
   yarn install
   ```
3. Konfigurasi Variabel Lingkungan:  
   Buat file bernama .env di direktori root proyek dan tambahkan kunci API Anda:  
   # .env  
   ```
   GEMINI_API_KEY="MASUKKAN_KUNCI_API_ANDA_DI_SINI"  
   PORT=3000
   ```

   * GEMINI_API_KEY: Kunci API yang Anda dapatkan dari Google AI Studio.  
   * PORT: Port tempat server akan berjalan (opsional, default ke 3000).

### **Menjalankan Server**

Untuk memulai server, jalankan perintah berikut di terminal Anda:

```
node index.js
```

Anda akan melihat pesan konfirmasi di konsol:  
Server is running on port 3000

## **📖 Dokumentasi API**

Server menyediakan empat endpoint utama. Semua endpoint merespons dengan format JSON.

### **1. Generate dari Teks**

Menghasilkan konten berdasarkan prompt teks.

**URL**: /generate-text  
**Metode**: POST  
**Body**: application/json  
```
  {  
      "prompt": "Tulis sebuah cerita pendek tentang robot yang belajar melukis."  
  }
```

**Contoh cURL**:  
  curl -X POST -H "Content-Type: application/json" 
  -d '{"prompt": "Tulis sebuah cerita pendek tentang robot yang belajar melukis."}'
  http://localhost:3000/generate-text

### **2. Generate dari Gambar**

Menganalisis gambar dan menghasilkan teks berdasarkan gambar dan prompt.

**URL**: /generate-from-image  
**Metode**: POST  
**Body**: multipart/form-data  
```
- prompt (teks): Pertanyaan atau instruksi Anda mengenai gambar.  
- image (file): File gambar yang akan diunggah (misalnya, .jpg, .png).  
```

**Contoh cURL**:  
  curl -X POST -F "prompt=Objek apa saja yang ada di gambar ini?" 
  -F "image=@/path/ke/gambar/anda.jpg"   
  http://localhost:3000/generate-from-image

### **3. Generate dari Dokumen**

Meringkas atau menganalisis konten file dokumen.

**URL**: /generate-from-document  
**Metode**: POST  
**Body**: multipart/form-data  
```
- prompt (teks, opsional): Instruksi spesifik. Jika kosong, defaultnya adalah "Summarize the document.".  
- document (file): File dokumen yang akan diunggah (misalnya, .txt, .pdf).
```
 
**Contoh cURL**:  
  curl -X POST -F "prompt=Sebutkan tiga poin utama dari dokumen ini."  
  -F "document=@/path/ke/dokumen/anda.txt"  
  http://localhost:3000/generate-from-document

### **4. Generate dari Audio**

Mentranskripsikan atau menganalisis file audio.

**URL**: /generate-from-audio  
**Metode**: POST  
**Body**: multipart/form-data  
```
- prompt (teks, opsional): Instruksi spesifik. Jika kosong, defaultnya adalah "Transcribe or analyze the following audio.".  
- audio (file): File audio yang akan diunggah (misalnya, .mp3, .wav).
```
 
**Contoh cURL**:  
  curl -X POST -F "prompt=Transkripsikan audio ini ke dalam bahasa Indonesia." 
  -F "audio=@/path/ke/audio/anda.mp3" 
  http://localhost:3000/generate-from-audio

## **🤝 Kontribusi**

Kontribusi selalu diterima! Jika Anda ingin meningkatkan proyek ini, silakan fork repositori dan buat *pull request*. Anda juga bisa membuka *issue* jika menemukan bug atau memiliki saran fitur.

1. Fork repositori ini.  
2. Buat branch fitur baru (git checkout -b fitur FiturBaru).  
3. Lakukan perubahan Anda (git commit -m 'Menambahkan FiturBaru').  
4. Push ke branch tersebut (git push origin fitur FiturBaru).  
5. Buka *Pull Request*.

## **📄 Lisensi**

Proyek ini dilisensikan di bawah Lisensi MIT. Lihat file LICENSE untuk detailnya.
