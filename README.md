# Modul 10 Pemrograman Lanjut : Asynchronous Programming
oleh **Brenda Po Lok Fahida**

<br>
<br>



## Experiment 1.2: Understanding how it works.
<img src="image/image_1.png">

<br>

Setelah menambahkan baris `println!("Brenda's Komputer: hey hey");` tepat setelah pemanggilan `spawner.spawn(...)`, hasil yang muncul saat program dijalankan menunjukkan bahwa kalimat "Brenda's Komputer: hey hey" dicetak terlebih dahulu, kemudian diikuti oleh "Brenda's Komputer: howdy!" dan, setelah dua detik, "Brenda's Komputer: done!". Hal ini terjadi karena `spawner.spawn(...)` tidak langsung menjalankan tugas yang diberikan, melainkan hanya mendaftarkan tugas tersebut ke dalam antrean executor. Karena proses tersebut bersifat non-blocking, eksekusi program langsung berlanjut ke baris berikutnya dan mencetak "hey hey". Barulah setelah `executor.run()` dijalankan, executor mulai menjalankan task yang telah di-*spawn*, yang mencetak "howdy!", menunggu selama dua detik menggunakan `TimerFuture`, dan kemudian mencetak "done!". Ini menunjukkan bagaimana tugas asynchronous berjalan secara independen dan executor-lah yang mengatur kapan tugas-tugas tersebut dijalankan.
