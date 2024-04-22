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
