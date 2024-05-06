# Tutorial 10 
Wahyu Hidayat - 2206081894 - Advanced Programming B

***Experiment 1.2: Understanding how it works.***

Kalimat "Wahyu's Computer: hey hey" dieksekusi terlebih dahulu karena dieksekusi secara langsung di `main` thread sebelum `executor.run()`. Kemudian `executor.run()` mulai menjalankan futures dalam urutan yang sesuai. Kalimat "Wahyu's Computer: howdy!" dicetak setelahnya karena muncul saat `spawner.spawn` memulai eksekusi future yang dimulai dengan println tersebut. Setelah timer future selesai (dua detik kemudian), eksekusi melanjutkan kalimat "Wahyu's Computer: done!".