---
title: Dapatkan Semua Lampiran dari File PDF
linktitle: Dapatkan Semua Lampiran dari File PDF
second_title: Referensi API Aspose.PDF untuk .NET
description: Temukan cara mudah mengekstrak lampiran tertanam dari file PDF menggunakan Aspose.PDF untuk .NET dalam panduan langkah demi langkah ini.
type: docs
weight: 40
url: /id/net/tutorials/pdf/mastering-pdf-attachments/get-all-the-attachments-from-pdf-files/
---
## Perkenalan

Di dunia digital kita, file PDF sangat penting untuk berbagi dokumen—file tersebut serbaguna, aman, dan dapat berisi berbagai jenis informasi, termasuk lampiran yang disematkan. Pernahkah Anda perlu mengekstrak informasi tersembunyi tersebut dari PDF? Anda berada di tempat yang tepat! Dalam tutorial ini, kita akan membahas cara menggunakan Aspose.PDF untuk .NET guna mengekstrak semua lampiran dari file PDF. Baik Anda seorang pengembang berpengalaman atau baru memulai, panduan ini akan memandu Anda melalui proses tersebut langkah demi langkah.

## Prasyarat

Sebelum kita masuk ke kode, pastikan Anda memiliki hal berikut:

1. Visual Studio: Pastikan Anda telah menginstalnya di komputer Anda.
2.  Aspose.PDF untuk .NET: Unduh dan instal pustaka dari[Di Sini](https://releases.aspose.com/pdf/net/).
3. Pengetahuan Dasar C#: Keakraban dengan pemrograman C# akan membantu Anda memahami potongan kode dengan lebih mudah.

## Menyiapkan Lingkungan Anda

Untuk memulai, ikuti langkah-langkah berikut untuk menyiapkan proyek C# Anda:

### Buat Proyek Baru

Buka Visual Studio, dan buat proyek Aplikasi Konsol baru.

### Tambahkan Referensi Aspose.PDF

- Klik kanan pada proyek Anda di Solution Explorer.
- Pilih “Kelola Paket NuGet.”
- Cari “Aspose.PDF” dan instal versi terbaru.

## Impor Namespace yang Diperlukan

Di bagian atas file program Anda, impor namespace yang diperlukan:

```csharp
using System.IO;
using Aspose.Pdf;
using System;
```

Sekarang semuanya sudah disiapkan, mari kita tangani ekstraksi lampiran dari PDF.

## Langkah 1: Tentukan Direktori Dokumen Anda

Tentukan direktori tempat file PDF Anda disimpan. Ini memberi tahu program di mana PDF Anda akan disimpan.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Pastikan untuk mengganti`YOUR DOCUMENT DIRECTORY` dengan jalur sebenarnya.

## Langkah 2: Buka Dokumen PDF

Gunakan pustaka Aspose.PDF untuk membuka dokumen PDF Anda:

```csharp
Document pdfDocument = new Document(dataDir + "GetAlltheAttachments.pdf");
```

Pastikan jalur dan nama berkas sudah benar.

## Langkah 3: Akses Koleksi File Tertanam

Untuk mengakses lampiran dalam PDF, ambil koleksi file yang tertanam:

```csharp
EmbeddedFileCollection embeddedFiles = pdfDocument.EmbeddedFiles;
```

## Langkah 4: Hitung File yang Tertanam

Berguna untuk mengetahui berapa banyak lampiran yang ada:

```csharp
Console.WriteLine("Total files : {0}", embeddedFiles.Count);
```

## Langkah 5: Ulangi Melalui Lampiran

Ekstrak detail setiap lampiran menggunakan loop:

```csharp
int count = 1;

foreach (FileSpecification fileSpecification in embeddedFiles)
{
    Console.WriteLine("Name: {0}", fileSpecification.Name);
    Console.WriteLine("Description: {0}", fileSpecification.Description);
    Console.WriteLine("Mime Type: {0}", fileSpecification.MIMEType);
```

## Langkah 6: Ekstrak Parameter File Tambahan

Untuk lampiran dengan parameter tambahan, Anda dapat memeriksa dan mencetak rincian berikut:

```csharp
if (fileSpecification.Params != null)
{
    Console.WriteLine("CheckSum: {0}", fileSpecification.Params.CheckSum);
    Console.WriteLine("Creation Date: {0}", fileSpecification.Params.CreationDate);
    Console.WriteLine("Modification Date: {0}", fileSpecification.Params.ModDate);
    Console.WriteLine("Size: {0}", fileSpecification.Params.Size);
}
```

## Langkah 7: Ekstrak dan Simpan Lampiran

Terakhir, mari simpan setiap lampiran yang diekstrak ke sebuah file:

```csharp
byte[] fileContent = new byte[fileSpecification.Contents.Length];
fileSpecification.Contents.Read(fileContent, 0, fileContent.Length);

using (FileStream fileStream = new FileStream(dataDir + count + "_out" + ".txt", FileMode.Create))
{
    fileStream.Write(fileContent, 0, fileContent.Length);
}
count += 1;
```

Kode ini membaca konten setiap lampiran ke dalam array byte dan menyimpannya ke file teks baru, menamainya secara berurutan (misalnya,`1_out.txt`, `2_out.txt`, dll.).

## Kesimpulan

Selamat! Anda baru saja mengekstrak semua lampiran dari file PDF menggunakan Aspose.PDF untuk .NET. Pustaka canggih ini menyederhanakan manipulasi dokumen PDF dan memudahkan akses ke file yang disematkan—keterampilan yang sangat berharga untuk proyek pribadi dan usaha profesional.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.PDF untuk .NET?
Aspose.PDF untuk .NET adalah pustaka yang dirancang bagi pengembang untuk membuat, memanipulasi, dan mengonversi dokumen PDF secara terprogram.

### Apakah ada uji coba gratis Aspose.PDF?
 Ya, Aspose menyediakan versi uji coba gratis yang dapat Anda gunakan untuk menjelajahi fitur-fiturnya. Akses versi uji coba gratis[Di Sini](https://releases.aspose.com/).

### Bagaimana saya bisa mendapatkan dukungan untuk Aspose.PDF?
 Dukungan tersedia melalui forum Aspose, yang dapat Anda temukan[Di Sini](https://forum.aspose.com/c/pdf/10).

### Bisakah saya memperoleh lisensi sementara?
 Ya, Anda dapat meminta lisensi sementara untuk Aspose.PDF[Di Sini](https://purchase.aspose.com/temporary-license/).

### Di mana saya dapat menemukan dokumentasi untuk Aspose.PDF?
 Anda dapat menemukan dokumentasi lengkap untuk Aspose.PDF untuk .NET[Di Sini](https://reference.aspose.com/pdf/net/).