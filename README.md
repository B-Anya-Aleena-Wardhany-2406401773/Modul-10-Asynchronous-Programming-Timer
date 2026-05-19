# Reflection

Anya Aleena Wardhany

2406401773

## Experiment 1.2: Understanding How It Works

![Experiment 1.2](images/01.png)

Setelah menambahkan `println!("Anya's Komputer: hey hey!")` tepat setelah `spawner.spawn(...)`,
outputnya adalah:

```
Anya's Komputer: hey hey!
Anya's Komputer: howdy!
Anya's Komputer: done!
```

"hey hey!" muncul sebelum "howdy!" meskipun kode `spawn` ditulis lebih dulu. Ini terjadi karena `spawner.spawn()` hanya mendaftarkan future ke dalam queue, bukan langsung menjalankannya. Future baru benar-benar dieksekusi saat `executor.run()` dipanggil. Jadi baris `println!` yang ada di luar async block akan langsung dieksekusi oleh main thread, sedangkan isi async block (howdy! dan done!) baru dijalankan oleh executor setelahnya.