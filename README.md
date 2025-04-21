# Custom Gradle Task

Proyek Gradle sederhana yang menampilkan tugas kustom untuk menerima parameter command-line dan menampilkan pesan ucapan.

## Struktur Proyek

```
gradle-custom-task/
├── .gradle/
├── .gitignore
├── gradle/
├── lib/
│   ├── build.gradle
│   └── src/
│       ├── main/java/
│       └── test/java/
├── gradlew
├── gradlew.bat
├── settings.gradle
└── README.md
```

## Fitur

- Tugas Gradle kustom yang menerima parameter command-line
- Integrasi dengan library eksternal (Google Guava, JUnit, Apache Commons Math)
- Kompatibel dengan configuration cache Gradle

## Persyaratan

- Java JDK 21 atau lebih baru
- Gradle 8.13 atau lebih baru (sudah termasuk via Gradle Wrapper)

## Instalasi

1. Clone repositori ini:
   ```bash
   git clone https://github.com/azka-art/gradle-custom-task.git
   cd gradle-custom-task
   ```

## Penggunaan

### Menjalankan Tugas Greeting

Proyek ini menyertakan tugas kustom bernama `greetingTask` yang menerima parameter nama dan menampilkan pesan ucapan.

**Dengan nama kustom:**

```bash
# Untuk Linux/Mac
./gradlew greetingTask -Pnama=NamaAnda

# Untuk Windows (PowerShell)
.\gradlew greetingTask -Pnama=NamaAnda
```

**Dengan nama default:**

```bash
# Untuk Linux/Mac
./gradlew greetingTask

# Untuk Windows (PowerShell)
.\gradlew greetingTask
```

### Tugas yang Tersedia

Untuk melihat semua tugas kustom dalam proyek ini:

```bash
# Untuk Linux/Mac
./gradlew tasks --group custom

# Untuk Windows (PowerShell)
.\gradlew tasks --group custom
```

## Detail Implementasi

Tugas greeting kustom didefinisikan dalam `lib/build.gradle` dengan kode berikut:

```groovy
tasks.register('greetingTask') {
    description = 'Greets a user with a custom message'
    group = 'custom'
    
    // Definisikan properti selama fase konfigurasi
    def namaProperty = project.findProperty('nama') ?: 'Gradle User'
    
    doLast {
        // Gunakan properti selama fase eksekusi
        println "Hello, ${namaProperty}! Welcome to Gradle World!"
    }
}
```

## Dependensi

Proyek ini menggunakan dependensi berikut:

- Google Guava: `com.google.guava:guava:31.1-jre`
- JUnit: `junit:junit:4.13`
- Apache Commons Math: `org.apache.commons:commons-math3:3.6.1`

## Pengembangan

Untuk memodifikasi proyek ini:

1. Edit file `lib/build.gradle` untuk mengubah perilaku tugas atau dependensi
2. Jalankan tugas yang telah dimodifikasi menggunakan perintah yang ditunjukkan di bagian Penggunaan

## Lisensi

Proyek ini dilisensikan di bawah Lisensi MIT - lihat file LICENSE untuk detailnya.

## Kontribusi

1. Fork repositori
2. Buat branch fitur Anda (`git checkout -b feature/fitur-keren`)
3. Commit perubahan Anda (`git commit -m 'Menambahkan fitur keren'`)
4. Push ke branch (`git push origin feature/fitur-keren`)
5. Buka Pull Request