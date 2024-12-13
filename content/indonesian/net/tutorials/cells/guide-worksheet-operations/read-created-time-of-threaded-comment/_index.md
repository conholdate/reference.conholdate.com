---
title: Membaca Waktu Pembuatan Komentar Berulir dengan Aspose.Cells
linktitle: Membaca Waktu Pembuatan Komentar Berulir dengan Aspose.Cells
second_title: API Pemrosesan Excel Aspose.Cells .NET
description: Pelajari cara mudah membaca waktu pembuatan komentar berulir dalam lembar kerja Excel menggunakan Aspose.Cells for .NET. Ikuti panduan terperinci kami dengan petunjuk langkah demi langkah.
type: docs
weight: 21
url: /id/net/tutorials/cells/guide-worksheet-operations/read-created-time-of-threaded-comment/
---
## Perkenalan

Saat bekerja dengan file Excel, mengelola komentar dapat menjadi hal penting untuk kolaborasi dan pelacakan umpan balik. Dalam panduan ini, kami akan memandu Anda melalui proses membaca waktu pembuatan komentar berulir dalam lembar kerja Excel menggunakan Aspose.Cells for .NET. Alat canggih ini menyediakan cara yang efisien untuk berinteraksi dengan file Excel, yang memungkinkan pengembang untuk mengekstrak informasi terperinci dari komentar, yang khususnya berguna untuk melacak waktu umpan balik dalam skenario kolaboratif.

## Prasyarat

Sebelum memulai, penting untuk memastikan bahwa lingkungan pengembangan Anda telah diatur dengan benar untuk menggunakan Aspose.Cells for .NET. Berikut ini yang Anda perlukan:

1.  Aspose.Cells untuk .NET: Anda perlu menginstal pustaka Aspose.Cells. Anda bisa mendapatkan versi terbaru dari[Situs web Aspose](https://releases.aspose.com/cells/net/).
2. IDE: Visual Studio (atau IDE .NET pilihan Anda) untuk menulis dan mengeksekusi kode Anda.
3. Pengetahuan Dasar C#: Keakraban dengan pemrograman C# akan memudahkan untuk mengikuti contoh-contohnya.
4.  File Excel: Untuk tutorial ini, kita akan menggunakan file Excel bernama`ThreadedCommentsSample.xlsx`, yang menyertakan beberapa komentar berulir. Pastikan berkas Anda berisi komentar untuk diikuti.

## Mengimpor Paket yang Diperlukan

Untuk memulai, Anda perlu mengimpor namespace yang diperlukan untuk bekerja dengan Aspose.Cells. Buka proyek C# Anda dan tambahkan perintah berikut di bagian atas berkas kode Anda:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

 Itu`Aspose.Cells` namespace memungkinkan Anda mengakses semua kelas dan metode yang diperlukan untuk memanipulasi file Excel, sementara`System` diperlukan untuk fungsionalitas umum seperti keluaran dan penanganan pengecualian.

## Langkah 1: Tentukan Direktori File Excel

Langkah pertama adalah menentukan jalur tempat file Excel Anda disimpan. Jalur ini akan digunakan untuk menemukan file tersebut secara terprogram.

```csharp
// Tentukan direktori file Excel
string sourceDir = "Your Document Directory";
```

 Mengganti`"C:\\YourDirectory\\"`dengan jalur sebenarnya ke berkas Anda. Ini memastikan bahwa program mengetahui di mana menemukan berkas tersebut`ThreadedCommentsSample.xlsx`.

## Langkah 2: Muat Buku Kerja

 Dengan direktori yang sudah ditetapkan, kita sekarang dapat memuat buku kerja Excel. Ini dilakukan dengan membuat buku kerja baru`Workbook` objek dan meneruskan jalur berkas ke objek tersebut.

```csharp
// Memuat buku kerja Excel
Workbook workbook = new Workbook(sourceDir + "ThreadedCommentsSample.xlsx");
```

Jika berkas tidak ditemukan pada jalur yang ditentukan, pengecualian akan dikeluarkan, jadi pastikan jalur berkas sudah benar sebelum melanjutkan.

## Langkah 3: Akses Lembar Kerja yang Diinginkan

Setelah buku kerja dimuat, Anda perlu mengakses lembar kerja yang berisi komentar berulir. Dalam contoh ini, kita akan mengambil lembar kerja pertama dari buku kerja tersebut.

```csharp
// Akses lembar kerja pertama di buku kerja
Worksheet worksheet = workbook.Worksheets[0];
```

 Jika komentar Anda berada di lembar kerja yang berbeda, cukup ubah indeksnya. Misalnya, gunakan`Worksheets[1]` untuk lembar kerja kedua, dan seterusnya.

## Langkah 4: Ambil Komentar Berulir

Untuk mengambil komentar berulir, Anda harus menentukan sel yang berisi komentar. Dalam kasus ini, kita fokus pada sel`A1` .Metode`GetThreadedComments` digunakan untuk mendapatkan semua komentar yang terkait dengan sel tertentu.

```csharp
// Dapatkan komentar berulir dari sel A1
ThreadedCommentCollection threadedComments = worksheet.Comments.GetThreadedComments("A1");
```

Ini akan mengembalikan kumpulan komentar berulir untuk sel A1. Jika tidak ada komentar di sel yang ditentukan, kumpulan tersebut akan kosong.

## Langkah 5: Ulangi Komentar dan Ekstrak Waktu yang Dibuat

 Setelah komentar berulir diambil, langkah selanjutnya adalah mengulangi koleksi dan mengekstrak detail yang relevan, termasuk waktu pembuatan untuk setiap komentar. Kita dapat dengan mudah mencapainya dengan mengulang melalui`ThreadedCommentCollection`.

```csharp
// Ulangi setiap komentar berulir dan tampilkan detailnya
foreach (ThreadedComment comment in threadedComments)
{
    Console.WriteLine("Comment: " + comment.Notes);
    Console.WriteLine("Author: " + comment.Author.Name);
    Console.WriteLine("Created Time: " + comment.CreatedTime);
}
```

 Kode ini akan menampilkan konten komentar, nama penulis, dan waktu komentar dibuat.`CreatedTime` properti mengembalikan stempel waktu saat komentar awalnya dibuat.

## Langkah 6: Menampilkan Pesan Konfirmasi

Setelah berhasil membaca komentar berulir dan menampilkan informasinya, sebaiknya sertakan pesan konfirmasi dalam kode Anda. Ini membantu mengonfirmasi bahwa proses telah dijalankan dengan benar.

```csharp
// Pesan konfirmasi
Console.WriteLine("Successfully retrieved threaded comment created times.");
```

Pesan ini akan dicetak ke konsol setelah eksekusi kode selesai, mengonfirmasi bahwa proses berjalan tanpa kesalahan.

## Kesimpulan

Anda kini telah mempelajari cara mudah membaca waktu pembuatan komentar berulir dalam lembar kerja Excel menggunakan Aspose.Cells untuk .NET. Fungsionalitas ini sangat berharga untuk melacak komentar dan umpan balik dalam lingkungan kolaboratif, menyediakan stempel waktu penting untuk proses peninjauan dokumen. Dengan mengikuti panduan ini, Anda dapat mengekstrak dan memanfaatkan data komentar secara efisien dalam aplikasi .NET Anda, meningkatkan alur kerja Anda dan meningkatkan kolaborasi dengan anggota tim.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Cells untuk .NET?

Aspose.Cells untuk .NET adalah pustaka lengkap yang memungkinkan pengembang membuat, memanipulasi, dan mengelola berkas Excel dalam aplikasi .NET. Pustaka ini menyediakan alat yang tangguh untuk membaca, menulis, dan memodifikasi berkas Excel secara terprogram.

### Bagaimana cara mengunduh Aspose.Cells untuk .NET?

 Anda dapat mengunduh versi terbaru Aspose.Cells untuk .NET dari[Situs web Aspose](https://releases.aspose.com/cells/net/).

### Apakah ada uji coba gratis yang tersedia?

 Ya, Aspose menawarkan uji coba gratis untuk Aspose.Cells for .NET. Anda dapat mengunduh versi uji coba dari[halaman percobaan gratis](https://releases.aspose.com/).

### Bisakah saya mengakses komentar dari sel lain?

 Ya, Anda dapat mengakses komentar berulir dari sel mana pun di lembar kerja dengan mengubah referensi sel di`GetThreadedComments` metode. Cukup ubah`"A1"` ke referensi sel yang diinginkan.

### Di mana saya bisa mendapatkan dukungan untuk Aspose.Cells?

 Jika Anda memerlukan dukungan atau memiliki pertanyaan, kunjungi[Forum Aspose](https://forum.aspose.com/c/cells/9), tempat Anda dapat menemukan jawaban atau meminta bantuan dari komunitas.