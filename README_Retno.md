# ECC-NIN_MangroveChain_Retno_Kusbianto_Batch_9

Repositori ini dibuat oleh Kelompok 1 untuk memenuhi soal ujian (Task 2) yang diberikan untuk menguasai sistem manajemen basis data relasional objek / PostgreSQL dan pemrograman Python dalam konteks MANGROVECHAIN CONSERVATION ANALYTICS. Dengan semangat inovasi dan kolaborasi, kami berupaya menghasilkan karya yang tidak hanya memenuhi standar, tetapi juga mencerminkan dedikasi kami untuk mendukung pembangunan sistem inovatif yang menggabungkan teknologi blockchain dengan upaya konservasi mangrove di seluruh Indonesia.

---
### 👥 Kelompok 1

| Nama            | No Absen       | Kelompok |
|------------------|----------------|----------|
| Retno K     | 9.007.DB2025   | 1        |      


---
## 📜 BAB 1 PENDAHULUAN

### 1.1 Latar Belakang
Hutan mangrove merupakan salah satu ekosistem pesisir paling penting di dunia, terutama dalam mitigasi perubahan iklim melalui kemampuan tinggi menyerap karbon (blue carbon). Indonesia memiliki hutan mangrove terluas secara global, sekitar 3,7 juta hektare atau 23% dari total mangrove dunia. Ekosistem ini berperan besar dalam menahan abrasi, melindungi pesisir, mendukung keanekaragaman hayati, dan menjadi penyimpan karbon yang sangat efektif dengan potensi hingga 1.000 ton karbon per hektare.

Namun, keberadaan mangrove menghadapi ancaman serius. Sejak tahun 1980, sekitar 40% hutan mangrove Indonesia telah rusak akibat konversi lahan menjadi tambak, polusi limbah industri, dan tekanan aktivitas manusia seperti penebangan untuk kayu bakar. Di sisi lain, perubahan iklim, termasuk kenaikan permukaan laut, memperburuk kondisi ekosistem ini. Kurangnya kesadaran masyarakat dan keterbatasan pendanaan juga menjadi hambatan besar dalam upaya konservasi.

Sementara itu, pasar karbon global membuka peluang ekonomi melalui perdagangan kredit karbon, di mana setiap 1 kredit mewakili 1 ton CO₂ yang berhasil diserap. Hutan mangrove yang direhabilitasi dapat menghasilkan kredit karbon bernilai ekonomi tinggi, sehingga menjadi insentif bagi upaya konservasi. Namun, pengelolaan data dan transaksi kredit karbon menghadapi tantangan besar, seperti kurangnya transparansi, risiko manipulasi data, double counting, serta biaya validasi yang tinggi.

MangroveChain adalah sistem inovatif yang menggabungkan teknologi blockchain dengan upaya konservasi mangrove di seluruh Indonesia. Analisis ini menyediakan wawasan mendalam tentang 30 proyek konservasi dari Aceh hingga Papua, melacak kepatuhan regulasi, dampak biodiversitas, keterlibatan masyarakat, dan transaksi kredit karbon yang tercatat dalam ledger blockchain yang tidak dapat diubah
Sistem ini mengintegrasikan 14 dimensi data termasuk pemantauan lingkungan, catatan kepemilikan lahan, sumber pendanaan, dan transaksi smart contract untuk menciptakan pandangan komprehensif tentang efektivitas konservasi. Ada 5 analisis yang menjadi dasar latar belakang masalah, diantaranya :
1. **Analisis Efektivitas Regulasi & Dampak Biodiversitas** : Tim konservasi menemukan adanya perbedaan yang cukup besar dalam hasil pemantauan biodiversitas pada berbagai proyek konservasi. Sebagai contoh, di Kalimantan Timur, proyek yang telah mendapatkan izin resmi menunjukkan kerapatan pohon hingga 40% lebih tinggi dibandingkan proyek yang izinnya masih menunggu persetujuan. Namun, situasinya berbeda di Jawa, di mana kualitas air tetap buruk meskipun izin proyek sudah disetujui. Analisis ini bertujuan mengungkap pola sistemik bagaimana kerangka regulasi dan struktur kepemilikan lahan mempengaruhi hasil konservasi.Hal ini didorong oleh tingginya risiko penyelewengan dana, kurangnya transparansi, dan sulitnya mengukur dampak secara akurat dalam model pendanaan konvensional. Sebuah konsorsium investor hijau bahkan telah mengalokasikan dana sebesar 15 juta dolar AS untuk proyek konservasi mangrove. 
Penelitian ini difokuskan untuk menjawab beberapa pertanyaan penting, yaitu:

   - Apakah status izin proyek berpengaruh terhadap peningkatan biodiversitas, misalnya kualitas air dan kerapatan pohon?
     
   - Bagaimana perbedaan kepemilikan lahan (negara, swasta, masyarakat) memengaruhi keanekaragaman spesies?
     
   - Apakah proyek dengan batas lahan yang jelas secara hukum mampu mencapai hasil ekologi yang lebih baik?

3. **Optimalisasi Pendanaan Berbasis Blockchain.** Investor berdampak (impact investors) kini semakin menuntut bukti terverifikasi mengenai efektivitas program dalam mengurangi emisi karbon serta integritas data yang disajikan. Hal ini didorong oleh tingginya risiko penyelewengan dana, kurangnya transparansi, dan sulitnya mengukur dampak secara akurat dalam model pendanaan konvensional. Sebuah konsorsium investor hijau bahkan telah mengalokasikan dana sebesar 15 juta dolar AS untuk proyek konservasi mangrove. Namun, dana ini hanya akan disalurkan jika terdapat jaminan bahwa proyek tersebut memenuhi persyaratan ketat, antara lain :

   - Perlindungan data yang kuat melalui enkripsi blockchain.
     
   - Persetujuan masyarakat yang terdokumentasi
     
   - Bukti efisiensi penyerapan karbon
   
   Dengan demikian, dibutuhkan sebuah sistem analisis yang mampu mengoptimalkan pendanaan berbasis blockchain, dengan menekankan pada :

   - Kuantifikasi penyerapan karbon per unit investasi

   - Verifikasi tata kelola data yang sesuai standar

   - Pemilihan proyek dengan kinerja terbaik

   Optimalisasi ini bukan hanya akan meningkatkan kepercayaan investor, tetapi juga mendorong tercapainya target mitigasi perubahan iklim secara lebih transparan dan akuntabel.

3. **Prediksi Kinerja Proyek Berbasis Keterlibatan Masyarakat**. : Keberhasilan suatu proyek pembangunan tidak hanya bergantung pada ketersediaan sumber daya dan perencanaan teknis, tetapi juga pada tingkat keterlibatan masyarakat dalam proses pelaksanaannya. Studi empiris menunjukkan bahwa proyek yang memiliki partisipasi masyarakat tinggi cenderung lebih berkelanjutan dalam jangka panjang. Data historis memperlihatkan bahwa proyek dengan tingkat keterlibatan masyarakat di atas 30% memiliki peluang keberlanjutan hingga 75% lebih tinggi setelah tiga tahun dibandingkan proyek dengan partisipasi rendah. Adapun faktor analisisnya antara lain :

   - Seberapa sering masyarakat ikut kegiatan, Misalnya berapa kali ada lokakarya, konsultasi, atau pelatihan yang melibatkan masyarakat.
  
   - Bagaimana manfaat ekonomi dibagi ke warga lokal. Apakah keuntungan atau bantuan dari proyek benar-benar sampai ke masyarakat sekitar?

   - Tingkat keikutsertaan dibandingkan jumlah warga. Dari seluruh anggota komunitas, berapa banyak yang ikut berpartisipasi?

   - Hubungan waktu antara kegiatan dan peningkatan keanekaragaman hayati. Apakah setelah ada kegiatan tersebut, keanekaragaman hayati (biodiversitas) meningkat? Dan berapa lama jeda waktunya?
  
4. **Analisis Risiko Hukum Multi-Dimensi**. Pengelolaan proyek dengan kompleksitas tinggi sering kali menghadapi tantangan hukum yang dapat mempengaruhi keberlanjutan dan keberhasilan implementasi. Risiko hukum ini muncul dari berbagai faktor, diantaranya :

   - Perizinan yang tertunda, batas lahan yang tidak jelas.
  
   - kepemilikan lahan masyarakat adat yang sulit diverifikasi.
  
   - Kualitas lingkungan yang buruk serta kebutuhan restorasi yang intensif

   Berdasarkan studi kasus di Sulawesi Selatan, proyek yang mengandung ketiga faktor risiko tersebut memiliki kemungkinan 60% lebih tinggi untuk menghadapi konflik hukum dalam dua tahun mendatang. Hal ini menunjukkan pentingnya analisis risiko hukum yang bersifat multi-dimensi agar perusahaan maupun instansi terkait dapat mengantisipasi potensi permasalahan secara proaktif. Identifikasi yang tepat terhadap kombinasi faktor risiko ini menjadi kunci dalam menyusun strategi mitigasi yang efektif untuk menghindari sengketa dan memperlancar proses implementasi proyek.

   Adapun metodologi yang digunakan, yaitu :

   - Sistem scoring dengan bobot berbeda untuk setiap kriteria risiko. Artinya, setiap faktor risiko (misalnya izin, kepemilikan lahan, kualitas air) diberi nilai (skor) sesuai tingkat pengaruhnya. Faktor yang lebih penting diberi bobot lebih besar.

   - Klasifikasi proyek menjadi risiko rendah, sedang, tinggi. Setelah semua faktor dinilai, proyek dikelompokkan menjadi tiga kategori: risiko rendah, risiko sedang, atau risiko tinggi.

   - Analisis geospasial pola sebaran risiko. Ini berarti menggunakan peta dan data lokasi untuk melihat di mana proyek-proyek dengan risiko tertentu berada, sehingga bisa diketahui pola penyebarannya

5. **Analisis Jaringan Blockchain dalam Konservasi**. implementasi teknologi ini memerlukan pemahaman mendalam mengenai pola berbagi data dalam jaringan blockchain.  CTO (Chief Technology Officer) harus mampu menganalisis berbagai tipe data yang terlibat, seperti :

   - Distribusi tipe data (Geografis/Personal/Transaksi) per wilayah : Melihat sebaran berbagai jenis data di setiap wilayah. Misalnya, di satu wilayah lebih banyak data lokasi (geografis), sedangkan di wilayah lain lebih banyak data pribadi atau data transaksi.

   - Korelasi antara level akses dengan volume transaksi karbon : Melihat tingkat keterbukaan data (misalnya data terbuka untuk umum atau hanya untuk pihak tertentu) berpengaruh terhadap jumlah transaksi karbon yang terjadi. Contohnya, apakah jika data lebih terbuka, jumlah transaksi karbon jadi lebih banyak?

   - Pola temporal penerbitan izin vs aktivitas blockchain : Mempelajari bagaimana waktu penerbitan izin (misalnya izin konservasi) berkaitan dengan aktivitas di blockchain. Misalnya, apakah aktivitas blockchain meningkat setiap kali izin baru diterbitkan?

   Hasil analisis awal menunjukkan bahwa proyek dengan data geografis terbuka memiliki volume transaksi 2,5 kali lebih tinggi dibandingkan proyek yang datanya terbatas. Fakta ini menunjukkan pentingnya analisis jaringan blockchain untuk menentukan strategi distribusi data, pengelolaan izin, serta pengembangan arsitektur sistem yang efektif dan berkelanjutan dalam mendukung konservasi.

   Adapun aspek teknisnya antara lain :

   - Analisis jaringan hubungan antara node data : Mempelajari bagaimana titik-titik (node) dalam jaringan blockchain saling terhubung. Misalnya, siapa yang mengirim data, siapa yang menerima, dan bagaimana pola koneksinya.

   - Pola aliran informasi antar stakeholder : Melihat bagaimana informasi berpindah dari satu pihak ke pihak lain (misalnya dari pemerintah ke LSM atau dari perusahaan ke masyarakat). Ini penting agar komunikasi dan koordinasi berjalan lancar

   - Optimasi desain smart contract : Membuat aturan otomatis (smart contract) yang lebih efisien dan aman supaya transaksi berjalan cepat, transparan, dan tanpa kesalahan.
   
---
