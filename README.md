**🏛️ Universitas Islam Indonesia (UII) – DSpace**

**🔹 Platform: DSpace**

- **Alamat Akses**: <https://dspace.uii.ac.id>
- **Deskripsi**: UII menggunakan DSpace sebagai platform untuk mengelola dan mendistribusikan karya ilmiah digital, termasuk skripsi, tugas akhir, laporan, dan makalah ilmiah.
- **Fitur Utama**:
  - **Akses Terbuka**: Pengguna dapat mengakses dan mengunduh dokumen tanpa perlu login.
  - **Mode Akses**:
    - **Browse**: Menelusuri koleksi berdasarkan kategori.
    - **Search**: Mencari dokumen berdasarkan kata kunci.
  - **Integrasi**: Mendukung protokol OAI-PMH untuk interoperabilitas dengan sistem lain.
- **Pengembangan dan Pelatihan**: UII secara aktif mengadakan pelatihan bagi petugas perpustakaan dalam penggunaan DSpace dan integrasinya dengan alat cek plagiarisme seperti Turnitin. 
-----
**🏛️ Universitas Airlangga (UNAIR) – EPrints**

**🔹 Platform: EPrints**

- **Alamat Akses**: <https://repository.unair.ac.id>
- **Deskripsi**: UNAIR menggunakan EPrints sebagai platform open-source untuk membangun repository digital yang memungkinkan pengelolaan dan publikasi karya ilmiah seperti jurnal, artikel, tesis, dan disertasi. 
- **Fitur Utama**:
  - **Akses Terbuka**: Koleksi sebelum tahun 2007 dapat diakses secara bebas, sementara koleksi dari tahun 2008 ke atas memerlukan persetujuan dari fakultas terkait. 
  - **Unggah Mandiri**: Mahasiswa dapat mengunggah karya ilmiahnya secara mandiri melalui sistem AILIS for Education. 
  - **Integrasi**: Mendukung protokol OAI-PMH dan dapat terindeks oleh Google Scholar, meningkatkan visibilitas karya ilmiah.
- **Pengembangan dan Pelatihan**: UNAIR menyediakan kelas "Unggah Mandiri Repository" untuk membimbing mahasiswa dalam mengunggah karya ilmiah sesuai format yang ditentukan.

📊 Tabel Perbandingan DSpace (UII) vs EPrints (UNAIR)



|**Aspek**|**UII (DSpace)**|**UNAIR (EPrints)**|
| :- | :- | :- |
|**Alamat Repository**|[https://dspace.uii.ac.id](https://dspace.uii.ac.id/)|[https://repository.unair.ac.id](https://repository.unair.ac.id/)|
|**Platform Sistem**|DSpace|EPrints|
|**Jenis Platform**|Open-source, fokus pada distribusi dan pengarsipan dokumen|Open-source, fleksibel untuk publikasi dan pengelolaan repository|
|**Tipe Akses**|Akses terbuka penuh (tidak butuh login)|Terbuka untuk koleksi sebelum 2007; koleksi pasca-2008 terbatas|
|**Mode Pencarian**|Search (kata kunci), Browse (judul, penulis, tahun, subjek)|Search + Browse by Author, Year, Division, Subject|
|**Koleksi Utama**|Skripsi, laporan, tugas akhir, makalah ilmiah|Skripsi, tesis, disertasi, laporan PKL, artikel ilmiah|
|**File Dokumen PDF**|Umumnya tersedia langsung untuk diunduh|Tidak selalu tersedia (tergantung kebijakan fakultas)|
|**Unggah Mandiri**|Tidak tersedia untuk mahasiswa; unggah oleh admin/pustakawan|Tersedia via AILIS (login mahasiswa)|
|**Proses Unggah Mandiri**|—|Upload → Isi metadata → Submit → Verifikasi admin → Publikasi|
|**Plagiarisme (Turnitin)**|Terintegrasi (untuk pengecekan sebelum unggah oleh pustakawan)|Tidak disebutkan eksplisit integrasi dengan Turnitin|
|**Protokol OAI-PMH**|Ya (untuk harvesting metadata oleh sistem eksternal)|Ya (memungkinkan indexing Google Scholar, dll.)|
|**Indeks Google Scholar**|Bisa, tergantung pengaturan OAI-PMH dan metadata|Ya, biasanya sudah terindeks|
|**Pelatihan Mahasiswa**|Tidak wajib unggah mandiri, pelatihan internal bagi pustakawan|Ada kelas "Unggah Mandiri Repository" secara rutin|
|**User Interface (UI)**|Sederhana, direct ke dokumen|Lebih fleksibel, banyak filter pencarian|
|**Kecepatan Akses**|Cepat, stabil|Cepat, kadang beberapa file tidak langsung dapat diakses|
|**Lisensi Karya Ilmiah**|Umumnya CC (Creative Commons) jika disebutkan|Bergantung pada fakultas, kadang tidak ditampilkan|
|**Akses Mahasiswa Umum**|Sangat mudah, tanpa login|Tergantung kebijakan tiap fakultas|



### Scraping Metadata dari DSpace/EPrints (untuk riset)

Gunakan Python + BeautifulSoup atau Scrapy. Contoh untuk DSpace:


  ```bash
      import requests
      from bs4 import BeautifulSoup

      url = 'https://dspace.uii.ac.id/handle/123456789/1/browse?type=dateissued&sort_by=2&order=DESC&rpp=10'
      response = requests.get(url)
      soup = BeautifulSoup(response.text, 'html.parser')

      items = soup.find_all('div', class_='artifact-title')
      for item in items:
          title = item.get_text(strip=True)
          link = 'https://dspace.uii.ac.id' + item.find('a')['href']
          print(f"Judul: {title} \nLink: {link}\n")
```




 Untuk **EPrints UNAIR**, target div atau table dengan class ep\_summary\_content.


**Note:** ⚠️ Gunakan headers dan sleep() untuk menghindari pemblokiran oleh firewall.





