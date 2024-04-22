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
