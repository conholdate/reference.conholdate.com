---
title: Daftar Bernomor Bergaya Menggunakan Aspose.PDF untuk .NET
linktitle: Daftar Bernomor Bergaya Menggunakan Aspose.PDF untuk .NET
second_title: Referensi API Aspose.PDF untuk .NET
description: Temukan cara membuat daftar bernomor cantik dalam dokumen PDF Anda dengan Aspose.PDF untuk .NET. Panduan ini memandu Anda melalui proses penerapan berbagai gaya penomoran—seperti angka Romawi.
type: docs
weight: 10
url: /id/net/programming-with-headings/stylish-numbered-lists/
---
## Perkenalan

Pernahkah Anda perlu membuat daftar bernomor yang terstruktur dengan baik dalam dokumen PDF Anda? Baik untuk dokumen hukum, laporan, atau presentasi, gaya penomoran yang efektif sangat penting untuk mengatur konten Anda. Dengan Aspose.PDF untuk .NET, Anda dapat dengan mudah menerapkan berbagai gaya penomoran ke judul PDF Anda, sehingga menghasilkan dokumen yang rapi dan profesional.

## Prasyarat

Sebelum kita masuk ke pengkodean, pastikan Anda telah menyiapkan hal berikut:

1.  Aspose.PDF untuk .NET: Unduh versi terbaru dari[Di Sini](https://releases.aspose.com/pdf/net/).
2. Lingkungan Pengembangan: Anda memerlukan Visual Studio atau IDE apa pun yang kompatibel dengan .NET.
3. .NET Framework: Pastikan Anda telah menginstal .NET Framework 4.0 atau yang lebih tinggi.
4.  Lisensi: Anda dapat menggunakan lisensi sementara dari[Di Sini](https://purchase.aspose.com/temporary-license/) atau jelajahi[uji coba gratis](https://releases.aspose.com/) pilihan.

## Mengimpor Paket yang Diperlukan

Mulailah dengan mengimpor namespace yang diperlukan dalam proyek Anda:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## Langkah 1: Menyiapkan Dokumen

Mari kita mulai dengan membuat dokumen PDF baru dan mengonfigurasi tata letaknya, termasuk ukuran halaman dan margin.

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document pdfDoc = new Document();

// Atur dimensi dan margin halaman
pdfDoc.PageInfo.Width = 612.0; // 8,5 inci
pdfDoc.PageInfo.Height = 792.0; // 11 inci
pdfDoc.PageInfo.Margin = new Aspose.Pdf.MarginInfo(72, 72, 72, 72); // margin 1 inci
```

Pengaturan ini memberi dokumen Anda ukuran surat standar dengan margin satu inci di semua sisi.

## Langkah 2: Menambahkan Halaman ke PDF

Berikutnya, kita akan menambahkan halaman kosong ke dokumen PDF, tempat kita nantinya akan menerapkan gaya penomoran.

```csharp
// Tambahkan halaman baru ke dokumen PDF
Aspose.Pdf.Page pdfPage = pdfDoc.Pages.Add();
pdfPage.PageInfo = pdfDoc.PageInfo; // Gunakan pengaturan yang sama seperti dokumen
```

## Langkah 3: Membuat Kotak Mengambang

FloatingBox memungkinkan Anda memposisikan konten secara independen dari alur halaman, memberi Anda kontrol lebih besar atas tata letak Anda.

```csharp
//Buat FloatingBox untuk konten terstruktur
Aspose.Pdf.FloatingBox floatBox = new Aspose.Pdf.FloatingBox
{
    Margin = pdfPage.PageInfo.Margin
};
pdfPage.Paragraphs.Add(floatBox);
```

## Langkah 4: Menambahkan Judul dengan Angka Romawi

Sekarang, mari kita tambahkan judul pertama kita dengan penomoran angka Romawi kecil.

```csharp
// Buat judul pertama dengan angka Romawi
Aspose.Pdf.Heading heading1 = new Aspose.Pdf.Heading(1)
{
    IsInList = true,
    StartNumber = 1,
    Text = "List 1",
    Style = NumberingStyle.NumeralsRomanLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading1);
```

## Langkah 5: Menambahkan Judul Kedua dengan Nomor Awal Kustom

Berikutnya, kita akan menambahkan judul kedua, dimulai dari angka Romawi 13.

```csharp
// Buat judul kedua dimulai dengan angka Romawi 13
Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1)
{
    IsInList = true,
    StartNumber = 13,
    Text = "List 2",
    Style = NumberingStyle.NumeralsRomanLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading2);
```

## Langkah 6: Menambahkan Judul dengan Penomoran Alfabet

Untuk variasi, mari tambahkan judul ketiga menggunakan penomoran alfabet dalam huruf kecil.

```csharp
// Buat judul dengan penomoran alfabet
Aspose.Pdf.Heading heading3 = new Aspose.Pdf.Heading(2)
{
    IsInList = true,
    StartNumber = 1,
    Text = "The value, as of the effective date of the plan, of property to be distributed under the plan on account of each allowed",
    Style = NumberingStyle.LettersLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading3);
```

## Langkah 7: Menyimpan PDF

Terakhir, mari simpan berkas PDF ke direktori yang Anda inginkan.

```csharp
// Simpan dokumen PDF
dataDir = dataDir + "ApplyNumberStyle_out.pdf";
pdfDoc.Save(dataDir);
Console.WriteLine($"\nNumber style applied successfully in headings.\nFile saved at {dataDir}");
```

## Kesimpulan

Selamat! Anda telah berhasil menerapkan berbagai gaya penomoran—angka Romawi dan alfabet—pada judul dalam file PDF menggunakan Aspose.PDF untuk .NET. Fleksibilitas Aspose.PDF memungkinkan Anda untuk mengontrol tata letak halaman, gaya penomoran, dan posisi konten, sehingga Anda dapat membuat dokumen PDF yang terorganisasi dengan baik dan profesional.

## Pertanyaan yang Sering Diajukan

### Dapatkah saya menerapkan gaya angka yang berbeda pada dokumen PDF yang sama?  
Ya, Anda dapat mencampur gaya penomoran yang berbeda, seperti angka Romawi, angka Arab, dan penomoran alfabet dalam dokumen yang sama.

### Bagaimana saya dapat menyesuaikan nomor awal untuk judul?  
 Anda dapat mengatur nomor awal untuk judul apa pun menggunakan`StartNumber` milik.

### Apakah ada cara untuk mengatur ulang urutan penomoran?  
 Ya, Anda dapat mengatur ulang penomoran dengan menyesuaikan`StartNumber` properti untuk setiap judul.

### Dapatkah saya menerapkan gaya tebal atau miring pada judul selain penomoran?  
 Tentu saja! Anda dapat menyesuaikan gaya judul dengan memodifikasi properti seperti font, ukuran, tebal, dan miring menggunakan`TextState` obyek.

### Bagaimana cara mendapatkan lisensi sementara untuk Aspose.PDF?  
 Anda dapat memperoleh lisensi sementara dari[Di Sini](https://purchase.aspose.com/temporary-license/)untuk menguji Aspose.PDF tanpa batasan.