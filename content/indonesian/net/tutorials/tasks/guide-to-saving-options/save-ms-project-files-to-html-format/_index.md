---
title: Simpan File MS Project ke Format HTML dengan Aspose.Tasks untuk .NET
linktitle: Simpan File MS Project ke Format HTML
second_title: Aspose.Tasks .NET API
description: Pelajari cara mengonversi file Microsoft Project (.mpp) ke format HTML dengan mudah menggunakan Aspose.Tasks untuk .NET. Tutorial komprehensif ini menyediakan petunjuk langkah demi langkah, termasuk cara memuat file proyek, menyesuaikan keluaran HTML, dan menyimpan halaman tertentu.
type: docs
weight: 10
url: /id/net/tutorials/tasks/guide-to-saving-options/save-ms-project-files-to-html-format/
---
## Perkenalan

Selamat datang di tutorial lengkap kami tentang mengonversi file Microsoft Project ke format HTML menggunakan Aspose.Tasks untuk .NET. Pustaka canggih ini menawarkan kepada pengembang kemampuan untuk memanipulasi file Microsoft Project secara terprogram dengan mudah. Dalam tutorial ini, kami akan memandu Anda melalui proses tersebut langkah demi langkah.

## Prasyarat

Sebelum kita memulai, pastikan Anda telah memenuhi prasyarat berikut:

1. Pengetahuan Dasar C#: Diasumsikan memiliki pengetahuan tentang bahasa pemrograman C#.
2. Instalasi Aspose.Tasks: Pastikan Anda telah menginstal Aspose.Tasks for .NET di lingkungan pengembangan Anda. Anda dapat dengan mudah mendapatkannya dari[Situs web Aspose](https://www.aspose.com).
3.  File Microsoft Project: Siapkan file Microsoft Project untuk konversi (dengan`.mpp` perpanjangan).

## Mengimpor Ruang Nama yang Diperlukan

Untuk memulai, kita perlu mengimpor namespace yang diperlukan yang akan memberi kita akses ke semua fungsi Aspose.Tasks.

```csharp
using Aspose.Tasks;
using Aspose.Tasks.Saving;
using Aspose.Tasks.Visualization;
```

## Langkah 1: Muat File Microsoft Project

 Muat berkas Microsoft Project Anda menggunakan potongan kode berikut. Ganti`"YourProjectFile.mpp"` dengan jalur ke berkas proyek Anda sebenarnya.

```csharp
var project = new Project("YourProjectFile.mpp");
```

## Langkah 2: Tentukan Opsi Penyimpanan HTML

Berikutnya, tentukan opsi penyimpanan HTML. Ini memungkinkan Anda untuk menyesuaikan tampilan data proyek saat dikonversi ke HTML.

```csharp
var options = new HtmlSaveOptions();
```

## Langkah 3: Simpan Data Proyek sebagai HTML

 Sekarang saatnya untuk menyimpan data proyek Anda dalam format HTML. Tentukan jalur output sebagai ganti`"OutputFilePath.html"`.

```csharp
project.Save("OutputFilePath.html", options);
```

## Fungsionalitas Tambahan: Menyimpan Halaman Tertentu

Jika Anda tertarik untuk menyimpan halaman tertentu dari proyek Anda, Anda dapat melakukannya dengan menentukan halaman mana yang akan disertakan. Berikut ini cara menentukan nomor halaman tertentu:

```csharp
options.Pages.Add(pageNumber); // Ganti dengan nomor halaman yang diinginkan
project.Save("OutputFilePath.html", options);
```

## Kesimpulan

Selamat! Anda kini telah mempelajari cara mengonversi file Microsoft Project ke format HTML menggunakan Aspose.Tasks for .NET. Proses sederhana ini memungkinkan Anda membuat data proyek Anda dapat diakses di berbagai platform.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menyesuaikan tampilan keluaran HTML?
 Ya! Anda dapat mengubah aspek-aspek seperti gaya font, warna, dan tata letak dengan menyesuaikan`HtmlSaveOptions` pengaturan yang sesuai dengan kebutuhan Anda.

### Apakah Aspose.Tasks mendukung format file lain untuk konversi?
Tentu saja! Aspose.Tasks mendukung konversi ke berbagai format, termasuk PDF, XLSX, dan PNG, dan masih banyak lagi.

### Apakah Aspose.Tasks kompatibel dengan berbagai versi file Microsoft Project?
Ya, pustaka ini dirancang agar kompatibel dengan berbagai versi file Microsoft Project, memastikan proyek Anda dapat diproses tanpa masalah.

### Bisakah saya mengekstrak data proyek tertentu untuk konversi HTML?
Tentu saja! Anda dapat memilih dan menyertakan halaman atau bagian tertentu dari proyek Anda berdasarkan kebutuhan Anda untuk keluaran HTML.

### Apakah ada versi uji coba yang tersedia untuk Aspose.Tasks?
Ya, Aspose menawarkan versi uji coba gratis Aspose.Tasks sehingga Anda dapat menjelajahi fitur-fiturnya sebelum memutuskan pembelian.