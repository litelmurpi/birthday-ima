# Aplikasi Quiz Bimbel Interaktif Berbasis Kotlin

![Kotlin](https://img.shields.io/badge/kotlin-%237F52FF.svg?style=for-the-badge&logo=kotlin&logoColor=white)
![Coroutines](https://img.shields.io/badge/Coroutines-Async-blue.svg?style=for-the-badge)
![License](https://img.shields.io/badge/license-MIT-green.svg?style=for-the-badge)

## 📚 Daftar Isi
- [Deskripsi](#-deskripsi)
- [Fitur](#-fitur)
- [Teknologi](#-teknologi)
- [Instalasi](#-instalasi)
- [Cara Penggunaan](#-cara-penggunaan)
- [Struktur Project](#-struktur-project)
- [Konsep Pemrograman](#-konsep-pemrograman)
- [Screenshot](#-screenshot)
- [Kontributor](#-kontributor)
- [Lisensi](#-lisensi)

## 📝 Deskripsi

Aplikasi Quiz Bimbel Interaktif adalah sebuah program pembelajaran berbasis console yang dirancang untuk membantu siswa dalam belajar melalui sistem quiz interaktif. Aplikasi ini dibangun menggunakan bahasa pemrograman Kotlin dengan menerapkan konsep-konsep pemrograman modern seperti OOP, Coroutines, dan Functional Programming.

### Tujuan Aplikasi:
- Menyediakan platform pembelajaran interaktif
- Membantu siswa berlatih soal dengan berbagai kategori
- Memberikan feedback instant dan tracking progress
- Meningkatkan motivasi belajar melalui gamifikasi

## ✨ Fitur

### 🎯 Fitur Utama
- **Multi-kategori Soal**: Matematika, Bahasa, dan Umum
- **Level Kesulitan**: Dasar, Menengah, dan Sulit
- **Sistem Penilaian Otomatis**: Skor dan nilai huruf
- **Time Tracking**: Mencatat waktu pengerjaan per soal
- **Statistik Detail**: Performa per kategori

### 🚀 Fitur Tambahan
- **Async Loading**: Memuat soal secara paralel dengan coroutines
- **Animasi Loading**: Visual feedback saat proses berjalan
- **Personalisasi**: Greeting dengan nama user
- **Leaderboard System**: Menyimpan hasil untuk kompetisi
- **Instant Feedback**: Respon langsung setelah menjawab
- **Progress Tracking**: Monitoring kemajuan belajar

## 🛠 Teknologi

### Bahasa Pemrograman
- **Kotlin** 1.9.0+

### Libraries & Dependencies
```gradle
dependencies {
    implementation("org.jetbrains.kotlinx:kotlinx-coroutines-core:1.7.3")
}
```

### Konsep yang Digunakan
- Object-Oriented Programming (OOP)
- Coroutines & Async Programming
- Functional Programming
- Design Patterns
- SOLID Principles

## 📦 Instalasi

### Prerequisites
- JDK 11 atau lebih tinggi
- Kotlin compiler
- Gradle (optional)

### Langkah Instalasi

1. **Clone Repository**
```bash
git clone https://github.com/username/quiz-bimbel-kotlin.git
cd quiz-bimbel-kotlin
```

2. **Setup Gradle (jika menggunakan Gradle)**
```bash
gradle init
gradle build
```

3. **Compile Manual (tanpa Gradle)**
```bash
kotlinc FP_quiz_tanpa_timer_realtime.kt -include-runtime -d quiz.jar
```

4. **Run Application**
```bash
java -jar quiz.jar
```

## 💻 Cara Penggunaan

### 1. Menjalankan Aplikasi
```bash
java -jar quiz.jar
```

### 2. Input Username
```
🎓 Selamat datang di Program Bimbel Sederhana!
==================================================
Masukkan nama pengguna (username) Anda: [ketik nama anda]
```

### 3. Menjawab Soal
- Baca soal dengan teliti
- Ketik jawaban Anda
- Tekan ENTER untuk submit
- Lihat feedback dan waktu menjawab

### 4. Melihat Hasil
- Skor akhir dan persentase
- Nilai huruf (A-E)
- Statistik per kategori
- Total waktu pengerjaan

## 📁 Struktur Project

```
quiz-bimbel-kotlin/
│
├── src/
│   └── main/
│       └── kotlin/
│           └── FP_quiz_tanpa_timer_realtime.kt
│
├── docs/
│   ├── flowchart.png
│   ├── class-diagram.png
│   └── laporan.pdf
│
├── test/
│   └── QuizTest.kt
│
├── build.gradle.kts
├── README.md
└── LICENSE
```

## 🏗 Konsep Pemrograman

### 1. Object-Oriented Programming (OOP)

#### Enkapsulasi
```kotlin
abstract class SoalTemplate(
    private val pertanyaan: String,
    private val jawabanBenar: String
) : ISoal {
    // Private properties dengan public getter
    open fun getPertanyaan(): String = pertanyaan
}
```

#### Inheritance
```kotlin
class SoalMatematika(...) : SoalTemplate(...) {
    // Child class mewarisi dari parent
}
```

#### Polimorfisme
```kotlin
override fun getPertanyaan(): String {
    return "Matematika ($levelKesulitan): ${super.getPertanyaan()}"
}
```

#### Abstraksi
```kotlin
interface ISoal {
    fun tampilkanInfo(): String
    fun getDifficulty(): Int
}
```

### 2. Coroutines & Async Programming

#### Async Loading
```kotlin
suspend fun loadSoalFromDatabase(): List<SoalTemplate> = coroutineScope {
    val soalList = listOf(
        async { Soal(...) },
        async { SoalMatematika(...) }
    )
    soalList.awaitAll()
}
```

#### Animation Effects
```kotlin
launch {
    print("Loading")
    repeat(3) {
        delay(500)
        print(".")
    }
}
```

### 3. Functional Programming

#### Lambda Expression
```kotlin
daftarSoal.filter { it.getKategori() == kategori }
```

#### Higher-Order Functions
```kotlin
fun prosesJawaban(
    soal: SoalTemplate,
    jawaban: String,
    onCorrect: () -> Unit,
    onWrong: (String) -> Unit
)
```

#### Scope Functions
```kotlin
// with
with(hasil) {
    println("Skor: $skor")
}

// let
daftarSoal.let { 
    println("Total: ${it.size}")
}

// apply
skorPerKategori.apply {
    forEach { (k, v) -> println("$k: $v") }
}
```

### 4. Collections

#### Set untuk unique values
```kotlin
private val kategoriSoal = mutableSetOf<String>()
```

#### Map untuk key-value pairs
```kotlin
private val skorPerKategori = mutableMapOf<String, Int>()
```

## 📸 Screenshot

### Welcome Screen
```
🎓 Selamat datang di Program Bimbel Sederhana!
==================================================
Masukkan nama pengguna (username) Anda: John Doe
```

### Loading Soal
```
📥 Mengambil soal dari database...
✅ Soal berhasil dimuat dalam 1523ms
```

### Quiz Session
```
Soal #1: Matematika (Dasar): Berapa hasil dari 5 + 7?
Jawaban Anda: 12
⏱️ Waktu menjawab: 3 detik
Memeriksa jawaban...
🎉 Benar sekali!
⚡ Luar biasa! Jawaban super cepat!
```

### Final Result
```
--- Kuis Selesai! ---

Selamat, John Doe!
Skor akhir Anda: 8 dari 10 soal.
Persentase Jawaban Benar: 80.00%
Nilai Huruf Anda: B
Total waktu pengerjaan: 2 menit 15 detik
```

## 👥 Kontributor

### Developer
- **Litel Murpi** - [@litelmurpi](https://github.com/litelmurpi)
  - Project Leader
  - System Architecture
  - Core Implementation
  - Testing & Documentation

## 📄 Lisensi

Distributed under the MIT License. See `LICENSE` for more information.

```
MIT License

Copyright (c) 2025 Litel Murpi

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## 🔗 Links

- [Kotlin Documentation](https://kotlinlang.org/docs/home.html)
- [Coroutines Guide](https://kotlinlang.org/docs/coroutines-guide.html)
- [Project Repository](https://github.com/litelmurpi/quiz-bimbel-kotlin)

---

**Made with ❤️ by Litel Murpi**

*Last Updated: July 11, 2025*
