---
title: Menambahkan Java Script ke File PDF
linktitle: Tambahkan File PDF Java Script
second_title: Referensi API Aspose.PDF untuk .NET
description: Dokumen ini menyediakan panduan lengkap untuk menambahkan elemen interaktif seperti peringatan pop-up atau fungsi cetak otomatis ke dokumen PDF menggunakan Aspose.PDF for .NET.
type: docs
weight: 10
url: /id/net/tutorials/pdf/master-pdf-document-programming/adding-java-script-to-pdf/
---
## Perkenalan
Dokumen ini menyediakan panduan lengkap untuk menambahkan elemen interaktif seperti peringatan pop-up atau fungsi cetak otomatis ke dokumen PDF menggunakan Aspose.PDF for .NET. Dengan memanfaatkan kemampuan pustaka ini, Anda dapat membuat PDF yang dinamis dan menarik yang memenuhi berbagai kebutuhan pengguna.

## Prasyarat
 Sebelum melanjutkan, pastikan Anda telah mengunduh versi terbaru Aspose.PDF untuk .NET dari[Rilis Aspose](https://rilis.aspose.com/pdf/net/) atau memperoleh uji coba gratis melalui situs web mereka:[releases.aspose.com](http://releases.aspose.com).

Anda juga harus memiliki pemahaman dasar tentang C# dan terbiasa dengan lingkungan pengembangan yang Anda gunakan. Selain itu, jika Anda perlu menghindari batasan selama proses pengembangan, pertimbangkan untuk memperoleh lisensi sementara dari Aspose.

## Mengimpor Paket yang Diperlukan
Untuk mulai menulis kode, impor namespace yang diperlukan dari pustaka Aspose.PDF:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Annotations;
using Aspose.Pdf.Text;
```

## Langkah 1: Memuat PDF yang Ada
Muat dokumen PDF yang sudah ada yang ingin Anda tambahkan elemen interaktif:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "input.pdf");
```

 Mengganti`"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya ke berkas PDF Anda.

## Langkah 2: Menambahkan JavaScript di Tingkat Dokumen

 Untuk menerapkan skrip yang dipicu saat dokumen dibuka, buat instance`JavascriptAction` obyek:

```csharp
JavascriptAction javaScript = new JavascriptAction("this.print({bUI:true,bSilent:false,bShrinkToFit:true});");
doc.OpenAction = javaScript;
```

## Langkah 3: Menambahkan JavaScript di Tingkat Halaman

 Untuk memicu tindakan tertentu berdasarkan pembukaan atau penutupan halaman, buat contoh`JavascriptAction` objek untuk setiap halaman:

```csharp
doc.Pages[2].Actions.OnOpen = new JavascriptAction("app.alert('Page 2 opened')");
doc.Pages[2].Actions.OnClose = new JavascriptAction("app.alert('Page 2 closed')");
```

## Langkah 4: Menyimpan Dokumen PDF

Untuk menyimpan dokumen PDF yang dimodifikasi, tentukan jalur file keluaran:

```csharp
string dataDir = dataDir + "JavaScript-Added_out.pdf";
doc.Save(dataDir);
Console.WriteLine("\nJavaScript added successfully to the PDF.\nFile saved at " + dataDir);
```

## Kesimpulan
Dengan mengikuti panduan ini dan memanfaatkan Aspose.PDF untuk .NET, Anda dapat menyempurnakan PDF Anda secara efektif dengan elemen interaktif. Pustaka ini menawarkan solusi komprehensif untuk membuat dokumen yang dinamis dan menarik yang memenuhi berbagai kebutuhan pengguna.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menambahkan beberapa tindakan JavaScript ke halaman berbeda dalam PDF?
Ya, Anda dapat menetapkan tindakan JavaScript yang berbeda untuk halaman individual atau keseluruhan dokumen.

### Apakah mungkin untuk menghapus JavaScript dari PDF setelah menambahkannya?
 Ya, Anda dapat menghapus atau mengubah tindakan JavaScript yang ada dengan menghapus`Actions` properti dokumen atau halaman.

### Fungsi JavaScript apa saja yang dapat saya gunakan dalam PDF?
Anda dapat menggunakan JavaScript apa pun yang didukung oleh mesin JavaScript Adobe Acrobat, seperti pencetakan, peringatan, dan manipulasi formulir.

### Apakah JavaScript berfungsi di semua penampil PDF?
Sebagian besar tindakan JavaScript akan berfungsi di penampil PDF yang mendukung PDF interaktif, seperti Adobe Acrobat. Namun, beberapa pembaca PDF dasar mungkin tidak mendukung JavaScript.