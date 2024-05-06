# Tutorial 10 
Wahyu Hidayat - 2206081894 - Advanced Programming B

***Experiment 1.2: Understanding how it works.***

<div align="center">
    <img width="446" alt="Screenshot 2024-05-06 at 4 23 28 PM" src="https://github.com/wahyuhiddayat/advprog-module10-timer/assets/119432989/60a9c326-3c4d-40d9-9180-9b8148ec6927">
</div>

Kalimat "Wahyu's Computer: hey hey" dieksekusi terlebih dahulu karena dieksekusi secara langsung di `main` thread sebelum `executor.run()`. Kemudian `executor.run()` mulai menjalankan futures dalam urutan yang sesuai. Kalimat "Wahyu's Computer: howdy!" dicetak setelahnya karena muncul saat `spawner.spawn` memulai eksekusi future yang dimulai dengan println tersebut. Setelah timer future selesai (dua detik kemudian), eksekusi melanjutkan kalimat "Wahyu's Computer: done!".
