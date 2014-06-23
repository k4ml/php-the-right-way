---
anchor: dependency_management
---

# Dependency Management {#dependency_management_title}

Ada segudang _library_, _framework_, dan komponen yang dapat dipilih di PHP. Proyek Anda mungkin akan menggunakan beberapa dari mereka - hal ini disebut sebagai dependensi / ketergantungan. Sampai saat ini, PHP tidak memiliki cara yang baik untuk mengelola dependensi proyek ini. Bahkan jika Anda berhasil melakukannya secara manual, Anda masih harus khawatir tentang autoloaders.

Namun kini tidak lagi. Saat ini ada dua sistem manajemen paket utama untuk PHP - Komposer dan PEAR. Mana yang tepat bagi Anda? Jawabannya adalah keduanya.

 * Gunakan **Composer** ketika mengelola dependensi untuk satu proyek saja.
 * Gunakan **PEAR** ketika mengelola dependensi untuk PHP secara keseluruhan pada sistem Anda.

Secara umum, paket Composer akan tersedia hanya dalam proyek-proyek yang secara eksplisit Anda tentukan sedangkan paket PEAR akan tersedia bagi semua proyek PHP Anda. Sementara PEAR mungkin terdengar seperti lebih mudah pendekatan pada pandangan pertama, ada keuntungan untuk menggunakan pendekatan dependensi proyek-by-proyek.
