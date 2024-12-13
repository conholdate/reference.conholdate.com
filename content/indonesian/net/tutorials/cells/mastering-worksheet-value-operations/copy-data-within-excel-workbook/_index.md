---
title: Menyalin Data Dalam Buku Kerja Excel menggunakan Aspose.Cells untuk .NET
linktitle: Menyalin Data Dalam Buku Kerja Excel menggunakan Aspose.Cells untuk .NET
second_title: API Pemrosesan Excel Aspose.Cells .NET
description: Pelajari cara menyalin data secara efisien dalam buku kerja Excel menggunakan Aspose.Cells untuk .NET. Ikuti panduan langkah demi langkah ini untuk menduplikasi lembar kerja, mentransfer data, dan mengelola file Excel dengan mudah.
type: docs
weight: 12
url: /id/net/tutorials/cells/mastering-worksheet-value-operations/copy-data-within-excel-workbook/
---
## Perkenalan

Dalam panduan terperinci ini, kami akan menunjukkan cara menyalin data dalam buku kerja yang sama menggunakan Aspose.Cells untuk .NET. Dengan mengikuti petunjuk langkah demi langkah yang diuraikan di bawah ini, Anda akan mempelajari cara menduplikasi lembar kerja secara terprogram, mempertahankan konten dan formatnya.

## Prasyarat untuk Menyalin Data di Excel dengan Aspose.Cells

Sebelum menyelami proses pengkodean, mari pastikan Anda telah menyiapkan semuanya:

1. Pustaka Aspose.Cells untuk .NET: Anda perlu menginstal pustaka Aspose.Cells untuk .NET. Anda dapat mengunduh versi terbaru dari[Halaman unduhan Aspose.Cells untuk .NET](https://releases.aspose.com/cells/net/).
2. Lingkungan Pengembangan: IDE yang kompatibel dengan .NET seperti Visual Studio diperlukan untuk menulis dan menjalankan kode Anda.
3.  Lisensi Aspose: Anda dapat menggunakan uji coba gratis atau lisensi yang dibeli. Untuk informasi lebih lanjut, kunjungi[Di Sini](https://purchase.aspose.com/temporary-license/).

Setelah prasyarat ditetapkan, Anda siap untuk mulai bekerja dengan perpustakaan.

## Mengimpor Paket yang Diperlukan

Untuk memulai, Anda perlu mengimpor namespace yang relevan dari Aspose.Cells. Ini memungkinkan Anda untuk bekerja dengan file Excel menggunakan kelas dan metode yang disediakan oleh Aspose.Cells.

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

 Ruang nama ini akan memberi Anda akses ke`Workbook` kelas (untuk bekerja dengan file Excel) dan`WorksheetCollection` (untuk mengakses beberapa lembar dalam buku kerja).

## Langkah 1: Inisialisasi Jalur File untuk Buku Kerja

Agar kode Anda tetap teratur, penting untuk menentukan jalur berkas tempat buku kerja Anda berada dan tempat Anda ingin menyimpan berkas yang dimodifikasi. Berikut cara menentukan jalur:

```csharp
// Tentukan jalur direktori tempat file Excel berada.
string dataDir = "Your Directory Path";

// Tentukan jalur lengkap ke buku kerja masukan.
string inputPath = dataDir + "book1.xls";
```

 Mengganti`"Your Directory Path"` dengan jalur sebenarnya ke direktori Anda yang berisi buku kerja. Ini membantu memastikan bahwa kode tersebut fleksibel dan Anda dapat mengelola jalur secara efektif.

## Langkah 2: Buka Buku Kerja untuk Mengakses Data

 Sekarang setelah jalur file telah ditetapkan, langkah berikutnya adalah memuat buku kerja Excel ke dalam`Workbook` objek. Ini memungkinkan Anda mengakses isinya untuk manipulasi.

```csharp
// Muat berkas Excel ke dalam objek Buku Kerja.
Workbook wb = new Workbook(inputPath);
```

 Dengan baris ini, Anda telah berhasil memuat`book1.xls` ke dalam`wb` objek, membuat datanya dapat diakses.

## Langkah 3: Akses Koleksi Lembar Kerja

 Setelah buku kerja dimuat, Anda dapat mengakses lembar yang ada di dalamnya. Aspose.Cells menyediakan`Worksheets`koleksi, yang memungkinkan Anda berinteraksi dengan setiap lembar kerja dalam buku kerja.

```csharp
// Ambil koleksi lembar kerja dari buku kerja.
WorksheetCollection sheets = wb.Worksheets;
```

 Itu`sheets` objek sekarang memberi Anda akses ke semua lembar kerja di dalamnya`book1.xls`, dan Anda dapat melakukan berbagai operasi pada komputer tersebut, termasuk menyalin data dari satu lembar ke lembar lainnya.

## Langkah 4: Salin Data dari Satu Lembar ke Lembar Lainnya

 Untuk menyalin data dari satu lembar kerja ke lembar kerja lain dalam buku kerja yang sama, Aspose.Cells menawarkan metode yang mudah digunakan yang disebut`AddCopy`Metode ini membuat duplikat lembar kerja yang ditentukan dan menambahkannya ke buku kerja.

```csharp
// Salin data dari "Sheet1" ke lembar baru dalam buku kerja.
sheets.AddCopy("Sheet1");
```

 Dalam contoh ini, kita menyalin data dari "Sheet1" ke lembar baru.`AddCopy` Metode ini akan menduplikasi seluruh lembar, mempertahankan semua isinya, termasuk rumus, pemformatan, dan nilai.

## Langkah 5: Simpan Buku Kerja yang Dimodifikasi

 Setelah menyalin data, Anda dapat menyimpan buku kerja yang dimodifikasi dengan nama atau lokasi baru. Ini dilakukan dengan memanggil perintah`Save`metode pada`Workbook` obyek.

```csharp
//Simpan buku kerja yang dimodifikasi dengan nama baru.
wb.Save(dataDir + "book1_copy.xls");
```

 Ini akan menyimpan buku kerja dengan lembar yang disalin sebagai`book1_copy.xls` di direktori yang ditentukan. Anda dapat mengubah nama file dan jalur sesuai kebutuhan Anda.

## Kesimpulan

Menyalin data dalam buku kerja Excel menggunakan Aspose.Cells untuk .NET merupakan tugas yang mudah, dan panduan ini menyediakan langkah-langkah yang diperlukan untuk melakukannya secara efisien. Baik Anda menduplikasi seluruh lembar atau rentang data tertentu, Aspose.Cells menawarkan API yang tangguh dan fleksibel yang membuat otomatisasi Excel menjadi sederhana dan efektif.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menyalin beberapa lembar sekaligus?

Aspose.Cells tidak mendukung penyalinan beberapa lembar dalam satu panggilan. Namun, Anda dapat mengulang lembar yang ingin Anda salin dan menyalinnya satu per satu.

### Bagaimana cara mengganti nama lembar yang disalin?

Setelah menyalin lembar tersebut, Anda dapat mengganti namanya sebagai berikut:

```csharp
sheets[sheets.Count - 1].Name = "NewSheetName";
```

### Apakah Aspose.Cells kompatibel dengan .NET Core?

Ya, Aspose.Cells sepenuhnya kompatibel dengan lingkungan .NET Framework dan .NET Core.

### Bagaimana Aspose.Cells menangani pemformatan selama penyalinan?

 Itu`AddCopy`metode mempertahankan semua konten dan format saat menyalin lembar, memastikan bahwa data yang disalin tampak identik dengan aslinya.

### Bisakah saya menyalin lembar ke buku kerja lain?

 Ya, Anda dapat menyalin lembar ke buku kerja lain dengan menggunakan`Copy` metode dengan referensi ke buku kerja target.

```csharp
sheets.Add().Copy(wb.Worksheets["Sheet1"]);
```