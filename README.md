# REFLEKSI
## Fransisca Ellya Bunaren - 2306152286
### TUTORIAL

### TIMER
![Screenshot of the message](img/message_1.png)

Output yang didapatkan adalah 
* `Fransisca's Komputer: hey hey`
* `Fransisca's Komputer: howdy!`
* `Fransisca's Komputer: done!`

Hal ini terjadi karena `hey hey` dicetak langsung di main sebelum executor dijalankan. Setelah itu, executor menjalankan task async yang mencetak `howdy!`, lalu berhenti sejenak karena await TimerFuture. Setelah timer selesai (2 detik), task dilanjutkan dan mencetak `done!`

![Screenshot of the message](img/message_2.png)

Jika tidak menggunakan `drop(spawner)`, executor tidak pernah tahu bahwa tidak ada task lagi yang akan dikirim. Akibatnya, ia akan terus menunggu di recv() meskipun semua task sudah selesai, membuat program tidak pernah selesai atau hang.