---
title: Melindungi Baris dalam Lembar Kerja menggunakan Aspose.Cells
linktitle: Melindungi Baris dalam Lembar Kerja menggunakan Aspose.Cells
second_title: API Pemrosesan Excel Aspose.Cells .NET
description: Pelajari cara mengamankan informasi sensitif di lembar kerja Excel Anda dengan melindungi baris tertentu menggunakan Aspose.Cells untuk .NET. Tutorial komprehensif ini mencakup semuanya mulai dari menyiapkan lingkungan Anda.
type: docs
weight: 18
url: /id/net/tutorials/cells/mastering-worksheet-security/protecting-rows/
---
## Perkenalan

Bekerja dengan file Excel secara terprogram sering kali memerlukan tidak hanya manipulasi data tetapi juga perlindungan data. Melindungi baris tertentu dalam lembar kerja dapat menjadi hal yang penting untuk menjaga informasi sensitif atau mencegah penyuntingan yang tidak disengaja. Dalam tutorial ini, kita akan membahas cara melindungi baris dalam lembar kerja Excel menggunakan Aspose.Cells for .NET. Kami akan memandu Anda melalui langkah-langkah yang diperlukan, mulai dari menyiapkan lingkungan hingga menerapkan fitur perlindungan baris dengan cara yang mudah.

## Prasyarat
Sebelum memulai, pastikan Anda telah menyiapkan hal-hal berikut:

1.  Aspose.Cells untuk .NET: Unduh dan instal dari[Halaman unduhan Aspose Cells](https://releases.aspose.com/cells/net/).
2. Visual Studio atau IDE .NET apa pun: Anda memerlukan lingkungan pengembangan. Visual Studio direkomendasikan, tetapi IDE apa pun yang kompatibel dengan .NET sudah cukup.
3. Pengetahuan Dasar C#: Keakraban dengan pemrograman C# akan membantu Anda mengikuti dan memodifikasi kode contoh sesuai kebutuhan.
4.  Dokumentasi API Aspose.Cells: Tinjau[Dokumentasi Aspose.Cells untuk .NET](https://reference.aspose.com/cells/net/) untuk ikhtisar struktur dan metode kelas.

Setelah prasyaratnya siap, kita dapat melanjutkan ke implementasi.

## Impor Paket yang Diperlukan
Mulailah dengan mengimpor paket yang diperlukan dalam proyek C# Anda. Pustaka ini penting untuk berinteraksi dengan file Excel.

```csharp
using System.IO;
using Aspose.Cells;
```

## Langkah 1: Buat Buku Kerja dan Lembar Kerja Baru
Sebelum menerapkan pengaturan proteksi apa pun, buat buku kerja baru dan pilih lembar kerja yang ingin Anda kerjakan.

```csharp
// Tentukan jalur ke direktori dokumen.
string dataDir = "Your Document Directory";
// Buat direktori jika belum ada.
if (!Directory.Exists(dataDir))
    Directory.CreateDirectory(dataDir);

// Buat buku kerja baru dan pilih lembar kerja pertama.
Workbook wb = new Workbook();
Worksheet sheet = wb.Worksheets[0];
```

## Langkah 2: Tentukan Objek Style dan StyleFlag
Tentukan objek gaya dan bendera gaya, yang akan memungkinkan Anda mengubah properti sel, seperti mengunci atau membukanya.

```csharp
// Tentukan objek gaya dan bendera gaya.
Style style;
StyleFlag flag;
```

## Langkah 3: Buka Kunci Semua Kolom di Lembar Kerja
Secara default, semua sel dalam lembar kerja Excel terkunci. Untuk melindungi hanya baris tertentu, buka kunci semua kolom terlebih dahulu.

```csharp
// Ulangi semua kolom dan buka kuncinya.
for (int i = 0; i <= 255; i++)
{
    style = sheet.Cells.Columns[i].Style;
    style.IsLocked = false;
    flag = new StyleFlag { Locked = true };
    sheet.Cells.Columns[i].ApplyStyle(style, flag);
}
```

## Langkah 4: Kunci Baris Tertentu
Sekarang, kunci baris yang ingin Anda lindungi. Dalam contoh ini, kita akan mengunci baris pertama.

```csharp
// Kunci baris pertama.
style = sheet.Cells.Rows[0].Style;
style.IsLocked = true;
flag = new StyleFlag { Locked = true };
sheet.Cells.ApplyRowStyle(0, style, flag);
```

Anda dapat mengulangi langkah ini untuk baris tambahan yang ingin Anda kunci.

## Langkah 5: Lindungi Lembaran
Setelah baris yang diperlukan terkunci, saatnya untuk melindungi lembar kerja. Ini akan mencegah modifikasi pada baris yang terkunci kecuali perlindungan dihapus.

```csharp
// Lindungi lembaran itu.
sheet.Protect(ProtectionType.All);
```

## Langkah 6: Simpan Buku Kerja
Terakhir, simpan buku kerja dengan perubahan yang diterapkan. Anda dapat memilih dari berbagai format, seperti Excel 97-2003 atau versi yang lebih baru.

```csharp
// Simpan berkas Excel.
wb.Save(dataDir + "output.out.xls", SaveFormat.Excel97To2003);
```

## Kesimpulan
Selamat! Anda telah berhasil mempelajari cara melindungi baris dalam lembar kerja Excel menggunakan Aspose.Cells for .NET. Dengan mengikuti langkah-langkah ini, Anda dapat membuka atau mengunci baris atau kolom sesuai kebutuhan dan menerapkan perlindungan untuk menjaga integritas data Anda.

## Pertanyaan yang Sering Diajukan
### Bagaimana saya bisa melindungi beberapa baris sekaligus?
Anda dapat melakukan pengulangan melalui beberapa indeks baris dan menerapkan gaya penguncian pada masing-masing indeks secara individual.

### Bisakah saya mengatur kata sandi untuk perlindungan lembar?
 Ya, Anda dapat memberikan kata sandi ke`sheet.Protect()` metode untuk menegakkan perlindungan kata sandi.

### Bisakah saya membuka kunci sel tertentu, bukan seluruh kolom?
Ya, Anda dapat membuka kunci sel individual dengan memodifikasi properti gayanya alih-alih membuka kunci seluruh kolom.

### Apa yang terjadi jika saya mencoba mengedit baris yang dilindungi?
Bila suatu baris diproteksi, Excel akan mencegah segala bentuk penyuntingan pada sel yang terkunci kecuali lembar tersebut tidak diproteksi.

### Bisakah saya melindungi rentang tertentu dalam satu baris?
 Ya! Anda dapat mengunci rentang individual dalam satu baris dengan mengatur`IsLocked` properti untuk sel tertentu dalam rentang tersebut.