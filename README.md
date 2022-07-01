# **LGBT Sentiment Analysis**

## **Pendahuluan**

Melihat maraknya perbincangan mengenai isu LGBT di Indonesia baru-baru ini, penulis tertarik untuk melakukan analisis sentimen masyarakat Indonesia mengenai isu LGBT. Sentimen yang akan diteliti terdiri dari tiga jenis, yaitu positif, netral, dan negatif. Analisis sentimen ini dilakukan menggunakan data dari media sosial Twitter berupa tweet yang ditulis pada tanggal 8-9 Juni 2022. Tweet diambil melalui API dengan kata kunci: LGBT, LGBTQ, LGBTQ+, lesbian, lesbi, transgender, homo,gay,homoseksual, biseks, biseksual, bisex. Terdapat 1403 tweet yang memenuhi kriteria pencarian yang kemudian digunakan untuk analisis sentimen. Analisis sentimen dilakukan menggunakan kombinasi antara Google Translate dan TextBlob. Metode ini dipilih karena performa analisis sentimen menggunakan algoritma machine learning, seperti Naïve Bayes, sangat bergantung pada daftar kata positif dan negatif yang digunakan. Sedangkan, belum ada library atau daftar kata dalam bahasa Indonesia yang dirasa cukup memadai untuk digunakan dalam analisis sentimen ini.

## **Pre-processing**

Tahapan pre-processing analisis sentimen: 
1.	Membersikan tweet dari unsur-unsur yang tidak diperlukan dalam analisis sentimen. Langkah ini dilakukan dengan menghapus username, link website, hashtag, dll.
2.	Menghapus empty tweets yang terbentuk setelah tahap 1.
3.	Mengganti beberapa istilah/slang ke dalam bahasa Indonesia yang baku. Proses penggantian ini dilakukan menggunakan daftar kata-kata yang sudah penulis buat, dikombinasikan dengan daftar kata-kata yang ada pada library. Proses ini dilakukan untuk mempersempit variasi kata dan memperkecil kesalahan translasi saat melakukan analisis sentimen.
4.	Melakukan language detection dan menghapus tweet yang tidak ditulis dalam bahasa Indonesia atau bahasa Inggris. Pada percobaan pengambilan tweet sebelumnya, penulis menemukan beberapa tweet yang ditulis dalam bahasa asing (selain bahasa Inggris) meskipun sudah melakukan pencarian menggunakan keyword lang=’id’. Tweet-tweet seperti ini diduga ditulis bukan oleh WNI. Oleh karena itu, tweet yang ditulis dalam bahasa asing (selain bahasa Inggris) dihapus.


**_Note:_** 
_Karena pada twitter terdapat fitur retweet yang dapat mengepost ulang tweet dari orang lain, maka tweet dari hasil retweet ini dianggap sebagai bentuk dukungan seseorang terhadap pendapat orang lain. Oleh karena itu tweet yang duplikat (karena adanya retweet) tidak dihapus, karena dapat mempengaruhi persentase jumlah orang dengan sentimen positif, negatif, atau netral. Stopwords sengaja tidak dihilangkan agar tidak mengubah makna saat melakukan sentiment analysis menggunakan Google Translate dan TextBlob._

Tahapan pre-processing visualisasi data (setelah analisis sentimen):
1.	Melakukan tokenisasi dan filtering. Pada tahap ini, stopwords dalam tweet dihapus karena tidak memberikan informasi yang berharga dan agar tidak mengganggu tampilan visualisasi data teks. Daftar stopwords yang digunakan diambil dari NLTK dan Sastrawi.
2.	Melakukan lemmatisasi. Pada tahap ini kata-kata pada tweet diubah ke dalam bentuk dasar, hal ini berguna untuk mengurangi variasi kata sehingga lebih mudah menemukan kata kunci yang paling sering dipakai dalam tweet.
3.	Melakukan visualisasi dalam bentuk word cloud melalui situs https://voyant-tools.org/ . Jenis visualisasi ini dipilih karena jenis visualisasi yang lainnya, seperti link dan word-tree, kurang dapat memberikan informasi.

## **Analisis Dasar** 

Proses analisis dilakukan dengan mentranslate tweet ke dalam bahasa Inggris menggunakan Google Translate, kemudian dilanjutkan dengan analisis sentimen menggunakan TextBlob. Terdapat dua jenis hasil dari proses ini, yaitu sentiment dan subjectivity. Sentiment terdiri dari positive (polarity > 0), netral (polarity = 0), dan negatif (polarity < 0). Sedangkan subjecticity terdiri dari subjektif (subjectivity > 0,5) dan objektif (subjectivity < 0,5). Berikut adalah hasil yang diperoleh.

![image](https://user-images.githubusercontent.com/99953890/176853754-277ef242-cc06-4336-9c16-2266be105a08.png)

Terlihat bahwa mayoritas tweet, yaitu sebesar 42,9% tweet, memberikan sentimen positif terhadap isu LGBT, sedangkan 38,7% tweet bersentimen netral, dan 18,4% tweet sisanya bersentimen negatif. Terlihat juga bahwa mayoritas dari tweet dengan sentimen positif bersifat subjektif, sedangkan mayoritas tweet bersentimen netral bersifat objektif. 

Berikut adalah hasil visualisasi data teks yang digunakan untuk analisis sentimen.

![image](https://user-images.githubusercontent.com/99953890/176853716-0d445e41-0e24-41a3-84c4-aefcb6ccd984.png)
 
Dari hasil visualisasi tersebut, terdapat beberapa kata kunci (selain kata kunci yang digunakan untuk mengambil data) yang menarik untuk ditelusuri kembali. Kata kunci tersebut diantaranya adalah “satpol”, “kafe”,”formula”,”kampanye”, dan “dukung”. Penulis kemudian mencari kembali isu apa yang diperbincangkan terkait dengan kata kunci ini. Berikut adalah hasil penelusuran oleh penulis:

1.	Pada tweet dengan keyword “satpol” dan “kafe”, banyak orang memperbincangkan mengenai penggrebekan satpol PP kepada dua pasangan pria yang pangku-pangkuan di salah satu kafe di Jakarta. Ada dua pendapat dalam tweet yang saya amati, yaitu yang pro dan yang kontra dengan tindakan satpol PP. Pihak kontra berpendapat bahwa satpol PP tidak seharusnya melakukan penggerebekan, karena dasar penggrebekan adalah perda. Sedangkan tidak ada perda Jakarta yang melarang bisnis yang mengandung LGBT.

2.	Pada tweet dengan keyword “formula”, “kampanye”, dan “dukung”, banyak orang membicarakan mengenai acara formula E yang baru-baru ini digelar. Pasalnya, sponsor utama dari acara ini adalah perusahaan besar yang memproduksi bir dan mendukung LGBT. Tidak hanya itu, formula E juga dianggap sebagai kampanye LGBT yang terselundup. Anggapan ini didukung dengan adanya salah satu tim yang menggunakan stiker pelangi di mobilnya. Akibat dari kejadian ini, banyak orang yang mengkritik sikap gubernur DKI Jakarta, Anies Baswedan, melalui twitter. Anies dianggap salah satu pendukung LGBT.  

## **Kesimpulan**
LGBT merupakan isu yang penting dan banyak diperdebatkan. Di satu sisi, LGBT merupakan HAM yang perlu dilindungi, namun di sisi lain LGBT dianggap sebagai sebuah penyimpangan terhadap norma dan agama. Oleh karena itu, Pemerintah dan DPR RI., sebaiknya segera menyusun peraturan perundang-undangan yang mengatur aktivitas dan gerakan LGBT, untuk mencegah meluasnya penyimpangan orientasi seksual di masyarakat.
