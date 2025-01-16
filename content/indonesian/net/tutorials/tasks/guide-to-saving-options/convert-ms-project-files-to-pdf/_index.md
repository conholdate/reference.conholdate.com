---
title: Konversi File MS Project ke PDF dengan Aspose.Tasks untuk .NET
linktitle: Opsi Penyimpanan PDF untuk Aspose.Tasks
second_title: Aspose.Tasks .NET API
description: Pelajari cara mengonversi file Microsoft Project (.mpp) ke PDF dengan Aspose.Tasks untuk .NET. Ikuti panduan langkah demi langkah ini untuk menyesuaikan keluaran PDF, memilih halaman tertentu, dan mengotomatiskan konversi batch.
type: docs
weight: 13
url: /id/net/tutorials/tasks/guide-to-saving-options/convert-ms-project-files-to-pdf/
---
## Perkenalan

Manajemen berkas proyek yang efisien memainkan peran penting dalam alur kerja yang efisien dan keberhasilan proyek. Dengan menggunakan Aspose.Tasks for .NET, pengembang dapat mengonversi berkas Microsoft Project ke dalam format PDF dengan presisi dan fleksibilitas. Dalam panduan ini, kami akan memandu Anda melalui proses langkah demi langkah untuk menyimpan berkas Microsoft Project (.mpp) sebagai PDF, lengkap dengan opsi yang dapat disesuaikan.

## Prasyarat untuk Menggunakan Aspose.Tasks untuk .NET

Sebelum melanjutkan, pastikan prasyarat berikut terpenuhi:

1. Aspose.Tasks untuk Instalasi .NET  
    Unduh dan instal perpustakaan dari[situs web](https://releases.aspose.com/tasks/net/).

2. Lingkungan Pengembangan  
   Pengetahuan tentang bahasa pemrograman C# dan lingkungan pengembangan .NET yang dikonfigurasi.

3. Masukkan File Proyek Microsoft  
    Memiliki validitas`.mpp`berkas tersedia untuk konversi.

## Impor Ruang Nama Penting

Sebelum melakukan pengkodean, sertakan namespace yang diperlukan untuk mengakses fungsionalitas Aspose.Tasks. 

```csharp
using Aspose.Tasks;
using Aspose.Tasks.Saving;
using Aspose.Tasks.Visualization;
using System.Collections.Generic;
```

## Langkah 1: Muat File Microsoft Project

 Untuk memulai, muat`.mpp` berkas ke dalam`Project` objek. Ganti`"Your_Project_File_Path.mpp"` dengan jalur ke berkas masukan Anda.

```csharp
var project = new Project("Your_Project_File_Path.mpp");
```

## Langkah 2: Konfigurasikan Opsi Penyimpanan PDF

Siapkan opsi untuk menyesuaikan keluaran PDF. Aspose.Tasks untuk .NET memberikan fleksibilitas untuk mengontrol tampilan halaman, tata letak, dan aspek lainnya.

```csharp
var options = new PdfSaveOptions
{
    RenderToSinglePage = false, // Apakah akan merender semua konten pada satu halaman
    Pages = new List<int>()     // Halaman yang akan disertakan dalam PDF
};
```

## Langkah 3: Tentukan Jumlah Halaman

 Gunakan`PageCount` properti untuk mengidentifikasi berapa banyak halaman yang dapat dicakup proyek. Ini membantu memutuskan apakah akan menyertakan halaman tertentu atau mengekspor semuanya.

```csharp
Console.WriteLine("Total Pages: " + options.PageCount);
```

## Langkah 4: Pilih Halaman Tertentu untuk Diekspor (Opsional)

 Tentukan halaman yang tepat untuk disertakan dalam PDF dengan mengisi`Pages` properti. Misalnya, untuk mengekspor halaman 1 dan 4:

```csharp
options.Pages.Add(1);
options.Pages.Add(4);
```

## Langkah 5: Simpan File Proyek sebagai PDF

 Terakhir, simpan`.mpp`file sebagai PDF dengan memanggil`Save` metode. Tentukan jalur file keluaran dan berikan opsi yang dikonfigurasi.

```csharp
project.Save("Output_PDF_File_Path.pdf", options);
```

## Kesimpulan

Mengonversi file Microsoft Project ke PDF menggunakan Aspose.Tasks untuk .NET memastikan pengalaman yang lancar dan dapat disesuaikan. Dari memilih halaman tertentu hingga mengotomatiskan ekspor batch, alat ini memberdayakan pengembang untuk menangani file proyek secara efektif.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menyesuaikan tampilan PDF yang diekspor?
Ya, Aspose.Tasks memungkinkan penyesuaian font, warna, dan tata letak halaman untuk memenuhi kebutuhan spesifik Anda.

###  Apakah mungkin untuk mengkonversi?`.mpp` files from older versions of Microsoft Project?
 Aspose.Tasks mendukung`.mpp` file dari Microsoft Project 2003 dan seterusnya.

### Bagaimana cara menyajikan semua data proyek pada satu halaman PDF?
 Mengatur`RenderToSinglePage` milik`PdfSaveOptions` keberatan terhadap`true`.

```csharp
options.RenderToSinglePage = true;
```

### Bisakah saya mengekspor data proyek ke format file lain?
Ya, Aspose.Tasks mendukung ekspor ke berbagai format termasuk Excel, HTML, dan format gambar seperti PNG dan JPEG.

### Apakah ada uji coba gratis yang tersedia untuk Aspose.Tasks untuk .NET?
 Ya, Anda dapat mengunduh[versi uji coba gratis di sini](https://releases.aspose.com/).