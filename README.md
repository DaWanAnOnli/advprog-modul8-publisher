<h1>
  Refleksi
</h1>

<h2>
  No 7
</h2>

<h3>
  a.
</h3>

Ada lima pesan (message) yang dikirm oleh program publisher saat di-run. Hal ini dapat dilihat dari lima panggilan publish_event pada main function di main.rs, masing-masing dengan user_id dan user_name yang berbeda-beda. Penerima pesan (subscriber) akan menerima setiap dari lima pesan yang dikirim oleh publisher.

<h3>
  b.
</h3>

URL yang sama di publisher dan subscriber berarti kedua pihak terhubung dengan broker AMQP yang sama, yaitu yang berjalan di mesin lokal. Publisher dan subscriber dapat berkomunikasi melalui broker. Pada kasus ini, publisher mengirim data dan subscriber menerimanya. 


![image](https://github.com/DaWanAnOnli/advprog-modul8-publisher/assets/124868777/9b1810a8-6876-4f4f-9d6a-bcad033844f4)





Console Publisher
![image](https://github.com/DaWanAnOnli/advprog-modul8-publisher/assets/124868777/5939a964-8bc9-428b-8099-51a610d72ad1)




Console Subscriber:
![image](https://github.com/DaWanAnOnli/advprog-modul8-publisher/assets/124868777/6f56f7a7-be3f-4ebe-8ce3-166941f207d2)

Penjelasan:
Pertama, program subscriber harus ada dalam keadaan running. Lalu, saat program publisher di run, publisher akan mengirim 5 pesan ke subscriber. Pesan yang diterima oleh subscriber akan diterima oleh subscriber dan diproses oleh function handle. Function ini akan mem-print message yang diterima ke console, sehingga muncul kelima pesan di console subscriber. Ini adalah contoh dari bagaimana dua project yang berbeda dapat berkomunikasi menggunakan broker AMQP. Hal ini akan membantu dalam integrasi modul-modul pada aplikasi yang besar.





![image](https://github.com/DaWanAnOnli/advprog-modul8-publisher/assets/124868777/d1602c12-29de-4608-adec-e76cc2ccc234)

Penjelasan:
Chart kedua di RabbitMQ (yang berwarna ungu) menunjukkan message rates, yaitu berapa banyak message yang dikirim dalam satu detik. Saat program publisher dijalankan, ada 5 messages yang dikirim sekaligus (hampir instan). RabbitMQ tidak mendeteksi 5 messages secara instan, namun didistribusikan dalam waktu 10 detik (lonjakannya berbentuk seperti segitiga). Dapat dilihat bahwa alas segitiga adalah 10 detik, dan tinggi segitiga adalah 1 message/detik. Maka dengan rumus segitiga, dapat dihitung jumlah message pada periode segititiga tersebut = (1/2) * (1 message / detik) * (10 detik) = 5 messages -- sesuai dengan program. Perhitungan yang serupa dapat dilakukan juga untuk lonjakan yang berbentuk trapezium.





![image](https://github.com/DaWanAnOnli/advprog-modul8-publisher/assets/124868777/e6ececff-4efb-43da-adbb-85e5caa1fc37)

Penjelasan:
Saya menjalankan cargo run 7 kali berturut-turut di console publisher saya. Kali ini, subscriber tidak bisa menerima setiap message sekaligus, karena ada jeda 10 ms dalam menerima message. Alhasil dalam beberapa detik pertama queue meningkat drastis, karena penambahan jumlah message yang dikirim (dengan cargo run pada publisher) lebih banyak dari jumlah message yang diterima (diambil dari queue oleh subscriber). Queue mencapai maksimum antara 20 dan 30 (kita anggap 25). Mengapa tidak 35? Padahal publishe di run sebanyak 7 kali, masing-masing dengan 5 message. Hal ini karena sudah ada beberapa message yang diterim publisher, sehingga yang tersimpan dalam queue tidak mencapai 35. Setelah titik tersebut subscriber mengambil message dari queue secara perlahan tapi pasti (1 message per 10 ms).


