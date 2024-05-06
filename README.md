# Tutorial 10 
Wahyu Hidayat - 2206081894 - Advanced Programming B

***Experiment 1.2: Understanding how it works***

<div align="center">
    <img width="446" alt="Screenshot 2024-05-06 at 4 23 28 PM" src="https://github.com/wahyuhiddayat/advprog-module10-timer/assets/119432989/60a9c326-3c4d-40d9-9180-9b8148ec6927">
</div>

Kalimat "Wahyu's Computer: hey hey" dieksekusi terlebih dahulu karena dieksekusi secara langsung di `main` thread sebelum `executor.run()`. Kemudian `executor.run()` mulai menjalankan futures dalam urutan yang sesuai. Kalimat "Wahyu's Computer: howdy!" dicetak setelahnya karena muncul saat `spawner.spawn` memulai eksekusi future yang dimulai dengan println tersebut. Setelah timer future selesai (dua detik kemudian), eksekusi melanjutkan kalimat "Wahyu's Computer: done!".

***Experiment 1.3: Multiple Spawn and removing drop***

<div align="center">
    <p>Tanpa `drop(spawner)`</p>
    <img width="447" alt="Screenshot 2024-05-06 at 4 30 27 PM" src="https://github.com/wahyuhiddayat/advprog-module10-timer/assets/119432989/d38173c4-f341-4d54-8450-82ec1ee2febb">
    <img width="447" alt="Screenshot 2024-05-06 at 4 31 00 PM" src="https://github.com/wahyuhiddayat/advprog-module10-timer/assets/119432989/3eae3f7c-be85-4af5-b354-aef9bedfc486">
</div>

<div align="center">
    <p>Dengan `drop(spawner)`</p>
    <img width="414" alt="Screenshot 2024-05-06 at 4 31 41 PM" src="https://github.com/wahyuhiddayat/advprog-module10-timer/assets/119432989/24714a08-f38e-4ad6-bf73-f54f122d07db">
</div>

Ketika `drop(spawner);` dikomentari, executor terus berputar dan "stuck" karena spawner masih ada. Hal ini membuat executor terus mengharapkan adanya task baru yang dikirim ke dalam ready queue. Namun, karena tidak ada task baru yang dikirim, executor tetap berjalan tanpa berhenti, mencari task yang tidak ada.

Jika `drop(spawner);` tidak dikomentari, hal ini memberikan sinyal kepada executor bahwa tidak ada lagi task baru yang akan dikirim. Dengan demikian, executor dapat menyelesaikan prosesnya dengan benar setelah menyelesaikan task yang tersisa di dalam ready queue.
