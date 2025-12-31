# REST Assured API Automation Framework

![Java](https://img.shields.io/badge/Java-21-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Maven](https://img.shields.io/badge/Apache%20Maven-3.9.6-C71A36?style=for-the-badge&logo=apachemaven&logoColor=white)
![RestAssured](https://img.shields.io/badge/Rest%20Assured-5.3.0-02569B?style=for-the-badge&logo=google-chrome&logoColor=white)
![TestNG](https://img.shields.io/badge/TestNG-7.8.0-FF7F00?style=for-the-badge&logo=testng&logoColor=white)
![Build Status](https://img.shields.io/badge/Build-Passing-brightgreen?style=for-the-badge)

## 📖 Deskripsi Proyek
Repository ini berisi kerangka kerja otomatisasi pengujian API (*API Automation Testing Framework*) yang komprehensif, dibangun menggunakan **Java** dan **REST Assured**.

Proyek ini dirancang untuk memvalidasi fungsionalitas, keamanan, dan performa dari layanan RESTful API. Implementasi ini mencakup praktik terbaik (*best practices*) dalam Software Quality Assurance (SQA) modern, termasuk penggunaan *Design Pattern*, pemisahan konfigurasi, dan pembuatan data uji dinamis.

Target pengujian dilakukan pada layanan *mock API*:
* **JSONPlaceholder** (Simulasi operasi CRUD dasar)
* **ReqRes.in** (Simulasi autentikasi dan manajemen user)

## ✅ Cakupan Pengujian (Test Coverage)
Framework ini menangani berbagai skenario pengujian dari dasar hingga lanjutan:

### 1. Functional Testing (CRUD Operations)
Memastikan operasi basis data berjalan dengan benar melalui metode HTTP:
* **GET:** Verifikasi pengambilan data (Single User & List Users).
* **POST:** Verifikasi pembuatan data baru dengan payload JSON yang valid.
* **PUT/PATCH:** Verifikasi pembaruan data (Full & Partial Update).
* **DELETE:** Verifikasi penghapusan data dan status code yang sesuai (204 No Content).

### 2. Authentication & Security
* **Login & Register:** Simulasi alur autentikasi user berhasil dan gagal.
* **Token Validation:** Memastikan akses ke endpoint terproteksi memerlukan token yang valid.

### 3. Negative Testing (Error Handling)
Memastikan API menangani input yang salah dengan anggun:
* **Invalid Data:** Mengirim body request kosong atau format salah (expect 400 Bad Request).
* **Invalid Resource:** Mengakses ID atau endpoint yang tidak tersedia (expect 404 Not Found).

### 4. Data Driven Testing (Dynamic Data)
* Integrasi dengan library **Java Faker** untuk menghasilkan data uji yang unik (Random Name, Email, Address) setiap kali tes dijalankan.
* Mencegah kegagalan tes akibat duplikasi data (Unique Constraint Violation).

### 5. Performance & Schema Validation
* **Response Time Assertion:** Memastikan API merespon dalam batas waktu yang dapat diterima (Threshold < 2000ms).
* **JSON Schema Validator:** Memvalidasi struktur respon, tipe data, dan format JSON agar sesuai dengan kontrak API.

## 🛠️ Teknologi yang Digunakan (Tech Stack)

| Komponen | Teknologi | Versi | Deskripsi |
| :--- | :--- | :--- | :--- |
| **Language** | Java JDK | 21 (LTS) | Bahasa pemrograman utama |
| **Build Tool** | Apache Maven | 3.9+ | Manajemen dependensi & build |
| **Client Lib** | REST Assured | 5.3.0 | Library utama pengujian API |
| **Runner** | TestNG | 7.8.0 | Framework eksekusi test suite |
| **Matcher** | Hamcrest | 2.2 | Assertion library yang ekspresif |
| **Data Gen** | Java Faker | 1.0.2 | Generate data dummy otomatis |
| **JSON Utils** | Jackson | 2.15.2 | Serialisasi objek Java ke JSON |

## 📂 Struktur Project
Project ini mengikuti struktur standar Maven yang modular agar mudah dipelihara:

```text
src/test/java/com/praktikum/rest/
├── config/             # Konfigurasi Global (Base URL, Endpoints, Constants)
│   └── TestConfig.java
├── runners/            # Custom Test Runner (XML Suite Runner)
│   └── TestRunner.java
├── tests/              # Test Classes (Implementasi Skenario)
│   ├── BaseTest.java            # Setup & Teardown global (Before/After)
│   ├── UserAPITests.java        # Test Case CRUD User
│   ├── AuthenticationTests.java # Test Case Login/Register
│   ├── AdvancedAPITests.java    # Test Case Negative & Performance
│   └── FakerDataTests.java      # Test Case dengan Data Dinamis
└── utils/              # Utility & Helpers
    └── TestDataGenerator.java   # Helper class generator data Faker
```
